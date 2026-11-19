This pseudocode (EXTREMELY PSEUDO, Probably incorrect) constructs some sort of AST about a document. 
It holds no information on tasks, org roam blocks etc. only structure.

```
struct Document {
	frontmatter: yaml
	children: (Heading | Checklist | Text)[]
}

struct Heading {
	level: int
	content: string
	properties: map[string]value
	children: (Heading | Checklist | Text)[]
}

// a list of `- [ ] ...` lines
struct Checklist {
	items: {done: bool, content: str}[]
}

// basic markdown content that we don't care about parsing.
struct TextLine {
	content: string
}

parse_doc(s: str) -> Document:
	fenced := false // anything fenced must be ignored, even if it resembles a heading or whatever
	last_was_heading := false

	document := Document{}

	for line in s:
		if line starts with "```": 
			last_was_heading = false
			fenced = not fenced
			append line to latest found Text

		else if line starts with "#" and not fenced:
			last_was_heading = true

			level := amount of "#"
			content := string after last "#"
			heading := Heading{level, content}

			append heading at correct level

		else if line starts with ">" and last_was_heading and not fenced
			last_was_heading = false
			append parse_properties(line) to latest found heading

		else if line starts with "- [ ]" or with "- [x]":
			last_was_heading = false
			append parse_checklist_item(line) to latest found Checklist

		else:
			last_was_heading = false
			append line to latest found Text

	return document
```

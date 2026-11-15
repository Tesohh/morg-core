# tasks
- Tasks always satisfy pattern `/$- [.]/` or `/$#+ [.]/`
- The task parser should find all lines that start with the pattern 
- Tasks span across the entire line
- By default `[ ]` are todo, `[x]` are done <!-- [E] for events? -->
    - Users are able to add custom statuses in their config, eg. a `[-]` for "in progress"
- modifiers add data to the task

## example tasks (list style)
```md
- [ ] go to the doctor <!-- a "Bare task" with no extra data, only status and title -->
- [ ] go to the doctor @at(2026-22-11 12:00) <!-- goes to calendar at specific time -->
- [ ] go to the doctor @at(2026-22-11 12:00) @repeat(+60d x6) <!-- repeat every 2 months, 6 times -->
- [ ] go to the doctor @at(2026-22-11 12:00) @repeat(+60d -> 2028-01-01) <!-- repeat every 2 months, until 2028 -->
```

## big example tasks (org style)
Use the org style syntax to add a description of the task, or just to get a nicer hierarchy and hide the modifiers (folding)

```md
<!-- modifiers can be placed on the line after... -->
# [ ] go to the doctor
@at(2026-22-11 12:00) @repeat(+60d -> 2028-01-01)
You should go to the doctor man you're ill

<!-- or inline -->
# [ ] go to the doctor @at(2026-22-11 12:00) @repeat(+60d -> 2028-01-01)
You should go to the doctor man you're ill
```

## the `@at` modifier
- This modifier lets you set the time for a task
- Uses ISO dates, `T` between date and time is optional so it looks cleaner
```md
- [ ] go to the doctor @at(2026-22-11 12:00)
- [ ] go to the doctor @at(2026-22-11T12:00)
```

## the `@repeat` modifier
TODO

## the `@id` modifier
```md
<!-- all valid, as long as the id's are unique! -->
- [ ] go to the doctor @id(doctor)
- [ ] go to the doctor @id(go-to-doctor)
- [ ] go to the doctor @id(6abfae)
- [ ] go to the doctor @id(1)
```

- This modifier assigns a unique, stable id to a task.
- Editor plugins can automatically add one for you.
- If a task does not have one, the id is derived from the filename + task title (slug'ized)
    - Example in `analysis/integral/something.md`, these are equal:
    ```md
    - [ ] study this thing
    - [ ] study this thing @id(analysis-integral-something:study-this-thing)
    ```
- Use explicit `@id`s if you may move the tasks between files, 
  or you want to be absolutely sure that if you write the same title twice in the same file, nothing happens

## `+` tags
Used for categorizing tasks.
```md
- [ ] go to the doctor +health +personal
```

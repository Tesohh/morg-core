# tasks
<!-- - Tasks always satisfy pattern `/$- [.]/` or `/$#+ [.]/` -->
<!-- - The task parser should find all lines that start with the pattern  -->
<!-- - Tasks span across the entire line -->
<!-- - By default `[ ]` are todo, `[x]` are done <!-- [E] for events? --> -->
<!--     - Users are able to add custom statuses in their config, eg. a `[-]` for "in progress" -->
<!-- - modifiers add data to the task -->
<!-- ## the `@repeat` modifier -->
<!-- - Automatically repeat tasks, starting from the `@at` time -->
<!--     - Does nothing if no `@at` modifier is present. -->
<!-- - Use `+` -->
<!-- - Units can be: `h`, `d`, `w`, `m`, `y` -->
<!-- ```markdown -->
<!-- <!-- go at 12:00 every week, 3 times starting from 22/11/2026 --> -->
<!-- <!-- 22/11/2026, 29/11/2026, 6/12/2026 --> -->
<!-- - [ ] go to the doctor @at(2026-11-22 12:00) @repeat(+7d 3x) -->
<!-- ``` -->


## Example
This example is a self describing showcase of the syntax

```markdown
# TODO do this and that +tag +tag2
> scheduled: <2026-11-22 Sun 12:00> deadline: <2026-11-22 13:00>
> id: 123456 effort: 1h30m key: value longerkey: "longer value"

> This quote block is not part of the properties block as it is not directly below the heading

- The properties quote block contains key value pairs
    - It renders cleanly on most markdown renderers (eg. github), even if they don't have the custom format.
    - Can be split on different lines for readability
- Timestamps can optionally contain the weekday after the date
- The nvim plugin will let you conveniently edit timestamps, eg. arrow keys to adjust by hour, shift+arrows for days etc.

This is a checklist. The neovim plugin will track completion as virtual text after the task title.
- [x] Do this
- [ ] Do that

## DOING do something else
This is another task, i'm working on this

## DONE finished task
> closed: (2026-11-22 12:25) 

## WHAT +tag is this +task
> note: i dont know

The WHAT keyword doesn't exist, so it is not handled as a task
Also that note property is invalid, it would have been valid if it was: `> note: "i dont know"`

By the way, the `+tag` is not read, as tags can only be at the end of the heading (meaning `+task` is read)
```

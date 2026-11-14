# notes system sloppy

- Bring Your Own Sync: recommend syncthing, but you can use anything
- Bring Your Own Calendar: the server generates a ical or ics file that can be added to your favorite calendar client, which also gives you reminder notifications
- Bring Your Own Editor: use any regular text editor for editing your notes, organize however you like
- Reminders using a custom format
- When a note file changes on server disk, parse reminders

## Reminder/event syntax
```md
THIS IS A TASK
- [ ] do this and that @task(2026-11-22T15:22) @repeat(+7d -> 2026-12-11)

THIS IS AN EVENT
- event title @event(2026-11-22T15:00 -> 2026-11-22T17:00) @repeat(+7d)
```

the calendar file is pretty much a "projection" of all `@task` and `@event`s, including the repeats, the completion status etc.

## what we won't do
- Multi user
- authentication
- web editor/viewer (will be a separate repo/crate/whatever)

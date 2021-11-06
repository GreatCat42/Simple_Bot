## `ev_type` Format

The argument, `ev_type`, is a string that shows what 'kind' of event an Event instance is. It also shows the details of a command.

Used in the analysis part of this project, usually as a key in a `dict`.

```
COMMAND: com a b c d;
a-first digit
b-second digit
c-third digit
d-fourth digit

STATUS: sta a b c d;
a-forward accel
b-forward velocity 
c-angular accel
d-angular velocity

RESULT: res a b;
a-move/turn
move
	b-forward/backward
turn
	b-left/right

```


# Stack

- n take
- pop
- dup
- swap
- rot
- stackHeight

# Namespace

one global namespace

- null
- int (1 = true, 0 = false)
- float (double)
- str
- array (fixed length)
- block

name call:
- execute if block
- push to stack if variable

commands:
- exists
- type
- del
- (str) get (makes pointer-like behaviour possible)

# Sequence

- `()`: push frozen anonymous block to stack
- `exec`: execute block

## Ifelse

```
(x 2 % 0 ==) ('yes' print) ('no' print) ifelse
```

```
"ifelse" (2 take exec take swap pop exec) :seq
```

- cond t f
- t f cond (2 take)
- t f 1 (exe)
- f t (take)
- t f (swap)
- t (pop)

## If

```
(x 2 % 0 ==) ('yes' print) if
```

```
"if" (() ifelse) def
```

## While

- break: close last frame and go to next frame incrementing pointer by one.
- redo: reset pointer inside current frame to 0.
- exec: open sequence as a frame inside frame stack.
- take: take the element of the stack chosen by the element on top.

```
"i" 0 :int
(i 10 <) (i ++ i print) while
```

```
"while" (copy2 (break) ifelse redo) :seq 
```

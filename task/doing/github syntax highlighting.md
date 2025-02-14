Github syntax highlighting
==========================

I've been using `yaml` on markdown fenced code blocks because it's vaguely similar to silver, and looks good enough in Codium.
However on Github a lot of the indentation is being highlighted, presumably as a bug.
Need to investigate, might have to take it off.


Examples
--------

### Simple

```yaml
type: discovery/discussion/braindump etc
status: open/closed
opened: yyyy-mm-dd
closed: yyyy-mm-dd
```

Indented with spaces:
```yaml
  type: discovery/discussion/braindump etc
  status: open/closed
  opened: yyyy-mm-dd
  closed: yyyy-mm-dd
```

Tab indenting:
```yaml
	type: discovery/discussion/braindump etc
	status: open/closed
	opened: yyyy-mm-dd
	closed: yyyy-mm-dd
```

### Simple structures

With space indent:
```yaml
blockName: BlockType
  item1: Type1 value1
  item2: Type2 value2
```
```yaml
blockName: BlockType
  item1: Type1 value1
  item2: Type2 value2
end
```

With tab indents:
```yaml
blockName: BlockType
	item1: Type1 value1
	item2: Type2 value2
```
```yaml
blockName: BlockType
	item1: Type1 value1
	item2: Type2 value2
end
```

### Simple structures - indented

Spaces:
```yaml
  blockName: BlockType
    item1: Type1 value1
    item2: Type2 value2
```
```yaml
  blockName: BlockType
    item1: Type1 value1
    item2: Type2 value2
  end
```

Tabs:
```yaml
	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
```
```yaml
	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
	end
```


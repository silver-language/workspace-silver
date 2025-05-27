Github syntax highlighting
==========================

I've been using `yaml` on markdown fenced code blocks because it's vaguely similar to silver, and looks good enough in Codium.
However on Github a lot of the indentation is being highlighted, presumably as a bug.
Need to investigate, might have to take it off.


https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks


### In VSCode/Codium
https://stackoverflow.com/questions/70400790/where-can-i-find-the-list-of-supported-languages-for-markdown-preview-code-fence
https://github.com/highlightjs/highlight.js/blob/main/SUPPORTED_LANGUAGES.md


Fenced code examples using 'yaml'
---------------------------------

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

**Results**

Looks like the yaml syntax highlighter mainly has issues with tabs.
So i've either got to find another highlighter that's okay with tabs, or just take them all off.
I should probably be more consistent with base-indentation too.

https://en.wikipedia.org/wiki/Off-side_rule#Notable_programming_languages

Someones to try: Boo, Cobra, F#, Elm, gdscript, sass


Experiments with other syntax highlighters
------------------------------------------

https://github.com/github-linguist/linguist/blob/main/lib/linguist/languages.yml

none
```
	name: Type `value`

	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
	end
```

java
```java
	name: Type `value`

	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
	end
```

python
```python
	name: Type `value`

	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
	end
```

fsharp
```fs
	name: Type `value`

	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
	end
```

boo
```boo
	name: Type `value`

	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
	end
```

elm
```elm
	name: Type `value`

	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
	end
```

godot
```godot
	name: Type `value`

	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
	end
```

js
```js
	name: Type `value`

	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
	end
```

bash
```bash
name: Type `value`

blockName: BlockType
	item1: Type1 value1
	item2: Type2 value2
end

	name: Type `value`

	blockName: BlockType
		item1: Type1 value1
		item2: Type2 value2
	end
```

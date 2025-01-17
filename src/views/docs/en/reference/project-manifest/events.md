---
title: '@events'
category: app.arc
---

 Define SNS topics with Lambda handler functions.

## Syntax

- Name
  - Lowercase alphanumeric string
  - Maximum of 50 characters
  - Dashes are allowed; underscores are not allowed
  - Must begin with a letter

Events can use more verbose configuration to allow for [custom source paths](../../guides/developer-experience/custom-source-paths) in your project. Provide a  `src` for each event.

## Example

These configuration examples show how to define events:

<arc-viewer default-tab=arc>
<div slot=contents>

<arc-tab label=arc>
<h5>arc</h5>
<div slot=content>

```arc
@app
myapp

@events
hit-counter
likes
# verbose custom source:
custom-webhook
  src custom/source

```
</div>
</arc-tab>

<arc-tab label=json>
<h5>json</h5>
<div slot=content>

```json
{
  "app": "myapp",
  "events": [
    "hit-counter",
    "likes",
    {
      "custom-webhook": {
        "src": "custom/source"
      }
    }
  ]
}
```
</div>
</arc-tab>

<arc-tab label=yaml>
<h5>yaml</h5>
<div slot=content>

```yaml
---
app: "myapp"
events:
- hit-counter
- likes
# verbose custom source:
- "custom-webhook":
    src: "custom/source"
```
</div>
</arc-tab>

<arc-tab label=toml>
<h5>toml</h5>
<div slot=content>

```toml
app="myapp"
events=[
  "hit-counter",
  "likes"
]

# TOML doesn't allow mixed types in an array.
# Theoretically a "table" entry with a custom source would look like:

[[events]]
[events."custom-webhook"]
src = "custom/source"
```
</div>
</arc-tab>

</div>
</arc-viewer>

Which generates the following scaffolding:

```bash
/
├── custom
│   └── source/
├── src
│   └── events
│     ├── hit-counter/
│     └── likes/
├── app.arc
└── package.json
```

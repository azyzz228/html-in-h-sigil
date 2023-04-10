# html-in-h-sigil

Write fast HTML inside of `.ex` files with these snippets when writing Phoenix Application with Elixir.

## Features

This extension with code snippets aims to accelerate html production inside of `~H` sigil in Phoenix Framework. You can think of it as very lightweight *emmet* that allows you to produce html inside of quote marks in elixir files.

Simply type in `;<tag of your choice>` and there will be VSCODE auto suggestion with the snippet.

For example if there is an image subfolder under your extension project workspace:

![](https://github.com/azyzz228/html-in-h-sigil/blob/main/assets/sample.gif)

 But first, there are couple of things to make it work. (See section below)

## Installation

These code snippets must be enabled to be active inside of string. 

1. Go to Settings > Search "Quick Suggestions" > turn on suggestions for *strings*.

Or, change the `settings.json` file:

```json
"editor.quickSuggestions": {
        "strings": true // this is your relevant option
    }
```

2. Put a space after `~H` so that `""" """` is interpreted as string. After that, auto suggestions will be available for you to quickly write HTML. Compiler will complain because no space is needed for sigils to work. However, for the sake of writing quick HTML, ignore complains when writing HTML.

3. After you are done with HTML, delete the space after `~H`, and voila! No compiler errors, fast and beautiful HTML. 


```
# Change from this
def render() do
    ~H"""
    """
end

# to this
def render() do
    ~H """
    """
end

# so that

def render() do
    ~H """
    ;div + Tab produces the following: <div class=""></div>
    """
end

# after you are done, delete the space.
def render() do
    ~H"""
    <div class=""></div>
    """
end
```



## Available snippets

### Simple HTML tags

| snippet | generated code |
|---|---|
|;div|`<div class=""></div>`|
|;p|`<p class=""></p>`|
|;ul|`<ul class=""></ul>`|
|;li|`<li class=""></li>`|
|;h1|`<h1 class=""></h1>`|
|;h2|`<h2 class=""></h2>`|
|;h3|`<h3 class=""></h3>`|
|;h4|`<h4 class=""></h4>`|
|;h5|`<h5 class=""></h5>`|
|;h6|`<h6 class=""></h6>`|
|;span|`<span class=""></span>`|
|;form|`<form class=""></form>`|
|;button|`<button class=""></button>`|

### Phoenix specific snippets

| snippet | generated code |
|---|---|
|;pe|`<%=  %>`|
|;plink|`<.link navigate={~p"/"}></.link>`|

All simple HTML tags also have option to be foor loop'ed item, except for `form` and `button` tags. Simply add `fl` after the tag.

For example:

| snippet | generated code |
|---|---|
|;divfl|`<div :for={item <- list_of_items} class=""></div>`|
|;p|`<p :for={item <- list_of_items} class=""></p>`|
|;li|`<li :for={item <- list_of_items} class=""></li>`|

## Known Issues

A lot of HTML tags are not included in this snippet. HTML tags and other Phoenix Framework related snippets will be populated if demanded by community. Also, there is a lot of room for Phoenix specific snippets.

## Release Notes

Initial release.

### 1.0.0

Initial release of this snippet-extension with the following HTML tags: `div`, `p`, `ul`, `li`, `h1`, `h2`, `h3`, `h4`, `h5`, `h6`, `span`, `form`, `button`. All HTML tags except for `form` and `button` can be Phoenix for loop'ed when you add `fl` after the tag. Two other Phoenix specific snippets include: Code Render block (`<%= %>`), and `link` core component `<.link navigate={~p"/"}></.link>`

---

**Enjoy!**

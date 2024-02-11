<img src="https://github.com/echasnovski/media/blob/main/mini.nvim/logo/logo_operators.png" style="width: 100%">

<!-- badges: start -->
[![GitHub license](https://badgen.net/github/license/echasnovski/mini.nvim)](https://github.com/echasnovski/mini.nvim/blob/main/LICENSE)
<!-- badges: end -->

### Text edit operators

See more details in [Features](#features) and [help file](doc/mini-operators.txt).

---

⦿ This is a part of [mini.nvim](https://github.com/echasnovski/mini.nvim) library. Please use [this link](https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-operators.md) if you want to mention this module.

⦿ All contributions (issues, pull requests, discussions, etc.) are done inside of 'mini.nvim'.

⦿ See the repository page to learn about common design principles and configuration recipes.

---

If you want to help this project grow but don't know where to start, check out [contributing guides of 'mini.nvim'](https://github.com/echasnovski/mini.nvim/blob/main/CONTRIBUTING.md) or leave a Github star for 'mini.nvim' project and/or any its standalone Git repositories.

## Demo

https://github.com/echasnovski/mini.nvim/assets/24854248/8a3656c4-c92a-4d9f-9711-8d6a751b3e5a

## Features

Features:
- Operators:
    - Evaluate text and replace with output.
    - Exchange text regions.
    - Multiply (duplicate) text.
    - Replace text with register.
    - Sort text.

- Automated configurable mappings to operate on textobject, line, selection. Can be disabled in favor of more control with `MiniOperators.make_mappings()`.

- All operators support `[count]` and dot-repeat.

See `*MiniOperators-overview*` and `*MiniOperators.config*` tags in help for more details.

## Installation

This plugin can be installed as part of 'mini.nvim' library (**recommended**) or as a standalone Git repository.

There are two branches to install from:

- `main` (default, **recommended**) will have latest development version of plugin. All changes since last stable release should be perceived as being in beta testing phase (meaning they already passed alpha-testing and are moderately settled).
- `stable` will be updated only upon releases with code tested during public beta-testing phase in `main` branch.

Here are code snippets for some common installation methods (use only one):

<details>
<summary>With <a href="https://github.com/echasnovski/mini.nvim/blob/main/readmes/mini-deps.md">mini.deps</a></summary>
<table>
    <thead>
        <tr>
            <th>Github repo</th>
            <th>Branch</th> <th>Code snippet</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>'mini.nvim' library</td> <td>Main</td> <td rowspan=2><i>Follow recommended 'mini.deps' installation</i></td>
        </tr>
        <tr>
            <td>Stable</td>
        </tr>
        <tr>
            <td rowspan=2>Standalone plugin</td> <td>Main</td> <td><code>add('echasnovski/mini.operators')</code></td>
        </tr>
        <tr>
            <td>Stable</td> <td><code>add({ source = 'echasnovski/mini.operators', checkout = 'stable' })</code></td>
        </tr>
    </tbody>
</table>
</details>

<details>
<summary>With <a href="https://github.com/folke/lazy.nvim">folke/lazy.nvim</a></summary>
<table>
    <thead>
        <tr>
            <th>Github repo</th>
            <th>Branch</th> <th>Code snippet</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>'mini.nvim' library</td>
            <td>Main</td> <td><code>{ 'echasnovski/mini.nvim', version = false },</code></td>
        </tr>
        <tr>
            <td>Stable</td> <td><code>{ 'echasnovski/mini.nvim', version = '*' },</code></td>
        </tr>
        <tr>
            <td rowspan=2>Standalone plugin</td>
            <td>Main</td> <td><code>{ 'echasnovski/mini.operators', version = false },</code></td>
        </tr>
        <tr>
            <td>Stable</td> <td><code>{ 'echasnovski/mini.operators', version = '*' },</code></td>
        </tr>
    </tbody>
</table>
</details>

<details>
<summary>With <a href="https://github.com/junegunn/vim-plug">junegunn/vim-plug</a></summary>
<table>
    <thead>
        <tr>
            <th>Github repo</th>
            <th>Branch</th> <th>Code snippet</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>'mini.nvim' library</td>
            <td>Main</td> <td><code>Plug 'echasnovski/mini.nvim'</code></td>
        </tr>
        <tr>
            <td>Stable</td> <td><code>Plug 'echasnovski/mini.nvim', { 'branch': 'stable' }</code></td>
        </tr>
        <tr>
            <td rowspan=2>Standalone plugin</td> <td>Main</td> <td><code>Plug 'echasnovski/mini.operators'</code></td>
        </tr>
        <tr>
            <td>Stable</td> <td><code>Plug 'echasnovski/mini.operators', { 'branch': 'stable' }</code></td>
        </tr>
    </tbody>
</table>
</details>

<br>

**Important**: don't forget to call `require('mini.operators').setup()` to enable its functionality.

**Note**: if you are on Windows, there might be problems with too long file paths (like `error: unable to create file <some file name>: Filename too long`). Try doing one of the following:
- Enable corresponding git global config value: `git config --system core.longpaths true`. Then try to reinstall.

## Default config

```lua
-- No need to copy this inside `setup()`. Will be used automatically.
{
  -- Each entry configures one operator.
  -- `prefix` defines keys mapped during `setup()`: in Normal mode
  -- to operate on textobject and line, in Visual - on selection.

  -- Evaluate text and replace with output
  evaluate = {
    prefix = 'g=',

    -- Function which does the evaluation
    func = nil,
  },

  -- Exchange text regions
  exchange = {
    prefix = 'gx',

    -- Whether to reindent new text to match previous indent
    reindent_linewise = true,
  },

  -- Multiply (duplicate) text
  multiply = {
    prefix = 'gm',

    -- Function which can modify text before multiplying
    func = nil,
  },

  -- Replace text with register
  replace = {
    prefix = 'gr',

    -- Whether to reindent new text to match previous indent
    reindent_linewise = true,
  },

  -- Sort text
  sort = {
    prefix = 'gs',

    -- Function which does the sort
    func = nil,
  }
}
```

## Similar plugins

- [gbprod/substitute.nvim](https://github.com/gbprod/substitute.nvim)
- [svermeulen/vim-subversive](https://github.com/svermeulen/vim-subversive)
- [tommcdo/vim-exchange](https://github.com/tommcdo/vim-exchange)
- [christoomey/vim-sort-motion](https://github.com/christoomey/vim-sort-motion)

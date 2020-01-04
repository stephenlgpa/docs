# Journal Setup

**Purpose**: Documents the settings of the Journalling setup I have with NVIM.

## Plugins

1. **Goyo** - A distraction-free writing experience  
[Goyo on GitHub - junegunn](https://github.com/junegunn/goyo.vim)

- :Goyo              Toggles on
- :Goyo [dimension]  Turns on, or resizes to dimension
- :Goyo!             Toggles off
- [dimension]
	- width:       `Goyo 120`
	- height:      `Goyo x30`
	- both:        `Goyo 120x30`
	- percentage:  `Goyo 120x50%`
	- with offset: `Goyo 50%+25%x50%-25%`

2. **seoul256** - Low-contrast Vim color scheme based on Seoul Colors  
[Seoul255 on GitHub - junegunn](https://github.com/junegunn/seoul256.vim)

- Set using `:colo seoul256`.
- Turn on light version using `:colo seoul256-light`
- Set background darkness with the following: (233 (darkest) - 239 (lightest))

```
:let g:seoul256_background=233
:colo seoul256
```

3. **Limelight** - Dims surrounding paragraphs  
[Limelight on GitHub - junegunn](https://github.com/junegunn/limelight.vim)

- `:LimelightN`    Turn Limelight on, set dimming level N (0=none, 1=invisible)
	- e.g. `:Limelight0.5`
- `:Limelight!`    Turn Limelight off
- `:Limelight!!`

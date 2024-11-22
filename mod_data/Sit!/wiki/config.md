# Configuration
The sit mod has 2 config files, the [server-config](#server-configjson) and the [sitting-config](#sitting-configjson).

## server-config.json

### keep-active
**Type:** Boolean

If the sit entites should stay in the world when the player leaves or server closes or not.

### sit-while-seated
**Type:** Boolean

If the player can sit on another Sit! entity if they are already on a Sit! entity. *(enables cheap elevators and movement devices, be careful on server)*

### preset-blocks
Enables certain preset sitting blocks, can be overwritten by custom blocks or blacklist.

#### stairs
**Type:** Boolean

#### slabs
**Type:** Boolean

#### carpets
**Type:** Boolean

#### full-blocks
**Type:** Boolean

### custom-enabled
**Type:** Boolean

Enables the custom-blocks json block, to allow for custom sit blocks

### custom-blocks
**Type:** [Sitting Block](#sitting-block) List


### blacklisted-blocks
**Type:** [Custom Block](#custom-block) List

The list of blocks that can't be sit on. This is useful for blocking certain blocks from a wide custom block selection.

Put a `!` in front of block entries that are not allowed in the custom block.




## Sitting Block
A custom block entry with an extra field for sitting height

### sitting-height
**Type:** Double
\
**Example:** `0.437`
\
**Range:** `0 - 1`

Sets the sitting height for the custom block

### [Custom Block](#custom-block)
The rest are the same as Custom Block fields



## Custom Block
Specifies a custom block, can be used to select multiple blocks at once.

### block-ids
**Type:** String List
\
**Example:** `"!minecraft:warped_stem", "minecraft:polished_basalt"`

The list of blocks that are apart (or not apart) of the custom block.

Put a `!` in front of block entries that are not allowed in the custom block.

### block-tags
**Type:** String List
\
**Example:** `"#minecraft:logs", "!#minecraft:oak_logs"`

The list of block tags that are (or aren't) apart of the custom block.

Make sure each entry has a `#` in front of it.
\
Put a `!` in front of tag entries that are not allowed in the custom block.

### blockstates
**Type:** String List
\
**Example:** `"!axis=y"`

The list of blockstates that are (or aren't) apart of the custom block.

Make sure each entry is entered as they show up when looking at a block in f3 (compare using `=`).
\
Put a `!` in front of blockstates that are not allowed in the custom block.




## sitting-config.json
⚠️ When a player joins a `Sit!` server with the `Sit!` mod installed, they will use their own settings for this file.

### enabled
**Type:** Boolean

Toggles sitting ablity. If off on the server, and a player joins with it enabled, they would be able to sit.

### hand-sitting
**Type:** Boolean

Toggles sitting with hand. Sitting with keybind and command still work when off.

### main-hand
**Type:** [Hand Setting](#hand-setting)

Configures sitting requirments for the main hand.

### off-hand
**Type:** [Hand Setting](#hand-setting)

Configures sitting requirments for the off hand.




## Hand Setting
The json entry to configure hand requirments for sitting.

### requirement
**Type:** Enum
\
**Type options:** `NONE`, `FILTER`, `EMPTY`

The state the hand has to be in to sit.

- NONE - Can sit no matter the state of the hand.
- FILTER - Can only sit if the hand is empty or an item matches the filter.
- EMPTY - Can only sit if the hand is empty.

### filter
The hand filter. Only used if `FILTER` is selected in the requirement.

#### invert-filter
**Type:** Boolean
Inverts the filter selection when true.


#### presets
The selection of preset hand filters to choose from.

##### block
**Type:** Boolean

Allows blocks to be held when sitting.

##### food
**Type:** Boolean

Allows food items to be held when sitting.

##### usable
**Type:** Boolean

Allows usable items to be held when sitting. (shields, bows, ect.)


#### custom items
Custom items to be (or not be) filtered.

##### item-ids
**Type:** String List
\
**Example:** `"minecraft:torch", "!minecraft:redstone_block"`

##### item-tags
**Type:** String List
\
**Example:** `"#minecraft:bookshelf_books", "!#minecraft:lectern_books"`

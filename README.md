# Example Quadrum Config Folder

So I've included two blocks from [Wanderlust Reloaded's](http://forum.feed-the-beast.com/threads/1-7-10-wanderlust-reloaded-questing-adventure-magic-tech-hqm-over-250-quests-tabula-rasa) Tabula Rasa settings to demonstrate how easy it is to convert from one to the other.  The textures aren't the real textures, but this is a demonstration that needs to be finished off anyway, so...  \*shrugs\*


## Folder layout

Anyway, this is what the `config/quadrum` folder would look like.  You can also add an `items/` folder as well as the `blocks/` folder if you want to add items (check out [the GH wiki](https://github.com/dmillerw/Quadrum/wiki/Items) for the list of settings that items can have), but as the Tabula Rasa file seems to only have blocks in, I only did blocks myself.

Inside `blocks/`, you'll find files that end with `.json`, and files that end with `.png`.  The former are the configurations, the latter are the textures you want to include.  There is also a `lang` folder, I'll come to that in a moment.


## JSON layout

The layout of the `.json` files is as follows:  (Note: in terms of actual files, the "midnight\_black" block has pretty much all the features, whilst the "mocha\_brown" block uses the fact that setting a material also sets defaults on what properties a block will have.)

```js
{
  {
  // Unlocalized name.  You shouldn't ever see this, but you'll
  // need to remember it - this is the name that will be used
  // by recipes such as Minetweaker.
  "name": "modern_midnight_black_block",
  
  // The default texture.  Using the texture-info key (not
  // shown here), you can set the individual textures for any
  // particular side.  You should then put a texture file with
  // the same name that you've written here into the same folder
  // that you've put this file.  If you want to add texture
  // metadata, I believe that's supported.  If you don't, you don't
  // need to worry about it.
  "default-texture": "modern_midnight_black_block.png",
  
  // Inherits a lot of default properties from the "stone"
  // material (in the code this includes things such as sound,
  // flammability, resistance, hardness etc.)
  "material": "stone",
  
  // Easily make slabs, stairs, etc.  Default is stone, but if
  // you want a slab variant of a particular block?  Just create
  // a new .json file with this set to "slab".
  "type": "block",
  
  // Adds the block to the ore dictionary by default.  Probably
  // not necessary in this case, but you might find it useful so
  // I added it just in case.
  "ore-dictionary": ["blockMidnightBlack"],
  
  // These are fairly self explanatory.
  "hardness": 1.5,
  "resistance": 10.0,
  
  // Make a block that emits light.
  "light-level": 0,
  
  // Make a block that emits redstone (like a redstone block, say).
  "redstone-level": 0,
  
  // How long it will burn in a furnace.
  "burn-time": 0,
  
  // Probably more useful if you were making custom items, but this
  // allows you to specify the maximum number of items in one stack.
  "max-stack-size": 64,
  
  // 0 = a wooden pickaxe can mine it, 1 = stone pickaxe, etc.
  "mining-level": 0,
  
  // Doesn't make the block invisible, just changes the rendering
  // code slightly.  You might want to look into this more, but it
  // would probably allow you to add extra glass-type blocks in.
  "transparent": false,
  
  // You can't walk through this block.
  "collision": true,
  
  // Tbf, most of this doesn't need to be here, it's defined by the
  // "stone" material, but just in case, we'll emphasize that this
  // block can't be burned up.
  "flammable": false,
  
  // You can't grow crops in this block.
  "soil": false,
  
  // In this case (because stone) a pickaxe.
  "requires-tool": true,
  
  // If you wanted, you can actually set specific drops that will
  // drop when this is broken.  (e.g. diamond ore drops diamond gems,
  // redstone ore drops redstone etc.)
  "drops-self": true
}
```


## Important notes

IIRC, the JSON decoder (thing that converts these files into something the programmer can use) is fairly strict, which means that you can't add any comments (lines beginning with `//`).  It also means that every "key": "value" pair must be followed by a comma, except the last one which must not.  Thirdly, all the "keys" must be surrounded by quotation marks, but only some of the values should be.  Look at the example files in the `blocks/` directory to show you which bits should be quoted and which shouldn't.


## The `lang` directory

Language files are really useful, because they set the name of a block, but allow that name to change depending on which language is being used by the user.  This means that people playing Minecraft in (say) Russian don't have random items or blocks that insist on being written in English.  (That is, assuming you've put down the correct Russian translation.  If you aren't a native or skilled speaker of another language, the general advice is to not translate - particularly if you just use Google Translate.  Instead, when people report issues with your lack of translations, ask them to help translate for you - it's a simple thing that anyone can do.)

A language file looks a bit like this:
```lang
tile.modern_mocha_brown_block.name=Modern Mocha Brown Block
tile.modern_midnight_black_block.name=Modern Midnight Black Block
```

It should be fairly self-explanatory.  The bit before the equals (`=`) sign is the unlocalized name of the item, while the bit afterwards is the name you want to give it.  Always remember the `tile.` at the start and `.name` at the end of the unlocalized name, however.

In this case, you should save this in a file called `en_US.lang` in the `lang` directory.  `en_US` means "english, of the United States variety", and the `.lang` suffix just means that this is a file that defines the language.

If you wanted a language file for another language, you'll need to look up the official language code for that language (use Google, Wikipedia etc), and then replace `en_US` with the new language code.  For example, the file for Finnish would be `fi_FI.lang`.


## More help

If this isn't enough of an explanation (I rushed a lot of it, sorry!), the easiest thing to do for now would probably be to either PM me on Reddit (/u/MrJohz) or to file an issue here.  (There's a menu to the right - hover over one of the buttons and it should say "Issues".)


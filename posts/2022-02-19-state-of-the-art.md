# Frontier Mods: State of the Art

As of late February 2022, **no work is being done** on Frontier Mods.

This is because I, the sole author of these mods, have stopped playing *Cataclysm* in a while. I am currently busy with other personal projects as well as other games.

__I'd like to return to modding *Cataclysm* in 2022__, after the 0.G stable release, either in the *Dark Days Ahead* variety or with my own version.

Even during active development, updates were slow or minimal. This is because the scope of all major Frontier mods is vast for a single developer. To abate the intensity of process, I'd decided to develop a middle step between adding content and producing viable JSON: generators.


## Generators

In a more general sense, these generators were meant to take an item of non-JSON content, modify it in some way that is easier to do programmatically than manually, and produce JSON for use with the mods, which would then be automatically supplied to the mods' respective repositories, for players to download.

The reason I went with a middle-step option, as opposed to finding a way to work better with JSON, is that there are no JSON editors are that easy to use, no matter how far and how wide I would search, on a scale that is required for me to write Frontier Mods-tier content. Each editor I've tried so far has either been clunky, required me to adapt my code style, or was a downgrade from writing JSON manually.

All of Frontier Mods Extra were written by hand because they're all made up of a handful of independent, simple entries that I would have no problem managing manually. Frontier Mods proper, by contrast, have a large number of entries in multiple categories, each of which has to be managed effectively.

One reason for such managerial requirements is that each object must be provided with correct dimensions, this being a game that values realism. I had a workflow consisting of opening several windows of the browser, each with a different site, where I would find the numbers for the item, convert them where appropriate, then calculate the dimensions.

This worked for a while: it's a workflow I've been using for weeks during the development process. With the scale Frontier Mods intend to cover, it's a workflow that would eventually lead me to despise the work process in its entirety. (Give a shit about the tools you choose for the work you care about. Don't settle for bad tools if it's something you're aiming to work at for a while.)

So: generators.


### The Roadmap for Generators

In short: generators for Frontier Mods should take any number of YAML files from a specific folder, modify each one as instructed in the supplied processing files, and output the resulting JSON in the mods's respective repos.

These generators are JS-based, which I have skills for. Working with JS also means being able to use GitHub Actions to run the generators directly, which may become useful in the future. Right now, Actions are set up to run a Gulp instance for the entire process. Aside from being slower than it needs to be, it's a good option for something of the nature of GitHub-hosted mods.

I chose YAML for data structure because it's the easiest markup available to write by hand. That's the biggest gripe I have with JSON: the abundance of control symbols that could easily be abstracted by a competent, token-based editor. (A competent, field-based JSON editor would make the YAML requirment obsolete, allowing generators to work with JSON directly. There are many options for parsing and modifying JSON in JS.)


### "The Goal of This Project is to Make Itself Obsolete"

One thing that could make generators entirely unnecessary for any mod is a way to programmatically process JSON by leaving instructions in the JSON itself.

One example would be being able to supply volume data of an item by telling the game to calculate given values in provided manner. In JSON, this could be structured via custom tokens – something that can be seen in JSON supersets like JSOX. It could look like this:

```
	"volume": Calc(2in*3cm*1ft*0.8)
```

The token `Calc()` could represent an instruction to calculate the provided mathematical equation, including converting provided values into the appropriate units of measurements. In this case, the equation also includes an 80% modifier: in volume calculations, it's safe to assume that a non-rectangular object takes up less space than the rectangle its volume computes to. Since not all items provide detailed information on their volume in reality, modifications would have to be made.

As far as the game's item parser is concerned, this is equivalent to (because the equation computes to):

```
	"volume": "372 ml"
```

Another example would be partial inheritance or patching.

By default, the game makes it very difficult to apply partial properties: it requires long chains of manually-set-up inheritance per entity, as it's unlikely any two objects would have the exact same properties.

Being able to supply partial data to an entity would allow managing similar objects easier, without forcing them to be identical.

A good example of that would be something I've been working with a lot in Frontier Mods: gunmods. Being able to define a gunmod as being made of one of the three most-common materials in gunsmithing (aluminum, steel, or titanium) without removing the option for manual data (e.g. optics can include plastics and/or glass) would make managing the literal hundreds of gunmods per mod that much easier.


## Frontier Mods: A Roadmap

The entire premise of Frontier Mods is to vastly expand the variety of items available to the player character. Weight, volume, tool qualities, gunmod parameters, clothing coverage, and many other qualities should all play a role, as they do in reality.

Beyond that, a major goal of these mods is to add functionality.

Upon first release, [Armory](https://github.com/FrontierMods/Armory) demonstrated a modular-equipment system. It was later implemented in the base game. The feature is currently available in experimental builds, and is expected to hit stable release in 0.G. As such, the purpose of Armory moves away from implementing the system to supplying it with items.

In the demo available currently, [Gunsmith](https://github.com/FrontierMods/Gunsmith) presented an in-depth, highly-modular version of firearm modification, which is in line with what modern firearms are capable of.

A yet-unreleased mod, Workshop, is aiming to add a (convoluted but usable) way to 3D-print objects out of plastic, metal, biomaterials, and more. (This was also done previously in a now-deleted mod of mine, Homestead. Its remnants could still be found in mod archive collections, such as [TheGoatGod's Community Mod Compilation](https://github.com/GMC-Modding-Team/Community-Mod-Compilation-redux/tree/master/data/Unleash_The_Mods/Working_mods/Homestead_Instruments_Inc).)

Each mod is focused on a different domain within the game.


### Gunsmith

The ultimate goal of Gunsmith is to re-establish each base-game firearm as a moddable platform, as well as to provide a variety of options for modifying each firearm according to its capabilities.

The first demo showed how this could be accomplished on the most extensively-modifiable firearms platform today: the AR-15. The AR-15 has a massive worldwide aftermarket, with parts ranging from handguards to specific bolts and nuts. Using it to demonstrate the potential (as well as the headache) of the system was the best decision for the mod.

Most modern firearm platforms have aftermarkets of their own, though significantly smaller. The roadmap of the mod could roughly be mapped to how large the aftermarket of each platform is, from biggest to smallest. Ultimately, all base-game guns with replaceable parts are intended to be covered under Gunsmith.

(Adding support for mod firearms is going to be left in the hands of mod authors or third parties. The Gunsmith repo maintains a growing library of knowledge about the workings of firearms. This should make "conversion" of mod guns to the Gunsmith blueprint easier.)

Aside from that, here's what's intended to end up in the full v1.0 release of Gunsmith:

- separate skill, Gunsmithing, for measuring one's broad understanding of firearm modification: installing attachments, replacing parts, jury-rigging attachment points, and jury-rigging custom firearms of various levels of quality
- gunsmithing tools as a requirement for most sorts of gunsmithing, including installation of many types of attachments
- parts wear: critical parts of the firearm are going to experience structural wear over use, and will require mending in order to not get suddenly destroyed
- trinkets and other forms of firearm decoration, for roleplaying or personal preference
- adjustments to baselines of part stats and gun skills, for a more realistic effect
- simplified version of Gunsmith, with a minimal set of generic attachments, intended for players who enjoy the base game's generalized treatment of firearms and attachments


### Armory

Armory's goal is to provide the player with a real variety of protective and support gear: bullet-resistant vests, plate carriers, rigs, belts, and – perhaps most importantly – a plethora of small, specialized pockets. The intention behind these pockets is to allow players to customize their carrying capacity, at least as far as military and support equipment – such as tools, radios, and medical implements – is concerned.

Much of the functionality Armory intended to bring along – namely, modular equipment – has been implemented in a more generic fashion (meaning more cases can possibly be covered) within the base game, intended for release in 0.G. As such, the focus of Armory would shift from functionality to assortment of gear.

The basic principle driving Frontier Mods is "variety matters". Fashion, roleplaying, personal preference, or micromanagement of weight and encumbrance against carrying capacity and protection: small, yet not insignificant, differences in available items should provide the player with choice without paralyzing them with it.

Long story short: more stuff, with more-considered differences.

The v1.0 release would consist of more fleshed-out classes of gear, with multiple items per class in most cases. Adding entirely unexplored categories of gear would be followed by expansions (and some rework) of existing ones.


#### Armory: Holsters

Of particular interest to me currently are holsters. The game treats each holster as universal, in that it's meant to fit all sorts of compact arms in. Universal holsters do exist, but the holster market is full of fitted holsters: ones shaped to fit a specific model of small arm, or even a specific item (e.g. a pistol with a particular laser sight attachment).

The advantage of a fitted holster is the grip with which it holds the small arm: the weapon is meant to fit tightly in, thus making it far less likely to fall out. Since pocket instability is not implemented in the base game, a more grounded function of a fitted holster might be speed of the draw, reflecting (assumed) practice for one specific gesture of drawing the gun. It's a cop-out that allows me to explore an interesting new dimension of equipment.

Implementing specific-item-fitted holsters is nearly impossible in *Dark Days Ahead* without going insane, for me or the user. At best, assuming very few available attachments as in the base game, it would require dozens, if not hundreds, of crafting recipes, or a very loose volume-based restriction that could easily be gamed or become an unnecessary obstruction.

Much like many of the large-scale ideas intended by these mods, this is best implemented on the engine level, in a way similar to [firearms-as-pockets](https://github.com/FrontierMods/Design/blob/main/points/001-firearms-as-pockets.md).


### Dapper

Dapper does to civilian clothing what Armory does to military gear: brings variety, in fashion as well as in-game functionality. From high-class suits to affordable clothing that are better than nothing at all, Dapper seeks to expand one's choices for clothing.

The purpose of the mod is simple, so talking about it further is wasting time. However, there are a few interesting aspects of the mod's development that may be of interest to readers of this blog.

One fact of modern fashion is churn: it's impossible to find the same article of clothing in the same stores during the same season next year. As such, unlike other relatively-stable industries, like military gear and gun parts, it's also impossible to model the world of fashion as it would've been in New England (the setting of the game) at any point in the future, save for a handful of brands.

A decision, then, is to be made: do I take a step away from modelling the real world with precision and rely instead of fictional brands which I can control (and justify presence of via own lore), or do I use real brands, but make up fictional items for each, trying to follow the style and the feel of each brand with attention?

I'm just fashion-conscious and design-aware enough to realize the importance of (1) maintaining the same style across a given brand, (2) maintaining the same feel while transitioning between (expected) reality and its representation. Most players will probably not consider this a big deal, and will simply enjoy a good collection of new kinds of clothing if it's done well.

This matter is so far to-be-determined. I do, however, have a set of semi-developed distinct fashion brands to use, should I need them.


### Other Mods

Right now, Frontier Mods includes 8 mods, of which 3 are listed above. (Core mod doesn't count: it adds no functionality of its own, instead serving as a shared base of resources for all of them.)

All of these mods are intended to be reasonably wide in scope. Some take it steps further and introduce "new" mechanics.

In short:

- Workshop: adds stationary tools, and introduces 3D printing
- Toolkit: adds compact, portable tools, like pen knives or electric screwdrivers
- Comforts: adds small material comforts, like resealable thermoisolated water bottles and mood rings
- Computation: enhances computer functionality, introduces a variety of ways to get and use computational power, including CAD and AI-assisted automated design
- Recharge: overhauls the current energy system to more closely resemble reality

One thing I'd like to add here is that for Computation, there's a potential for effectively coercing the pocket system for managing of digital files. (Volume of the "item" of a file would then correspond with the volume of the actual files; 1 ml = 1 kB.) This is yet to be proven experimentally. If successful, the system could be used to transfer specific files, like apps and blueprints, which could then be used for "crafting" with in-game CPUs / GPUs.
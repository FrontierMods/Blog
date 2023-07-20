# Frontier Mods is Back in Business

It's been a hell of a year-and-a-half.

With a renewed interest in modding the game stemming from 0.G stable and a breadth of new features, Frontier Mods is now being worked on again.

The (re)start is going to be slow. An overabundance of enthusiasm tends to fizzle out unless progress is met with results. Developing a massive overhaul like Gunsmith by hand would've certainly burned me out, due to the sheer amount of manual coding I'd have to do. (JSON is *not* pleasant to work with by hand.)


## The Next Mod: Loadout

The next mod is going to be Loadout: a collection of varied gunmods. The goal is the same: to ground the game further in reality by introducing a variety of real-life equipment in a way that enhances the gameplay by providing more options. Basically: more is better if more is also different. Think of it as Gunsmith without abusing the stiff gunmod system.

Loadout will follow the in-game rules regarding gunmods: installing and removing parts will magically vanish and recall the implied existing parts (like the iron sights or the barrel or the trigger). This is an unfortunate compromise, but it is better to have a mod than wait until everything falls into place.

Ideally, Loadout would also require players to use appropriate tools for gunmod installation, but that would require both a good supply of tools (which would be provided by one of the mods under the Frontier Mods umbrella) and a significant overhaul of all the guns currently in the game (which would be implemented with a different Frontier mod). In other words, this is plans for later.


## After That

After that, there are a few things I'd like to do that should be relatively-easy to accomplish.

One of them is a different approach to survivor gear. The goal is to make it so that survivor gear, in-universe a customized piece of equipment from the character's own design, must be designed first, which would require a certain degree of skill and proficiency. The idea is to:

* finally make use of all the pens and paper available in the game
* juxtapose one's in-game survival with the hierarchy of needs model, where self-expression comes much, much later
* experiment with the approach and see if it would be viable to expand on for other types of gear and equipment

It's not meant to be an overhaul and would probably be released under the Frontier Mods Extra brand, where all the small and independent mods by me end up. If the results are well and the players feel enticed by the idea, it could be expanded further.

Several ideas like that, all experimental. We'll see.


## Frontier Mods Proper

There's a rough plan on paper about which direction to take Frontier Mods in. Long story short: it's meant to be a modular overhaul of the game, with each mod adding its own layer of changes and content.

The [Core](https://github.com/FrontierMods/Core) mod would likely remain the sole universal requirement for other Frontier mods. Its goal is to house all the big and small changes about the game that most other mods would likely use in one capacity or another. Tool qualities, item dimension fixes, materials... It would also house the overarching lore of the modpack, something that may be of interest to players looking for more fiction in their fiction.

Each Frontier mod would then augment base game's content and add on top of it. Main Frontier mods are intended to be large, all-encompassing collections of items and new concepts within their domain: for example, [Gunsmith](https://github.com/FrontierMods/Gunsmith) is that for guns, gunmods, and their associated tools, and [Armory](https://github.com/FrontierMods/Armory) – for combat equipment, armor, and relevant gear.

Each large mod would then likely be supplemented with submods, each – a different take on the same concept. For example, Gunsmith would likely ultimately have a submod for:

* "enhanced warfare": parts and attachments that aren't feasible today but may be in 10 or 20 years,
* "future warfare": highly-advanced pieces of gear just on this side of realistic for science fiction,
* The Third Doctrine: a variety of 3D-printed, custom, jury-rigged, and 80% guns and ammo,

and so on. These are meant to be supplementary, aiming to satisfy one's tastes and preferences, rather than complete one's experience with the game (that's the goal of the main mod behind them).


## But When?

Given the size of changes intended with each mod, and my ADHD and the amount of time I effectively have available, releases are likely to take a very long time. I could still be pushing small changes here and there, but something substantial might take a while.

The biggest hurdle for me is the fact that most of the work would have to be done by hand. There are no good JSON editors for Windows that work at my speed; if I have to stumble over a quotation mark or a comma, which would break my concentration, that is not a good JSON editor.

I've talked about generators before: a custom Node.js-based solution for rendering valid *Cataclysm* JSON from a third markup language (e.g. YAML, which is a lot easier to write). I think this is still the way to go, and given the research I've done into it so far, I think it's both viable and much easier to work with than manually writing JSON entries. However, that, too, will take time.

I'm not opposed to releasing smaller mods, done manually, in the meantime: any result is better than no result. But it's not a good solution for something of the scale of Gunsmith, which aims to completely overhaul the gunmodding system, including by adding tool requirements and gun-/platform-specific attachments (like Weaver rail scopes for older Western arms and side-mounted scopes and rail attachments for some of the older Soviet AKs). Working at scale means you must eliminate a lot more friction than with smaller projects, otherwise that friction is going to keep you in place once enthusiasm runs out.

Beyond that: I'm the sole developer for the entirety of Frontier Mods. Finding someone to work on them who shares my vision *and also* is on the same wavelength as me is... I do believe in miracles, but I don't think *expecting* them is a good idea. (That said, if you do want to help me with these mods, reach out, and we'll talk. My email is listed on my GitHub profile page.)

So... yeah, might take a while. But I'm very excited to be back and playing *Cataclysm* again.
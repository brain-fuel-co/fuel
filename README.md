# Ideas!

## Procedural game generation
A game engine crafted from the ground up to be amenable to proc gen. AI voice, automated landscape generation, automated dungeons, LLM-generated dialog, etc. In-game hints, journals, quest markers, and so on, is generated via metadata from the procedurally-generated content.

### Program Architecture
Architecture is what we call **Unidirectional Compositional Architecture**. This means that we begin with a gross layer, which is fed into a series of progressive refinements. It's *Unidirectional* because the gross layer is always resolved first. It's *Compositional* because the process resembles function composition: in the composed function f(g(h(i(x)))), i(x) is the most gross layer. We can flag things that should persist from iteration to iteration to preserve them from the vagaries of the random generators. For example, town A and town B always exist with certain buildings. But the layout is slightly different each time, and the trip between them is a different road each time. We should be able to flag certain characteristics as things that cannot be changed: this path up a mountain must be no steeper than such-and-such an incline, this group of NPCs must always have an archer, this monster must be defeatable by players of level nine or greater, and so on.

Procedurally-generated content always comes with metadata used to generate in-game information; this requires *radical inspectability*. Metadata must be used to determine whether or not the game can be finished. For example, if the first hill requires an agility of X to climb, then the AI should take note and not allow your team to have all characters with agility < X, whether AI or player generated.

### Process
#### Architecture
Our process is **Consecutive Bridge-Burning**. This means that, as the creative process continues, we lock the gross layer when we're finished with it, and move on to the next finest layer. Each time we finish a layer, we are artificially narrowing our scope by no longer allowing ourselves to change that layer. Imagine a series of bridges crossing consecutive moats. We burn each bridge as we decide there's no turning back, then finally arrive at the center.

For example, suppose we're generating a game world. The most gross layer would be drawing a topographical map with features such as ice sheets, forests, deserts, etc. "painted" on the surface. Once we're finished with this layer, we lock it, meaning that the topographical map will be used to generate the world and any further edits will take place on the generated content. We can make edits on finer layers before or after grosser layers are locked, but cannot edit a locked layer. By necessity, if a layer is locked, so is every grosser layer.

#### UX
An artist working on textures should be able to use a text prompt to generate a texture, which they can then perfect by hand. This should also be available at other levels of abstraction, e.g. procedurally generating a town or a single building. Once a town is generated, we only generate things with higher resolution than a town, in keeping with CBB.

### Marketplace
It is not feasible to create a proc gen tool suite that addresses every game developer's needs. However, it is feasible to create a procedural generation marketplace, where mod creators and developers can createa and share their tools for procedural generation. This implies the ability to interface with independently developed tools on a program level, which requires modular coding. 

## Collaborative Document Editing
A Quora answer I read recently by a professional writer talked about how he used Google Docs to do most of his writing. Google Docs does not have a great interface and it's not especially fast or convenient. The only reason he uses it is because it makes collaboration easier.

Google Docs was constructed based on older word processors, such as Microsoft Word. Much of the unwieldiness comes from this.

A collaborative document editor could be quite useful. Minimal typesetting and formatting facilities. You can use some other piece of software for that. Just a collaborative document editor set up to make collaboration as painless as possible. Make sure it can export in formats that typesetting and formatting software can use.

## AI Workout Critic
There are plenty of workout apps for keeping track of exercise. But when it comes time to critique your workout or correct your form, you still have to post a video of yourself on Reddit or something.

Unless we can train an AI to look at a video of you working out and tell you what you're doing wrong, i.e. not getting low enough on a deadlift.

## 3D Printing That Doesn't Suck
Despite being a raging libtard, Franklin Veaux makes a [good point](https://qr.ae/p2CnWz) about 3D printing. There are two main issues therein:

- 3D printing interfaces suck. It remains a niche hobby largely because you have to have an engineering mindset, if not an engineering background, to use one. We want to make a plug-n-play interface. Download a model. The software slices it for you, does all the hard work, and just fucking prints it. In order to do this, we would probably need to produce our own hardware/firmware/etc, and set it up to play nicely with our proprietary software.
- 3D printing mechanics suck. I haven't looked into it, but I suspect this is a body of mechanical/electrical engineering puzzles. There's not a ton of money in 3D printing (yet), so huge teams of mechanical engineers have not been employed to dissolve all these issues. Solving said issues for 3D printing *simpliciter* would be difficult. But if we just wanted to build an affordable consumer unit that works well, that would be more feasible. We could, for example, set it up so that the parts are easy to replace, and the parts are proprietary, so you can buy them from us when they break.

## AI Image Editor

- Most of the stuff I want to do with a photo editor is very simple. Take two pictures and stick them side-by-side. Crop an image. Rotate something. Desaturate. _These are all things that can be summed up in a simple English sentence_.
- Make an AI image editor that has a suite of basic point-and-click tools. But – here's the moat – these tools are either used or "summoned" by an English sentence, typed or spoken.
- For example, "I want to crop this. Show me the crop tool." That sentence brings up a crop tool, which you can use with your mouse and keyboard.
- On the other hand, "I want to put two pictures side by side and make them the same size." And then it will simply ask you to select two pictures from your computer. It will do the work for you.
- The premise here is that _most people neither want nor need photoshop_. I find myself Googling "put two images side by side" because I don't feel like downloading GIMP just to do some simple shit.
- In the end, the best interface would be dialogue-based. Here's an example: I give the computer an input – say, a picture I want to edit. I ask for a crop tool. I crop the picture. Then I say, "Okay, now reverse it horizontally. Now make it black-and-white. Now put a green monochrome over it. Now sharpen it a little. Increase the contrast just a hair. Thank you!"

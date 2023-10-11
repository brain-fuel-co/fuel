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

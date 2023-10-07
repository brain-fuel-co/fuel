# Ideas!

## Procedural game generation
A game engine crafted from the ground up to be amenable to proc gen. AI voice, automated landscape generation, automated dungeons, LLM-generated dialog, etc.

### Architecture

Architecture is what we call **Unidirectional Compositional Architecture**. This means that we begin with a gross layer, which is fed into a series of progressive refinements. It's *Unidirectional* because the gross layer is always resolved first. It's *Compositional* because the process resembles function composition: in the composed function f(g(h(i(x)))), i(x) is the most gross layer.

### Process

Our process is **Consecutive Bridge-Burning**. This means that, as the creative process continues, we lock the gross layer when we're finished with it, and move on to the next finest layer. Each time we finish a layer, we are artificially narrowing our scope by no longer allowing ourselves to change that layer.

For example, suppose we're generating a game world. The most gross layer would be drawing a topographical map with features such as ice sheets, forests, deserts, etc. "painted" on the surface. Once we're finished with this layer, we lock it, meaning that the topographical map will be used to generate the world and any further edits will take place on the generated content. We can make edits on finer layers before or after grosser layers are locked, but cannot edit a locked layer. By necessity, if a layer is locked, so is every grosser layer.

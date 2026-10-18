# Assets and credits

## Three.js

Three.js 0.186.1 and the GLTFLoader, SkeletonUtils and BufferGeometryUtils modules are from the official `three` npm package / https://github.com/mrdoob/three.js. MIT license, preserved in `dist/vendor/THREE-LICENSE.txt`.

`dist/models/soldier/` is the animated Soldier example model distributed in the Three.js repository:
https://github.com/mrdoob/three.js/blob/dev/examples/models/gltf/Soldier.glb

It is bundled from that public example distribution, together with its repository MIT license. It contains the original textured character and Idle, Walk, Run and TPose clips. No separate Mixamo downloads are included.

## Quaternius characters

- `dist/models/demon/`: Quaternius **Ultimate Monsters**, CC0 1.0. Creator's pack and license: https://quaternius.com/packs/ultimatemonsters.html and https://creativecommons.org/publicdomain/zero/1.0/ .
- `dist/models/skeleton/`: Quaternius **Animated Monster Pack**, CC0 1.0. Creator's pack and license: https://quaternius.com/packs/animatedmonster.html and https://creativecommons.org/publicdomain/zero/1.0/ .

The GLB conversions were obtained from the public asset mirror at https://github.com/ilrein/warptracker/tree/main/public/models ; its https://github.com/ilrein/warptracker/blob/main/ASSETS.md identifies these conversions and their original packs. The creator pack pages explicitly grant personal and commercial use under CC0. Character animation tracks and skeletons remain embedded in the GLBs. Downloaded 18 October 2026.

## Original project work

The articulated Siege Walker and serpent models, boss attachments and weak points, rifle assemblies, environmental geometry, terrain textures, UI, visual effects, sound synthesis, gameplay code and level scripting were created for this project. No Space Harrier game assets or audio are included.

Models are stored as multipart GLB data with JSON manifests and reassembled before parsing. The Soldier asset has unused UV sets removed, reduced animation key density with interpolation, and 512-pixel textures for mobile delivery. All meshes, joints and animation clips are retained. Three.js library modules are minified with esbuild.

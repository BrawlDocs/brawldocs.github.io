# Creating Franchise Icon Models

1. Open a new Blender scene, delete cube
2. In BrawlCrate, export a vanilla MDL0 node from STGRESULT.pac. These are found in “Misc Data [110]” and are named InfResultMark##_TopN. Export as .dae
3. Ensure you have a .svg of your icon. If you do not, you can take an image in Photopea and convert it: https://www.photopea.com/learn/vg-vectorize
4. In Blender, go to File > Import and import the vanilla icon as .dae
5. Repeat this but for your SVG file
6. Select your new icon’s mesh and go to Object > Convert > Mesh
7. OPTIMIZATION: In edit mode, do the following with everything selected You can see how much it’s helping by clicking the arrow next to the overlays in upper-right corner and checking “Statistics” ():
    - Edges > Un-Subdivide
    - Mesh > Delete > Dissolve Faces
    - Mesh > Delete > Limited Dissolve
    - Mesh > Clean Up > Degenerate Dissolve
    - With each step, make sure it looks good. You can also try each step multiple times.
8. Select again and go to Object > Set Origin > Geometry to Origin
9. Rotate, move, and scale your icon to align correctly with the vanilla one
10. On the right, in the Scene Collection, move your new icon’s object into the same collection as the existing icon. Then, shift-click and drag it into the “Armature” that the old icon is in.
11. Go to the material properties of your new icon and set it to match the material of the vanilla one (should be lambert2).
12. Go to vertex groups and add a new vertex group. Name it the same as the first vertex group on the existing icon, probably “InfResultMark01_TopN”.
13. Click the new icon object, switch to Edit mode, and highlight everything. With your new vertex group selected, ensure “Weight” is set to 1.000, and click “Assign”.
14. Switch to Weight Paint, hit “Weights > Normalize All”, then expand the brush radius to take up the whole icon. Spam click till it’s pure red.
15. Delete the old icon (Right-Click > Delete Hierarchy).
16. Go to File > Export > FBX. Export somewhere. Ensure on the right side, only “Armature” and “Mesh” are selected under “Object Types”. Ensure up is Y and forward is -Z.
17. Open FBX converter. Put your newly exported .fbx in. Change the output format to “DAE Collada” and convert.
18. In BrawlCrate, open STGRESULT.pac. Create a new mdl0 for your model, or select an existing one you wish to replace. Right-click and select “Replace”. Choose the .dae you converted earlier. Make sure “Blender Bone Fix” is true.
19. Go to the bones, delete any with _end added to them.
20. Export material and shader nodes from one of the existing mdl0s, then replace the new icon’s materials and shaders with them.
21. Under “Objects, click the object and change its settings to match a vanilla one.
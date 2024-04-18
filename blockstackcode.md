 ``` mathematica
h = 0.25 (*height of each block*)
n=5 (*number of blocks under first one*)
f=(2-Sum[1/(2i),{i,#}])& (*calculates how far out each block should be*)
Table[f[i],{i,1,5}] (*block positions*)

BlockStack =Table[Cuboid[{f[i],0,-h(i)+h(n)},{1+f[i],1,-h(i)+h(n)+h}],{i,n}] (*most of the blocks*)
ExtraBlock = Cuboid[{1+1,0,h(n)},{2+1,1,h+h(n)}](*first block*)

AllBlocks = Graphics3D[{BlockStack, ExtraBlock}](*all blocks displayed in 3D*)
CloudExport[AllBlocks, "STL", "blockstack.stl"]
```

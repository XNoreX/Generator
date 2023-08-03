# Generator
Procedural generator of roads and buildings

In order to use the procedural generator, you need to move the "BP_Generator" class to the stage and configure its parameters, for this you need to select the generator on the stage and go to the Details tab:
"Road Modules" is an array with road tiles, you can specify a straight road and an intersection (This is enough), building tiles do not need to be placed here.
"House Modules" is an array with building tiles, you can specify as many as you want.
"Area Size" is the parameter responsible for the size of the generation area.

After all the tiles are specified and the parameter of the size of the generation zone is also the first thing you need to generate roads, the "Generate Roads" button is responsible for this. If you don't like the road grid, then you can click on the "Generate Roads" button again and the cycle will repeat. 

After the road grid is created, you can fill the empty space between the roads with buildings, the "Generate House" button is responsible for this, it works similarly to the generation of roads.

The "Clear Roads" and "Clear House" buttons are responsible for clearing the grid of the corresponding tile types, when you click on these buttons, there is no complete removal of tiles, the tiles are removed in parts each time you click.

The "Clear All" button completely and instantly clears the generation area of all tiles.

Tile Parameters
The actor tile itself inherits from the BP_Module class and has the following parameters:
You can create as many tiles as you want, it is important to inherit them from the parent class "BP_Module"
Sockets X; -X; Y; -Y; Subsequent tiles are attached to these sockets during generation, for roads it is strongly recommended not to move sockets in different directions along their plane (Needs to be finalized)
Static Mesh is the main static mesh of an object, here you can place a 3d model of an object of such a scale that its boundaries fit into the boundaries of sockets. You can also add additional Static Mesh.

The Default:
Module Type parameters are the type of this module, stored in the Enum class "E_ModuleType". You can add your own.
Allowed Road Module Type – Array with types of possible road modules
Allowed Roads Sockets – An array with available sockets on the places where allowed road modules will be generated.
Allowed House Sockets - An array with available sockets where the building modules specified in the generator class will be generated.




The plug-in for procedural generation allows you to create road networks from direct type tiles and intersections, as well as create buildings inside the resulting cavities, but when generating a road network, there is a need to refine the generation algorithm in the following:

1). You can add the probability of creating tiles so that straight sections are created more often and there are more places for buildings.
2). In some places, a straight road comes almost close to another straight road that stands sideways, you need to pay attention to this point.
3). At this stage, it is impossible to create very large tiles, their size is limited to a radius of 100units, this needs to be finalized in the future.
4). When creating a tile, you can spawn a tile not in place of the socket of a neighboring tile, but produce an Atach Socket To Socket.

# SWE_CAP2_Game_Automation
SEW_CAP_2_Game_automation

# Programming the# Programming the Farming Drone (Report)
## Introduction

The Farming Drone is a simulation game that aims to teach players about modern farming techniques and the importance of sustainable agriculture. The game objective is to guide the player through various farming tasks, such as planting, watering, and harvesting crops, while also managing resources and maintaining the health of the land.

The game features a drone that the player controls, which can be used to survey the farm, monitor crop growth, and apply fertilizers and pesticides as needed. The player must also manage the farm's water supply, ensuring that crops receive the right amount of water at the right time.

Throughout the game,I learn about different types of crops, their growth cycles, and the best practices for cultivating them. They will also encounter challenges such as pests, diseases, and weather conditions that can impact crop yields. By overcoming these challenges, players will gain valuable skills and knowledge that can be applied to real-world farming situations.

In summary, the Farming Drone is an engaging and educational game that combines simulation and strategy elements to teach players about modern farming techniques and the importance of sustainable agriculture.

# Tsble of Cotents

- [Code Snippets and Explanation](#code-snippets-and-explanation)
- [Challenges and Learnings](#challenges-and-learnings)
- [References](#references)
  
# Code-Snippets-and-Explanation
Write and explain your code along with recordings.

## Step 1: Farming on 1 tile

**Code:**
``` python 
while True:
    if can_harvest():
        harvest()
```

*Explanation:*
The code runs an infinite number of times and harvest the grass with the if condition.
*Demo:*
Video Demo:
![](./lv1.mp4)

*Notes*
- Using the code above I was able to get enough hay to unlock the tile
* These features were unlocked too: variables and functions.


## Step 2: Farming on 3x3 tile
*Code:*
```  python while True:
# Code to go around
move(South) # The drone moves southward.
while True:
    for i in range(get_world_size()):
        move(North)
        if can_harvest():
            harvest()
            if num_items(Items.Hay) <500:
                plant(Entities.Grass)
            else:
                plant(Entities.Bush)
    move(East) 
```
*Explanation and Notes:*

If the drone can harvest, it will do so. It Checks if the number of hay items is less than 500 than it will plat grass.
 If the number of hay items is 500 or more, the drone will plant bushes.

 Video Demo:
![](./lv1.mp4)
![](./scree)

## Step 3: Farming on 4x4 tile
*Code:*
```  python while True:
clear()
move(South)
#variable 
waterTankCap =100

Haycap =3000
woodcap = 1500
carrotcap = 1000

while True:
    for i in range(get_world_size()):
        move(North)
        x = get_pos_x()
        y = get_pos_y()
        if can_harvest():
            #harvest
            harvest()
            #watering
            watering()
            #planting
            planting()
    #next row
    move(East)
```
*Explanation and Notes:*

This code will move the drone around a 4x4 tile, checking if it can harvest. If it can, it will harvest. It will also check the water tank capacity and the number of items for hay, wood, and carrots. If the water tank is empty, the drone will refill it. If the number of hay items is less than 500, the drone will plant grass. If the number of wood items is less than 500, the drone will plant trees. If the number of carrot items is less than 500, the drone will plant carrots. If the number of hay, wood, or carrot items is 500 or more, the drone will plant bushes.

The drone will continue to move around the 4x4 tile in this manner, harvesting, watering, and planting as needed.

*Code:*
```  python while True:
def planting():
    #hey
    if num_items(Items.Hay) < Haycap:
        if get_ground_type() == Grounds.Soil:
            till()
            plant(Entities.Grass)
    #WOOD
    elif num_items(Items.Wood) < woodcap:
        if (x % 2 == 0 and y % 2 == 1) or (x % 2 == 1 and y % 2 == 0):
            plant(Entities.Tree)
        else:
            if get_ground_type() == Grounds.Soil:
                till()
                plant(Entities.Bush)
    #carrots
    elif num_items(Items.Carrot) < carrotcap:
        if num_items(Items.Carrot_Seed) == 0:
            trade(Items.Carrot_Seed, 5)
        if get_entity_type() == Grounds.Turf:
            till()
            plant(Entities.Carrots)
```

Explanation and Notes:

This code will check the number of items for hay, wood, and carrots. If the number of hay items is less than the hay capacity, it will plant grass. If the number of wood items is less than the wood capacity, it will plant trees. If the number of carrot items is less than the carrot capacity, it will plant carrots.

The code also checks if the ground type is soil and if the entity type is turf before planting. It also trades for carrot seeds if they are not available.

The drone will continue to move around the 4x4 tile in this manner, harvesting, watering, and planting as needed.

*Code:*
```  python while True:
def watering():
    #water tank
            if num_items(Items.Water_Tank) < waterTankCap:
                trade(Items.Empty_Tank, 5)
            #watering 
            if get_water() < 0.75:
                use_item(Items.Water_Tank)
```

*Explanation and Notes:*

This code will check the number of items for the water tank. If the number of items for the water tank is less than the water tank capacity, it will trade for an empty water tank. If the water level is less than 0.75, it will use the water tank item to refill the water tank.

The drone will continue to move around the 4x4 tile in this manner, harvesting, watering, and planting as needed.
 Video Demo:
![](./3.mp4)
![](./Screenshot%20(153).png)
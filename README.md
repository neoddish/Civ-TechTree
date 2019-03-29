# Civ-TechTree

A 'technology-tree-like' directed acyclic graph dataset. It could be used to test or support Graph-based Visualization Tools.

# What is "Civ"

"Civ" stands for [Sid Meier's Civilization](https://en.wikipedia.org/wiki/Civilization_(series)). It is a series of turn-based strategy video games. All the games centered on building a civilization on a macro-scale from prehistory up to the near future. The technology development of a civilization in the games is quite similar to the real history of human being.

The series was first released in 1991. There are six main games in it, now(2019). My favorite version is **Civ5** or [Civilization V](https://en.wikipedia.org/wiki/Civilization_V) with the full(second) expansion pack, [Civilization V: Brave New World](https://en.wikipedia.org/wiki/Civilization_V:_Brave_New_World)("**BNW**" for short). So, the dataset is based on the technology tree of this version "Civ5 BNW".

# What is a "TechTree"

"TechTree" is short for [Technology tree](https://en.wikipedia.org/wiki/Technology_tree). 

In strategy computer games, a technology, tech, or research tree is a **hierarchical visual representation** of the possible sequences of upgrades a player can take (most often through the act of research). Because these trees are technically *directed and acyclic*, they can more *accurately* be described as a **technology directed acyclic graph** in computer science or graph theory. The diagram is tree-shaped in the sense that it branches between each 'level', allowing the player to choose one sequence or another. Each level is called a tier and is often used to describe the technological strength of a player. 

# TechTree of Civ5 BNW

![tech tree in civ5 BNW](civ5BNW_techtree.jpg)
> Download the original image from [civfanatics](https://forums.civfanatics.com/media/techtree-bnw.3607/)

The technology tree of Civilization V: Brave New World begins with Agriculture, Pottery, Animal Husbandary, Archery, Mining... and vias The Wheel, Civil Service, Gunpowder, Steam Power, Computers... finally ends with Future Tech. There are 81 tech nodes in total.

These tech nodes belong to 8 tiers, or eras: Ancient, Classical, Medieval, Renaissance, Industrial, Modern, Atomic, Information.

Each tech node contains the following information: name of the technology, era, cost of technology points(a KPI in the game), required technologies as prerequisite, leads to technologies (actived after the current tech), combat units enabled after the current tech, buildings enabled after the current tech, other notes, quote to introduce the tech.

# Dataset

The dataset is a **graph** dataset. It contains the technology nodes as a **directed acyclic graph**. 

## Files

JSON file (expanded format)
- [Civ-TechTree/dataset/civtechtree.json](https://github.com/jiazhewang/Civ-TechTree/blob/master/dataset/civtechtree.json)

JSON file (tech for one-line)
- [Civ-TechTree/dataset/civtechtree.min.json](https://github.com/jiazhewang/Civ-TechTree/blob/master/dataset/civtechtree.min.json)

## Graph

Every node(exclude the begining node) has one or several *required techs* to enable it. This means the current tech node could be enabled only after all its required techs are reserached.

Every node(exclude the ending node) has one or several *leads to* technologies. These leads to nodes would be possible for enabling once the current tech node is researched. *Notice that these nodes may not be enabled immediately because they may have multiple required techs.*

## Keys and Values

Every tech node contains the following keys:

| Keys | Data Type | Description |
|-|-|-|
| tech_id | Integer | An index of the technologies |
| tech_name | String | Name of the technology |
| era | String | The era this technology belongs to |
| cost | Integer | Technology points cost to research this technology |
| required_techs | Array/List | A list of prerequisite technologies |
| leads_to | Array/List | Technologies that consider the current one as a required technology |
| units_enabled | Array/List | Combat units enabled to be constructed once the technology is researched |
| buildings_enabled | Array/List | Buildings enabled to be constructed once the technology is researched |
| notes | Array/List | Other benifits from the technology |
| quote | Dictionary/Object | "Celebrity quotes" to introduce the technology |

## Sample

Here is an tech node for the technology "Civil Service".

```json
    {
        "tech_id": 22,
        "tech_name": "Civil Service",
        "era": "Medieval",
        "cost": 275,
        "required_techs": [
            "Drama and poetry",
            "Horseback riding",
            "Currency"
        ],
        "leads_to": [
            "Chivalry",
            "Education"
        ],
        "units_enabled": [
            "Pikeman",
            "Landsknecht"
        ],
        "buildings_enabled": [
            "Pikeman",
            "Landsknecht"
        ],
        "notes": [
            "+1 Food for Farms along fresh water",
            "+1 Food for Terrace farms along fresh water",
            "Allows Open borders treaties"
        ],
        "quote": {
            "content": "The only thing that saves us from the bureaucracy is its inefficiency.",
            "from": "Eugene McCarthy"
        }
    }
```

# Thanks to

- [AntV](https://antv.alipay.com/zh-cn/index.html)
- [FANDOM](https://civilization.fandom.com/wiki/List_of_technologies_in_Civ5#Brave%20New%20World)
- [CIVFANATICS](https://forums.civfanatics.com/media/techtree-bnw.3607/)
- [Wikipedia](https://en.wikipedia.org/wiki/Civilization_(series))
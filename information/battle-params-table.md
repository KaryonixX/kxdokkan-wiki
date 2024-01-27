---
title: Battle Params Table
Sort: 3
---
[**Thanks to T6 for allowing me to reuse the UD wiki!**](https://twitter.com/ThievingSix) 

[**Be sure to check out his new Dokkan Wiki**](https://dokkan.wiki/)
### Efficacy Type 103 - Transformation

* **Eff Value 1:** Transform Card Id
* **Eff Value 2:** Turn Requirement
* **Eff Value 3:** Links to [battle_params](/information/database-breakdown#battle_params) `param_no`


| Idx 	| Description                     	|
|-----	|---------------------------------	|
| 0   	| Max Turns                       	|
| 1   	| Transform Movie ID              	|
| 2   	| Termination Movie ID            	|
| 3   	| Termination Hp Greater          	|
| 4   	| Termination Hp Less             	|
| 5   	| Termination Probability         	|
| 6   	| Returning card id               	|
| 7   	| Name Path `card_transform/label/card_transform_label_%03d_%s.png`                      	| 
| 8  	| BGM No                          	|

<br /><br />

### Efficacy Type 79 - Metamorphic Transformation (Great Ape Style)

* **Eff Value 1:** Transform Card Id
* **Eff Value 2:** Links to [battle_params](/wiki/information/database-breakdown#battle_params) `param_no` for Set #1
* **Eff Value 3:** Links to [battle_params](/wiki/information/database-breakdown#battle_params) `param_no` for Set #2

| Eff Value 1 	|                     	|   	| Eff Value 2 	|                          	|
|-------------	|---------------------	|---	|-------------	|--------------------------	|
| 0           	| Minimum Turns       	|   	| 0           	| BGM Number               	|
| 1           	| Maximum Turns       	|   	| 1           	| Light Bg Color (Red)     	|
| 2           	| Term Rate           	|   	| 2           	| Light Bg Color (Green)   	|
| 3           	| Is Invinicible      	|   	| 3           	| Light Bg Color (Blue)    	|
| 4           	| HP Requirement (?)  	|   	| 4           	| Dark Bg Color (Red)      	|
| 5           	| Unknown             	|   	| 5           	| Dark Bg Color (Green)    	|
| 6           	| Execution Count (?) 	|   	| 6           	| Dark Bg Color (Blue)     	|
| 7           	| Unknown             	|   	| 7           	| Pizza LWF ID             	|
|             	|                     	|   	| 8           	| Begin Movie ID           	|
|             	|                     	|   	| 9           	| Continue Movie ID        	|
|             	|                     	|   	| 10          	| End Movie ID             	|
|             	|                     	|   	| 11          	| Roaring SE Number        	|
|             	|                     	|   	| 12          	| Finish Roaring SE Number 	|
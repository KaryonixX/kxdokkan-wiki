---
Title: Damage Calculations
---
---
# Class: `DPuzzleGameController`
## Method: `calcDealDamage()`

```
 - Called by DPuzzleGameController::setupDealDamageAndActionBank()
 - Called by ActionBankMng::execDokkanMode()
```

**__Variables:__**

 - **Deck_Index** = Out of the 7 cards you bring to the battle, this is the index of the card currently attacking. Zero (0) being the first card, six (6) being the last card (friend lead). During rotations the cards keep their index.
 - **Enemy_Target_Index** = This is the index of the enemy you are targeting. Zero (0) being the first enemy.
 - **Unknown_Bonus** = To be determined.
 - **Is_Dokkan_Mode** = True/False
 - **Is_Critical_Attack** = True/False
 - **Damage_Multiplier** = Increased damage multiplier through SetupExtraActionParam's

**__Execution Steps:__**

 1. Calculate `Card_Attack_Value` of attacking card
    - Based on: card stats, ki meter, card passives
    - To be analyzed later: `DPuzzleGameCalcData::calcInGameCharacterAttackValue()`


 2. Check if attack `Is_Guarded`
    - Based on: card elements, card conditions, `Is_Critical_Attack`, and `Is_Dokkan_Mode`
    - To be analyzed later: `DPuzzlegameCalcData::checkGuard()`


 3. Calculate the `Element_Coefficient`
    - Based on: card elements, `Is_Critical_Attack`, element modifiers on attack and defense
    - To be analyzed later: `DPuzzleGameCalcData::calcModifierElementAttack()`
    - To be analyzed later: `DPuzzleGameCalcData::calcModifierElementDefense()`
    - To be analyzed later: `DPuzzleGameCalcData::getElementTypeCoef()`


 4. Calculate the `Same_Target_Coefficient`
    - This is a 0.1x multiplier of `Unknown_Bonus`


 5. Get `Random_Coefficient` between 1.00 and 1.03


 6. `Total_Damage` = 
    - `Random_Coefficient * Same_Target_Coefficient * Element_Coefficient * Card_Attack_Value`


 7. If enemy can resist, calculate resist rate
    - To be analyzed later: `DPuzzleGameCalcData::calcResistDamageRate()`
    - `Resisted_Damage` = 
        - `((100 - calcResistDamageRate) * Total_Damage) / 100`


 8. If `Damage_Multiplier` > 0
    - `Total_Damage = Total_Damage * Damage_Multiplier`


 9. Calculate `Enemy_Defense` value
    - To be analyzed later: `DPuzzleGameCalcData::calcInGameCharacterDefenceValue()`


 10. Set `Enemy_Defense` to zero (0) if:
    - Has certain status effect (unable to determine yet)
    - Is `Is_Dokkan_Mode` and not activating certain enemy skills (Efficacy Type: 1)
    - Is critical attack


 11. If `Is_Critical_Attack` is false:
    - `Total_Damage = Total_Damage - Enemy_Defense`


 12. If `Is_Guarded`, get `Guard_Coefficient`
    - `Total_Damage = Total_Damage * Guard_Coefficient`
    - `Guard_Coefficient` is always 0.5


 13. Get `Enemy_Damage_Reduction_Skills` (Efficacy Type: 7)
    - For each `Skill` that is being activated, reduce damage by `eff_value1 * 0.01` of that `Skill`
    - `Total_Damage = Total_Damage - ((eff_value1 * 0.01) * Total_Damage)`


 14. Get `Enemy_Element_Damage_Reduction_Skills` (Efficacy Type: 15)
    - For each `Skill` that is being activated, and attacking card element matches `eff_value1`, reduce damage by `eff_value2 * 0.01` of that `Skill`
    - `Total_Damage = Total_Damage - ((eff_value2 * 0.01) * Total_Damage)`


 15. If `Is_Critical_Attack` multiply `Total_Damage` by 1.25


 16. If `Total_Damage < 150`, calculate minimum damage value
    - Based on: attacking card ki meter.
    - `01 Ki - Min: 009, Max: 012`
    - `12 Ki - Min: 097, Max: 144`
    - `24 Ki - Min: 193, Max: 288`


 17. Get `Enemy_Damage_Increase_Skill` (Efficacy Type: 3)
    - If activated, increase damage by `eff_value1`
    - `Total_Damage = Total_Damage * (eff_value1 / 100)`
    
 18. `calcDealDamage()` returns `Total_Damage` for further processing
---
---
Title: Database Changelog
Description: A list of changes to the Dokkan database
---
---
## Japan 4.10.0 🡢 4.11.0

<br />

#### All Tables

 - The columns `created_at` and `updated_at` are now **REQUIRED**. 

<br />

#### Card Specials Table

 - Removed column `is_ultra_special`
	 - **WARNING:** For global version compatibility, do not include this column.
 - Added column `priority`
	 - Number
	 - Not required
	 - Default `NULL`
	 - If multiple specials are available to trigger, priority will help determine which one gets used.
 - Added column `style`
	 - String
	 - Required
	 - No default
	 - Possible Values:
		 - `Hyper` if 18ki or above
		 - `Normal` if 17ki or below
 - Added column `causaility_conditions`
	 - String
	 - Not required
	 - No default
	 - JSON string used to determine if a special will activate.
 - Added column `special_asset_id`
	 - Number
	 - Not required
	 - Default `NULL`
	 - Unknown usage at this time.
	 - **WARNING:** For global version compatibility, this value must be `0`.

<br />

#### Effect Packs Table

 - Added column `lite_flicker_rate`
	 - Number
	 - Required
	 - Default `0`
	 - Unknown how this value changes visuals at this time.

<br />

#### Special Sets Table

 - Added column `causality_description`
	 - String
	 - Not required
	 - Default `NULL`
	 - Describes the causality set in the `card_specials` table.

<br />

#### Special Views Table

 - Added column `lite_flicker_rate`
	 - Number
	 - Required
	 - Default `0`
	 - Unknown how this value changes visuals at this time.

<br />

 #### Sugoroku Maps Table
 
 - Added column `link_skill_lv_up_prob_rate`
	 - Floating Point Number
	 - Not required
	 - Default `0`
	 - Unused

---
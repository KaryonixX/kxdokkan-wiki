---
Title: '[SQL] Card Potential Totals'
---
```sql
SELECT
	potential_boards.id AS 'potential_board_id',
	potential_boards.comment,
	potential_events.type,
	SUM(potential_events.additional_value) AS 'total'
FROM
	potential_boards
LEFT JOIN
	potential_squares ON (potential_squares.potential_board_id = potential_boards.id)
LEFT JOIN
	potential_events ON (potential_events.id = potential_squares.event_id)
GROUP BY
	potential_events.type,
	potential_squares.potential_board_id
HAVING
	potential_events.type NOT IN ("PotentialEvent::Select", "PotentialEvent::Skill")
ORDER BY
	potential_boards.id ASC,
	potential_events.type ASC
```

| potential_board_id 	| comment 	| type 	| total 	|
|:------------------:	|----------------------------------------------------------	|-------------------------	|------:	|
| 10 	| B-rank AGL. 	| PotentialEvent::Atk 	| 3000 	|
| 10 	| B-rank AGL. 	| PotentialEvent::Defense 	| 3240 	|
| 10 	| B-rank AGL. 	| PotentialEvent::Hp 	| 2760 	|
| 11 	| B-rank TEQ. 	| PotentialEvent::Atk 	| 3240 	|
| 11 	| B-rank TEQ. 	| PotentialEvent::Defense 	| 3000 	|
| 11 	| B-rank TEQ. 	| PotentialEvent::Hp 	| 2760 	|
| 12 	| B-rank INT. 	| PotentialEvent::Atk 	| 3000 	|
| 12 	| B-rank INT. 	| PotentialEvent::Defense 	| 3000 	|
| 12 	| B-rank INT. 	| PotentialEvent::Hp 	| 3000 	|
| 13 	| B-rank STR. 	| PotentialEvent::Atk 	| 3240 	|
| 13 	| B-rank STR. 	| PotentialEvent::Defense 	| 2760 	|
| 13 	| B-rank STR. 	| PotentialEvent::Hp 	| 3000 	|
| 14 	| B-rank PHY. 	| PotentialEvent::Atk 	| 3000 	|
| 14 	| B-rank PHY. 	| PotentialEvent::Defense 	| 2760 	|
| 14 	| B-rank PHY. 	| PotentialEvent::Hp 	| 3240 	|
| 20 	| A-rank AGL. 	| PotentialEvent::Atk 	| 5000 	|
| 20 	| A-rank AGL. 	| PotentialEvent::Defense 	| 5400 	|
| 20 	| A-rank AGL. 	| PotentialEvent::Hp 	| 4600 	|
| 21 	| A-rank TEQ. 	| PotentialEvent::Atk 	| 5400 	|
| 21 	| A-rank TEQ. 	| PotentialEvent::Defense 	| 5000 	|
| 21 	| A-rank TEQ. 	| PotentialEvent::Hp 	| 4600 	|
| 22 	| A-rank INT. This serves as the base for all others. 	| PotentialEvent::Atk 	| 5000 	|
| 22 	| A-rank INT. This serves as the base for all others. 	| PotentialEvent::Defense 	| 5000 	|
| 22 	| A-rank INT. This serves as the base for all others. 	| PotentialEvent::Hp 	| 5000 	|
| 23 	| A-rank STR. 	| PotentialEvent::Atk 	| 5400 	|
| 23 	| A-rank STR. 	| PotentialEvent::Defense 	| 4600 	|
| 23 	| A-rank STR. 	| PotentialEvent::Hp 	| 5000 	|
| 24 	| A-rank PHY. 	| PotentialEvent::Atk 	| 5000 	|
| 24 	| A-rank PHY. 	| PotentialEvent::Defense 	| 4600 	|
| 24 	| A-rank PHY. 	| PotentialEvent::Hp 	| 5400 	|
| 30 	| S-rank AGL. 	| PotentialEvent::Atk 	| 7000 	|
| 30 	| S-rank AGL. 	| PotentialEvent::Defense 	| 7560 	|
| 30 	| S-rank AGL. 	| PotentialEvent::Hp 	| 6440 	|
| 31 	| S-rank TEQ. 	| PotentialEvent::Atk 	| 7560 	|
| 31 	| S-rank TEQ. 	| PotentialEvent::Defense 	| 7000 	|
| 31 	| S-rank TEQ. 	| PotentialEvent::Hp 	| 6440 	|
| 32 	| S-rank INT. 	| PotentialEvent::Atk 	| 7000 	|
| 32 	| S-rank INT. 	| PotentialEvent::Defense 	| 7000 	|
| 32 	| S-rank INT. 	| PotentialEvent::Hp 	| 7000 	|
| 33 	| S-rank STR. 	| PotentialEvent::Atk 	| 7560 	|
| 33 	| S-rank STR. 	| PotentialEvent::Defense 	| 6440 	|
| 33 	| S-rank STR. 	| PotentialEvent::Hp 	| 7000 	|
| 34 	| S-rank PHY. 	| PotentialEvent::Atk 	| 7000 	|
| 34 	| S-rank PHY. 	| PotentialEvent::Defense 	| 6440 	|
| 34 	| S-rank PHY. 	| PotentialEvent::Hp 	| 7560 	|
| 120 	| A-rank AGL. For characters with special settings. 	| PotentialEvent::Atk 	| 5000 	|
| 120 	| A-rank AGL. For characters with special settings. 	| PotentialEvent::Defense 	| 5000 	|
| 120 	| A-rank AGL. For characters with special settings. 	| PotentialEvent::Hp 	| 5000 	|
| 121 	| A-rank TEQ. For characters with special settings. 	| PotentialEvent::Atk 	| 5000 	|
| 121 	| A-rank TEQ. For characters with special settings. 	| PotentialEvent::Defense 	| 5000 	|
| 121 	| A-rank TEQ. For characters with special settings. 	| PotentialEvent::Hp 	| 5000 	|
| 122 	| A-rank INT. For characters with special settings. 	| PotentialEvent::Atk 	| 5000 	|
| 122 	| A-rank INT. For characters with special settings. 	| PotentialEvent::Defense 	| 5000 	|
| 122 	| A-rank INT. For characters with special settings. 	| PotentialEvent::Hp 	| 5000 	|
| 123 	| A-rank STR. For characters with special settings. 	| PotentialEvent::Atk 	| 5000 	|
| 123 	| A-rank STR. For characters with special settings. 	| PotentialEvent::Defense 	| 5000 	|
| 123 	| A-rank STR. For characters with special settings. 	| PotentialEvent::Hp 	| 5000 	|
| 124 	| A-rank PHY. For characters with special settings. 	| PotentialEvent::Atk 	| 5000 	|
| 124 	| A-rank PHY. For characters with special settings. 	| PotentialEvent::Defense 	| 5000 	|
| 124 	| A-rank PHY. For characters with special settings. 	| PotentialEvent::Hp 	| 5000 	|
| 201 	| Son Goku Jr only 	| PotentialEvent::Atk 	| 4000 	|
| 201 	| Son Goku Jr only 	| PotentialEvent::Defense 	| 4000 	|
| 201 	| Son Goku Jr only 	| PotentialEvent::Hp 	| 4000 	|
| 202 	| Burma (girl's term) only 	| PotentialEvent::Atk 	| 4000 	|
| 202 	| Burma (girl's term) only 	| PotentialEvent::Defense 	| 4000 	|
| 202 	| Burma (girl's term) only 	| PotentialEvent::Hp 	| 4000 	|
| 203 	| Son Gohan (childhood) only 	| PotentialEvent::Atk 	| 4000 	|
| 203 	| Son Gohan (childhood) only 	| PotentialEvent::Defense 	| 4000 	|
| 203 	| Son Gohan (childhood) only 	| PotentialEvent::Hp 	| 4000 	|
| 204 	| Verta only 	| PotentialEvent::Atk 	| 4000 	|
| 204 	| Verta only 	| PotentialEvent::Defense 	| 4000 	|
| 204 	| Verta only 	| PotentialEvent::Hp 	| 4000 	|
| 205 	| Gull only 	| PotentialEvent::Atk 	| 4000 	|
| 205 	| Gull only 	| PotentialEvent::Defense 	| 4000 	|
| 205 	| Gull only 	| PotentialEvent::Hp 	| 4000 	|
| 206 	| Guinu dedicated 	| PotentialEvent::Atk 	| 4000 	|
| 206 	| Guinu dedicated 	| PotentialEvent::Defense 	| 4000 	|
| 206 	| Guinu dedicated 	| PotentialEvent::Hp 	| 4000 	|
| 207 	| Ges dedicated 	| PotentialEvent::Atk 	| 4000 	|
| 207 	| Ges dedicated 	| PotentialEvent::Defense 	| 4000 	|
| 207 	| Ges dedicated 	| PotentialEvent::Hp 	| 4000 	|
| 208 	| Rikume only 	| PotentialEvent::Atk 	| 4000 	|
| 208 	| Rikume only 	| PotentialEvent::Defense 	| 4000 	|
| 208 	| Rikume only 	| PotentialEvent::Hp 	| 4000 	|
| 209 	| Piccolo only 	| PotentialEvent::Atk 	| 4000 	|
| 209 	| Piccolo only 	| PotentialEvent::Defense 	| 4000 	|
| 209 	| Piccolo only 	| PotentialEvent::Hp 	| 4000 	|
| 210 	| Trunks (childhood) & Son Goten (childhood) & Marlon only 	| PotentialEvent::Atk 	| 4000 	|
| 210 	| Trunks (childhood) & Son Goten (childhood) & Marlon only 	| PotentialEvent::Defense 	| 4000 	|
| 210 	| Trunks (childhood) & Son Goten (childhood) & Marlon only 	| PotentialEvent::Hp 	| 4000 	|
| 211 	| Gil only 	| PotentialEvent::Atk 	| 4000 	|
| 211 	| Gil only 	| PotentialEvent::Defense 	| 4000 	|
| 211 	| Gil only 	| PotentialEvent::Hp 	| 4000 	|
| 213 	| Son Goku (DOKKAN Battle Fighter) exclusive use 	| PotentialEvent::Atk 	| 4000 	|
| 213 	| Son Goku (DOKKAN Battle Fighter) exclusive use 	| PotentialEvent::Defense 	| 4000 	|
| 213 	| Son Goku (DOKKAN Battle Fighter) exclusive use 	| PotentialEvent::Hp 	| 4000 	|
| 214 	| Vegeta (DOKKAN Battle Fighter) only 	| PotentialEvent::Atk 	| 4000 	|
| 214 	| Vegeta (DOKKAN Battle Fighter) only 	| PotentialEvent::Defense 	| 4000 	|
| 214 	| Vegeta (DOKKAN Battle Fighter) only 	| PotentialEvent::Hp 	| 4000 	|
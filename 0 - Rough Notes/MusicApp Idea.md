2024-08-16 09:59

Status: #baby
Tags: [[applied AI]] [[multimodal]]
Description:

### Final End goal:
Website + App product
Firebase account sign-in storing personal library
Public library of smartScores that others share
To create new smartScore:
Search imslp database/use camera for sheet music
Search youtube/spotify for audio/video or upload own
Auto-detection of handling repeats/non-repeats in music
Upload smartScore to personal library
smartScore features:
- flippable sheet music pages
- switch views (double page, single page, etc.)
- can zoom into pages and pan
- interactive: tap on measure to play the audio
	- moving line/cursor whenever playing audio
	- video player too? if not just audio. 
	- toolbar at top to navigate the audio (play, pause, restart, 15 sec +/-, etc.)

### First Baby Prototype
python notebook to:
- extract pixel speed at every given moment
- extract cursor position and how it corresponds to sheet ***pages***
- reverse engineer produce-a-video code:
	- `python test_agent.py --data_set ./data/test_sample --piece Anonymous__lesgraces__lesgraces --game_config game_configs/mutopia_lchs1.yaml --agent_type optimal`
- test manually on real sheet music and real audio.

### First Website Baby
reference http://jzhi.bol.ucla.edu/ and the repo https://github.com/ayangelah/flora-fauna
- for firebase database
- for website framework
- possible to host on github?
find javascript libraries to display sheet music (any example of basic sheet music flipper? pdf viewer?)

### References

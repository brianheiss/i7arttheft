"robbery test" by Brian Heissenbuttel

Darkness is a scene.
noise_level is a real number that varies. noise_level is usually 0.  [noise level starts at 0]
Outdoors is a room. The description of the Outdoors is "You are outside the house. All the lights are out. On the second floor you can see a cracked window. You climb up to the window. asdfasdf [noise_level]." Window is a door. [Window is closed.] Window is east of Outdoors and west of Bedroom.

Instead of searching the window: [so that the player doesn't look through a wooden door]
    say "Through the window, you make out [the other side of the window]."

Instead of going east from outdoors: [to introduce the noise mechanic]
	if the window is closed:
		now noise_level is noise_level plus 100;
		say "[noise_level]";
		say "You go to open the window. As you open is it, the window frame lets out a shriek.";
		now the window is open;
		reject the player's command;
	otherwise:
		continue the action.
Bedroom is a room.
The description of bedroom is "A dark room with a bed and nightstand. Stairs in the corner lead downstairs.".
Bed is in the bedroom. Bed is a supporter.
Nightstand is in the bedroom. Nightstand is a supporter.
Living room is a room.
Kitchen is a room.
Counter is in the kitchen. Counter is a supporter.
Cabinet is in the kitchen. Cabinet is a container.
Office is a room.
Desk is in the office. Desk is a supporter.
Basement is a room.
Living room is below the bedroom.
Kitchen is west of the living room.
Office is west of the kitchen. Description of the office is "[if unvisited]You look around to see that the walls are clear! The old man moved the painting! Aw shucks![otherwise]The old office. Papers are strewn about the floor and an open dictionary is sitting on the desk."
Basement is below the kitchen.
There is a flashlight on the counter.
Spice rack is nowhere.
Dictionary is nowhere. Description of dictionary is "A regular old dictionary. There is one passage highlighted, and it reads: [line break][bold type][line break]Ottendorf Cipher [roman type](n.) – Commonly referred to as a book cipher, this code uses a source text to disclose a message. An Ottendorf Cipher consists of three numbers, corresponding to the page #-line #-letter #. Each group of three numbers corresponds to one letter in the message."
Novel is nowhere. Description of novel is "To which page do you want to turn?".
Safe is nowhere. Safe is a container. Safe is locked. Description of safe is "A metal safe that must have the painting within it. There is a 26-setting dial that accepts some password, but I suppose I could break into the safe if I found something to cut the metal bars with.".
Painting is inside safe.
Paper is nowhere. Description of paper is "An old scrap of paper with the following numbers written on it:[line break][italic type][line break]187-2-1[line break]187-1-3[line break]187-5-1[line break]187-5-6[line break]187-5-18[line break]187-2-20".
Newspaper is nowhere. Description of newspaper is "Yesterday's newspaper, with the headline
reading, [apostrophe][apostrophe]Senator Ted Cruz confesses to being the Zodiac Killer.[apostrophe][apostrophe] This fact, while undeniably true, doesn't aid you in finding the painting.".
Key is nowhere. Description of key is "A brass key, though it's uncertain what it is used for.".
Attic is a room. Attic is above the bedroom.
Chest is in the attic. Chest is a container. Chest is lockable and locked. Key unlocks chest.
Crowbar is in the chest. Description of crowbar is "A large steel crowbar. This could be useful if you have to break open the safe.".
Wine bottle is nowhere. Description of wine bottle is "Wine, yo.".

Light is a scene. Light begins when the player has the flashlight.
When Light begins:
	say "You flick on the flashlight and can now see your way around the house. You can finally inspect the objects within the house. I remember the old man keeping his painting in his office.";
	now the description of the bedroom is "The owner's bedroom. You see a ladder in the corner leading to the attic.";	
	Now the spice rack is inside the cabinet;
	Now the dictionary is on the desk;
	Now the novel is on the nightstand;
	Now the safe is in the basement;
	Now the newspaper is in the living room;
	Now the wine bottle is in the kitchen.
	
Instead of taking spice rack:
	say "Moving the spices triggers a small compartment in the cabinet to open. There is a small piece of paper on the inside of the cabinet.";
	now the paper is in the cabinet.
	
Instead of taking dictionary:
	say "This object seems too heavy to carry around. It may have something interesting on its pages.".

Instead of opening safe:
	If the safe is locked:
		say "There is a 6-character passcode needed to open this safe. All the letters are capital";
		now the command prompt is "Enter passcode: ";
	otherwise:
		continue the action.
		
After reading a command when the command prompt is "Enter passcode: ":
	if the player's command matches "GATSBY":
		say "The safe creaks open, revealing the painting inside.";
		Now the safe is unlocked;
		Now the safe is open;
		now the command prompt is ">";
		reject the player's command;
	otherwise:
		say "The safe does not budge.";
		now the command prompt is ">";
		reject the player's command.
		
After examining novel:
	now the command prompt is "Page number ";

After reading a command when the command prompt is "Page number ":
	now the command prompt is ">";
	if the player's command matches "187":
		say "The story [italic type]George Walker at Suez[roman type] begins on this page. The
		text reads:[line break][line break]
		Of all the spots on the world that I,[line break]
		George Walker of Friday street, London, [line break]
		have ever visited, Suez, in Egypt, at the [line break]
		head of the Red Sea, is by far the vilest, [line break]
		the most unpleasant, and the least [line break] interesting.";
		reject the player's command;
	otherwise:
		say "There is nothing of interest on this page";
		reject the player's command.
		
After taking newspaper:
	say "Underneath the newspaper is a small brass key.";
	now the key is in the living room.

After reading a command when the player is in the basement:	
	If the player's command matches "break open safe":
		if the player has the crowbar:
			say "You wedge the crowbar against the metal bars that are keeping the safe locked. Pulling hard, the bars slowly surrender while letting lose a loud creaking noise. After enough time, the bars break free, making the safe nothing more than an expensive door.";
			Now the safe is unlocked;
			reject the player's command;
		otherwise:
			say "You can't do this with what you have right now.";
			reject the player's command.

Instead of taking wine bottle:
	say "The wine bottle slips out of your hands, shattering on the floor. The sound resonates through the empty kitchen.";
	now the wine bottle is nowhere.

Win is a scene. Win begins when the player has the painting.
When Win begins:
	say "You got the valuable painting and escaped without being noticed. Congratulations, you now own a valuable piece of art that will sell for millions of dollars.[line break][line break]Game Over: You have won!".
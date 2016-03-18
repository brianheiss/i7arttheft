"robbery test" by Brian Heissenbuttel

Darkness is a scene.

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
Office is west of the kitchen.
Basement is below the kitchen.
There is a flashlight on the counter.
Spice rack is nowhere.
Dictionary is nowhere. Description of dictionary is "A regular old dictionary. There is one passage highlighted, and it reads:
Ottendorf Cipher (n.) Commonly referred to as a book cipher, this code uses a source text to disclose a message. An Ottendorf Cipher consists of three numbers, corresponding to the page #-line #-letter #. Each group of three numbers corresponds to one letter in the message."
Novel is nowhere. Description of novel is "To which page do you want to turn?".
Safe is nowhere. Safe is a container. Safe is locked. Description of safe is "A metal safe that must have the painting within it. There is a 26-setting dial that accepts some password, but I suppose I could break into the safe if I found something to cut the metal bars with.".
Painting is inside safe.
Paper is nowhere. Description of paper is "An old scrap of paper with the following numbers written on it:[line break][italic type][line break]187-2-1[line break]187-1-3[line break]187-5-1[line break]187-5-6[line break]187-5-18[line break]187-2-20".

Light is a scene. Light begins when the player has the flashlight.
When Light begins:
	say "You flick on the flashlight and can now see your way around the house. You can finally inspect the objects within the house. I remember the old man keeping his painting in his office.";
	now the description of the bedroom is "The owner's bedroom. You see a ladder in the corner leading to the attic.";
	Now the spice rack is inside the cabinet;
	Now the dictionary is on the desk;
	Now the novel is on the nightstand;
	Now the safe is in the basement.
	
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
		say "The safe creaks open.";
		Now the safe is unlocked;
		now the command prompt is ">";
	otherwise:
		say "The safe does not budge.";
		now the command prompt is ">";
		
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
	otherwise:
		say "There is nothing of interest on this page".
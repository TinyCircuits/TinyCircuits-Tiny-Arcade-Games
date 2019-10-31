
   TinyQuix for the PocketArcade

      version 1.1 dated 12/28/2018 @1900
      written by Mark J Culross, KD5RXT (kd5rxt@arrl.net)

   The source & binaries (suitable for SD card loading) for TinyQuix is available in its own folder on my
      Google Drive (in the same place as for TinySimon & TinySNAKE):
         https://drive.google.com/open?id=1Pv0LDGhe3uLNJvhF7-aSdTOSZMYe8hbx

   Using the TinyScreen+ display to allow a player to play a loose implementation of the traditional Qix game

   Uses the TinyCircuits libraries for its display output & digital joystick input

   Configure/build to run in the PocketArcade Menu System as follows:
      Tools : Board : "Tiny Arcade"
      Tools : Build Options : "Binary for SD Card"
      Sketch : Export compiled Binary
      [ rename the binary to "Tiny Quix.bin" & place in "Tiny Quix" folder ]

   Configure/build to run standalone on the PocketArcade as follows:
      Tools : Board : "Tiny Arcade"
      Tools : Build Options : "Default"
      Sketch : Upload (after setting Tools/Port as appropriate)

   TODO:
      - limit the length of the quix

   Controls:
      - pressing the d-pad up/down at either the splash screen or any of the info screens shows more info screens
      - pressing the d-pad left/right at either the splash screen or any of the info screens adjusts the brightness
      - pressing the left button at the splash screen starts the game in player mode
      - allowing the 10-second timer on the splash screen to expire starts the demo mode
      - pressing the right button either while on the splash screen or any of the info screens or when in demo mode
        enters/exits the "debug" screen
         - pressing the up & down d-pad keys moves between debug controls
         - pressing the left & right d-pad keys while changing the number of lives causes changes by one
         - pressing the left button while changing the number of lives (with the d-pad) causes changes by ten
         - pressing the left button for any other debug control toggles that control on/off
      - the d-pad keys are used to move in player mode (player stops when no d-pad keys are pressed)

   Comparison to the original Qix game (purists take heed):

   Original Qix implementation:

      1) the Qix is multiple lines
      2) as the game progresses, the number of qix increases
      3) as the game progresses, the number of sparx increases
      4) as the game progresses, supersparx (which can kill the player) move around in the unfilled space
      5) the player & the sparx can only travel on borders that touch at least one empty space
      6) scoring is based upon the increase in the amount of space filled by the newly enclosed area(s)
      7) scoring includes a 1000 point bonus for each percent of filled space > 75%
      8) the player can move fast or slow, & space filled while moving slow scores higher points
      9) pressing a button while moving causes the player to move "slow"
     10) when moving, stix (temp lines) must have at least one space between them (to allow "filled" space)
     11) there is an initial animation when placing the player on the border

   TinyQuix implementation:

      1) the TinyQuix is always only a single line
      2) as the game progresses, there is always only a single TinyQuix
      3) as the game progresses, the number of sparx is always two
      4) there are no supersparx
      5) the player can freeze a sparx by closing a rectangle which leaves it no valid moves; also,
         the player can freeze itself by closing a rectangle whish leaves it no valid moves; in that
         case, the rectangle is closed/filled, but the player dies !!
      6) scoring is based upon the total amount of space filled each time new space is enclosed
      7) scoring includes a bonus for each percent of filled space > 75%
      8) the player can only move fast
      9) the buttons are only used to start the game (left button) & to enter/exit "debug" (right button)
     10) when moving, stix (temp lines) can be adjacent; this space will only be closed when another valid
         rectangle (with space to be filled) is closed; as long as the adjacent stix have not been
         closed, they remain vulnerable to collision by the TinyQuix, which kills the player
     11) there is only an animation when the player is killed


   NOTES:
      - the player's move generator in demo mode is very dumb, since it employs absolutely no offensive
        or defensive logic of any kind - it is purely semi-random !!
      - a score exceeding 100000 is signified with a red "+" displayed next to the word "Score"


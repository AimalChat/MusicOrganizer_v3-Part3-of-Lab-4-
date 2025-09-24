Project: music-organizer-v3. A project to collect audio files.
Authors: David J. Barnes and Michael Kölling

This project is part of the material for the book

   Objects First with Java - A Practical Introduction using BlueJ
   Seventh edition
   David J. Barnes and Michael Kölling

It is discussed in chapter 4.

To start:

Create a MusicOrganizer object on the object bench.
Use its methods to add, remove, and play files. The listAllFiles
method prints a list of the collection.

Lab report (part a = question, part b = answer)

21a.Create a MusicOrganizer and store a few file names in it. Use the listAllFiles 
method to print them out; check that the method works as it should.

21b.It does work as intended.

22a.Create an ArrayList<String> in the Code Pad by typing the following two lines:
import java.util.ArrayList;
new ArrayList<String>()
If you write the last line without a trailing semicolon, you will see the small red 
object icon. Drag this icon onto the object bench. Examine its methods and try 
calling some (such as add, remove, size, isEmpty). Also try calling the same methods 
from the Code Pad. You can access objects on the object bench from the Code Pad by 
using their names. For example, if you have an ArrayList named al1 on the object bench, 
in the Code Pad you can type: al1.size()

22b.Done.

23a.If you wish, you could use the debugger to help you understand how the statements 
in the body of the loop in listAllFiles are repeated. Set a breakpoint just before the 
loop, and step through the method until the loop has processed all elements and exits.

23b.They're(The tracks) set as local variables, which makes sense since I added them 
into the list from this object.

24a.Challenge exercise The for-each loop does not use an explicit integer variable to 
access successive elements of the list. Thus, if we want to include the index of each 
filename in the listing, then we would have to declare our own local integer variable 
(position, say) so that we can write in the body of the loop something like:
System.out.println(position + ": " + filename);
Write another version of listAllFiles, called listWithIndex that lists the file names 
with associated index. 
For instance:
0: Burning man.mp3
1: Livid.mp3
2: Maverick.mp3 
The easiest way to start this method is to copy your listAllFiles method within 
MusicOrganizer and then rename it to listWithIndex. Hint: You will need a local 
variable declaration of position in the method, as well as a statement that updates the
variable's value by one inside the for-each loop.

24b.
   /**
* Show a list of all the files in the collection.
*/
public void listWithIndex()
{
   int position = 0;
   for(String filename : files) {
      System.out.println(position +": "+ filename);
      position ++;
   }
}

25a.Add the listMatching method in Code 4.4 to your version of the project. (Use music-
organizer-v3 if you do not already have your own version.) Check that the method only 
lists matching files. Also try it with a search string that matches none of the file 
names. Is anything at all printed in this case?

25b.It does show files that contain the inputted String when it is included in the name
of the filename. It shows nothing when there are no matches.

26a.Challenge exercise In listMatching, can you find a way to print a message, once the 
for-each loop has finished, if no file names matched the search string? Hint: Use a 
boolean local variable.

26b.
    /**
     * List the names of files matching the given search string.
     * @param searchString The string to match.
     */
    public void listMatching(String searchString)
    {
        boolean found;
        found = false;
        for(String filename : files){
            if(filename.contains(searchString)){
                //A match.
                found = true;
                System.out.println(filename);
            }else{
                //Unable to find a match.
                System.out.print("");
            }
        }
        if(found == false){
                System.out.print("No matching files.");
            }
    }

27a.Write a method in your version of the project that plays samples of all the tracks 
by a particular artist, one after the other. The listMatching method illustrates the 
basic structure you need for this method. Make sure that you choose an artist with more 
than one file. Use the playSample method of the MusicPlayer (provided in music-organizer-
v3). The playsample method plays the beginning of a track (about 15 seconds) and then 
returns.

27b.
    public void playAllSamples(String searchString){
        MusicPlayer player = new MusicPlayer();
        boolean found;
        found = false;
        for(String filename : files){
            if(filename.contains(searchString)){
                //A match.
                found = true;
                System.out.println(filename);
                player.playSample(filename);
            }else{
                //Unable to find a match.
                System.out.print("");
            }
        }
        if(found == false){
                System.out.print("No matching files.");
            }

28a.Write out the header of a for-each loop intended to process an ArrayList<Track> 
called trackList. Don’t worry about the loop’s body. Remember to declare the loop 
variable to be of the appropriate type.

28b. for(Track track : trackList)

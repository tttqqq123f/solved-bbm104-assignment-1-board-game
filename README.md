Download Link: https://assignmentchef.com/product/solved-bbm104-assignment-1-board-game
<br>
In this experiment, you are expected to implement a game which is runned with commands from an input file. This game is based on a fantastic adventure board game and runs on a given multi-dimensional array. There will be two sides (monsters, heroes) and they will attack to each other. After given commands are executed, your program should print related outputs into a text file such as current situation of the map and status of the characters. Details are explained below.

BACKGROUND INFORMATION

<strong> </strong>

Adventure board games involve fantastical elements like heroes which explore the given map and the monsters they encounter during this exploration. Both heroes and monsters have different properties such as special attacks, health and they fight with each other accordingly. In general, game is finished after given quest is accomplished.




Monsters are placed on some specified points and heroes can attack them if they adjacent to their square. This combat takes place in an order like first all monsters attack to their adjacent heroes in their spawn order and then all heroes attack to their adjacent monsters in their spawn order vice versa. Therefore, if there is more than one monster adjacent to a hero, the first spawned monster will attack first and so on. Similarly, heroes attack in their spawn order to an adjacent monster.




Health is usually measured in hit points or health points, shortened to “HP”. When the HP of a character reaches zero, it become incapacitated or die. Each hero and monster have different attack powers and they give damage each other according to these attack powers.

Consequently, monster’s or hero’s HP is decreased according to attack’s “damage” value. If a hero kills a monster, that hero gains one experience point, shortened to “XP”.




<strong>EXPERIMENT </strong>

<strong> </strong>

<h1>1)      Loading Characters</h1>

<strong> </strong>

You will read 2 input files in order to start the game. First one is named

“chars_&lt;input_number&gt;.txt” and it includes properties of heroes and monsters such as “name”, “HP” and “damage value” in the given order, separated by comma. In each line there will be a character in the format of &lt;TYPE&gt;,&lt;NAME&gt;,&lt;HP&gt;,&lt;DAMAGE&gt;:




HERO,DRIZZT,8,3

MONSTER,MINDFLAYER,10,2

HERO,CATTIE,6,3

MONSTER,TROLL,4,3

MONSTER,GOBLIN,1,3




There can be any number of heroes and monsters. The order of attacking can be determined according to the order of spawn of the characters. Therefore, while your program is reading lines of this file, in each line a character will be spawn. For instance, in the given example above, when its heroes turn and they are going to attack,  the order of attacking will be like this: “1.DRIZZT, 2.CATTIE”. Moreover, for the monsters it will be like this:

“1.MINDFLAYER, 2.TROLL, 3.GOBLIN”.




<h1>2)      Playing the Game</h1>

<strong> </strong>

The second input file, which is named as “commands_&lt;input_number&gt;.txt”, includes the commands in order to play a scenario. The following commands will be fixed at the start of each file. Because, we need to load the map to start the game and we should put characters in specified places. Therefore, there is no need to print error messages for this part.




LOADMAP 5 5

PUT HERO DRIZZT 0 0 CATTIE 4 1

PUT MONSTER TROLL 1 1 GOBLIN 4 0 MINDFLAYER 0 3




All the other commands can be given in any order. Each line will contain only one command and there will not be an empty line anywhere in the file. The format of the commands and the error messages that you should give will be explained below in detail. All commands and command parameters will be separated by a one space.




<ul>

 <li><strong><u>LOADMAP:</u></strong> Loads a map with the given row and column sizes. These size values will be<u>​ </u> integers and can be any number. This map is basically a 2 dimensional array and should be created dynamically according to given row and column sizes.</li>

</ul>




<u>Input</u>

LOADMAP &lt;row_size&gt; &lt;column_size&gt;




<u>Output</u>

There will not be any messages for this command.




<h2>Error</h2>

There will be no incorrect entry for this command.




<ul>

 <li><strong> <u>PUT:</u></strong> Puts the given characters on to the map. &lt;type&gt; will be only “HERO” or​ “MONSTER”. Characters can be given in any order for this command.</li>

</ul>




<h2>Input</h2>

PUT &lt;type&gt; &lt;hero1_name&gt; &lt;row_no&gt; &lt;column_no&gt; &lt;hero2_name&gt; &lt;row_no&gt;

&lt;column_no&gt; &lt;hero3_name&gt; &lt;row_no&gt; &lt;column_no&gt; …

PUT &lt;type&gt; &lt;monster1_name&gt; &lt;row_no&gt; &lt;column_no&gt; &lt;monster2_name&gt; &lt;row_no&gt; &lt;column_no&gt; &lt;monster3_name&gt; &lt;row_no&gt; &lt;column_no&gt; …




<u>Output</u>

There will not be any messages for this command.




<h2>Error</h2>

There will be no incorrect entry for this command.




<ul>

 <li><strong> <u>SHOW (20 points):</u></strong> Prints the current situation of the heroes, monsters or the map.​ &lt;type&gt; will be only “HERO”, “MONSTER” or “MAP”. Characters should be printed in the spawn order. While printing the map, you should use the first letter of the character names and put ‘.’ for empty squares.</li>

</ul>




<u>Input</u>

SHOW &lt;type&gt;




<h2>Output</h2>

&lt;type&gt; STATUS

&lt;char1_name&gt; HP: &lt;char1_hp&gt; XP: &lt;char1_XP&gt;

&lt;char2_name&gt; HP: &lt;char2_hp&gt; XP: &lt;char2_XP&gt;




<em>Note: “XP” should not be printed for MONSTER type. </em>




MAP STATUS







<h2>Error</h2>

There will be no incorrect entry for this command.




<ul>

 <li><strong> <u>ATTACK (25 points):</u></strong> Executes the attack command for the given &lt;type&gt;. After this<u>​ </u> command is executed, the characters for the given &lt;type&gt; should attack the others and a combat will start. There are some rules you should consider:</li>

</ul>




○ First, characters can only attack adjacent enemies in the spawn order. For instance, for the ATTACK MONSTER command, all monsters start to attack in the order of: 1.MINDFLAYER, 2.TROLL, 3.GOBLIN.

○ Characters can attack any adjacent square and there are 8 directions in total. In addition, this directions have some attack priorities as shown below. Therefore, if there are more than one enemies adjacent to a hero or monster (red dot in the middle), it should attack the enemy in square 1 first, then square 2, square 3 and so on.










For the example above, if the command is ATTACK HERO, Drizzt will attack monsters before Cattie, and Drizzt will attack Mindflayer first and then Troll. This rule valid for the below conditions as well:







○ Same type of characters can not attack each other.

○ In order to simulate the combat, you should decrease the HP of damaged character in the amount of damage value of the character which is attacking. So, for the example above, after a monster attack, Drizzt will have HP=3 (8-2-3) and Catie will have HP=3 (6-3).

○ A character’s HP can not be smaller than “0”. If a character reaches HP=0, it can not attack or can not be attacked and should be removed from the map. However, the status of this character should be printed after each SHOW &lt;type&gt; command.

○ If a hero kills a monster, it’s XP should be increased 1 point. If a monster kills a hero, do nothing.




<u>Input</u>

ATTACK &lt;type&gt;




<u>Output</u>

&lt;type&gt;S ATTACKED




<h2>Error</h2>

There will be no incorrect entry for this command.




<ul>

 <li><strong> <u>MOVE (20 points):</u></strong> This command will be only for heroes and inputs will be given only<u>​ </u> for hero type, there is no need to check for type. However, you should check if given hero’s new position is out of the map or occupied by another character. Also, a dead hero can not be moved. Therefore, you should give error messages for these type of inputs. A hero will always move one unit and inputs will be given for one unit move. Heroes can be given in any order for this command.</li>

</ul>




<h2>Input</h2>

MOVE HERO &lt;hero1_name&gt; &lt;row_no&gt; &lt;column_no&gt; &lt;hero2_name&gt; &lt;row_no&gt; &lt;column_no&gt; &lt;hero3_name&gt; &lt;row_no&gt; &lt;column_no&gt; …




<u>Output</u>

HEROES MOVED




<h2>Error</h2>

<ul>

 <li>If a hero or a monster is in the next position of a given hero, give this message:</li>

</ul>




&lt;hero_name&gt; can’t move. Place is occupied.




<ul>

 <li>If hero’s next position is exceeds map boundaries, give this message:</li>

</ul>




&lt;hero_name&gt; can’t move. There is a wall.




<ul>

 <li>If hero is dead, give this message:</li>

</ul>




&lt;hero_name&gt; can’t move. Dead.




<h1>3)      Finishing the Game</h1>




After each ATTACK command is executed, you should check if all the heroes or all the monsters are dead. If one of these cases is true, print a message and terminate the program even there are more commands in the commands file. Message is:




ALL &lt;type&gt;S ARE DEAD!




Other than that, the game may not be finished according to given scenario from the input file (all monsters or heroes can be alive). In this case, just execute the commands and write the outputs accordingly.




<h1>RULES</h1>

<strong> </strong>

<ul>

 <li>You should use <u>dynamic arrays</u>​ and ​ <u>structs</u>​    in order to save given characters and their<u>​  </u> Other methods will not be accepted.</li>

 <li>The game map should be created as 2D dynamic array. Other methods will not be accepted.</li>

 <li>Follow <u>C coding standards</u>​ and pay attention to code readability. Use comments. <u>​       </u><strong>(5</strong>​<strong> points) </strong></li>

 <li>You should comply with given output formats in order to get points from evaluation. <strong>Note that it is not possible to get sufficient points without implementing the scenarios properly. </strong></li>

</ul>

<h1>INPUT &amp; OUTPUT</h1>

<strong> </strong>

The paths of the input and output files will be provided as command line arguments in the order of “chars_&lt;input_number&gt;.txt commands_&lt;input_number&gt;.txt”. You will be able to find example input and output files on Piazza. You can also create your own inputs. Remember that except the mentioned commands, all commands can be in any order and in any amount.

Output file name should be in the format of “output_&lt;input_number&gt;.txt”




<strong> </strong>

<h1>REPORT</h1>




<ul>

 <li>In the report, you are expected to determine and explain the <u>​problem</u>​: What is the main goal of the assignment and what points need to be understood. ​<strong>(5 points) </strong></li>

 <li>Then, give your <u>​solution</u>​ in detail: How do you approach this problem and how do you implement it, what do you use. ​<strong>(5 points) </strong></li>

 <li>Explain your <u>​data structure​</u>: What structures do you use to store characters or the map etc. (dynamic arrays, structs) ​<strong>(5 points) </strong></li>

 <li>Explain your <u>​code</u>​. For example, the purpose of the <u>​functions​</u>, but do not copy your code, just mention important parts. ​<strong>(5 points) </strong></li>

 <li>Give your detailed ​<u>algorithm​</u> step by step. ​<strong>(5 points) </strong></li>

</ul>




<strong> </strong>

<h1>NOTES</h1>




<ul>

 <li>Your experiments will be executed in DEV machine, please make it work on dev before submitting. Otherwise your submission will not be evaluated. Any library does not exist in DEV is forbidden. Compile your code with “-ansi” option.</li>

 <li>Do not forget to free allocated memory and check memory leaks by using “valgrind” on DEV machine.</li>

 <li>Input and output file names will not be fixed, so you should not hardcode them into your program.</li>

 <li>Save all your work until the assignment is graded.</li>

 <li>You can ask your questions about the experiment by sending your messages to Piazza Group. Any other method will not be accepted.</li>

 <li>Also, you are responsible to read discussions about the assignment on Piazza.</li>

</ul>













<ul>

 <li>You have to <u>submit</u>​ your experiment files in the given directory structure below:​         &lt;student id&gt;</li>

</ul>

&lt;src&gt;

*.c

*.h

&lt;report&gt; report.pdf

<ul>

 <li>You have three days for late submission. You will lose 10 points from maximum evaluation score for each day (your submitted study will be evaluated over 90, 80 and 70 for each late submission day). You have to submit your solution in deadline date + three days, otherwise it will not be evaluated.</li>

</ul>



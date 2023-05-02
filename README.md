Download Link: https://assignmentchef.com/product/solved-co2220-graphical-object-oriented-and-internet-programming-in-java-coursework-assignment-2
<br>
<h1><a name="_Toc17202"></a>Introduction</h1>

This is coursework assignment 2 (of two coursework assignments total) for 2018–19. Part A looks at a more sophisticated GUI than the one seen in coursework assignment 1, as well as: saving our data using text files and by serializing objects; static utility methods and classes; parsing text files to objects; overriding Object’s <em>equals()</em> method; and the Comparator interface. Part B asks that you demonstrate an understanding of simple network programming, Exceptions, <em>toString()</em> methods and String formatting.




<strong>IMPORTANT NOTE:</strong> Please use at least <strong>Java 8</strong> to compile and test your programs. Later versions of Java are also fine.

<strong> </strong>

<h1><a name="_Toc17203"></a>Electronic files you should have</h1>

<h2><a name="_Toc17204"></a>Part A</h2>

<em>Java files </em>

<ul>

 <li><em>java </em></li>

 <li><em>java </em></li>

 <li><em>java </em></li>

 <li><em>java </em></li>

 <li><em>java </em></li>

 <li><em>java </em></li>

 <li><em>java </em></li>

 <li><em>java </em></li>

 <li><em>java </em></li>

</ul>

<em> </em>

<em>Text files </em>

<ul>

 <li><em>2017-18 Premier League Results.txt </em></li>

 <li><em>2017-18 Premier League Results partial-1.txt </em></li>

 <li><em>2017-18 Premier League Results partial-2.txt </em></li>

</ul>

<em> </em>

<em>Serialized files </em>

<ul>

 <li><em>2017-18 Premier League Results.ser </em></li>

 <li><em>2017-18 Premier League Results partial-1.ser </em></li>

 <li><em>2017-18 Premier League Results partial-2.ser </em></li>

</ul>

<em> </em>

<h2><a name="_Toc17205"></a>Part B</h2>

<ul>

 <li><em>java</em></li>

 <li><em>java</em></li>

 <li><em>2017-18-PLResults.ser</em></li>

</ul>




<h1><a name="_Toc17206"></a>Reading</h1>

Please note that the reading given for part A and part B is carefully chosen to reflect the tasks you are asked to achieve. Every year students miss marks for their submissions that they very likely would have gained had they paid attention to the recommended reading.

<h1><a name="_Toc17207"></a>What you should hand in: very important</h1>

At the end of each section there is a list of files to be handed in – <strong>please note the hand-in requirements supersede the generic University of London instructions</strong>. Please make sure that you give in <strong>electronic versions</strong> of your Java files since you cannot gain any marks without handing in the .<strong>java</strong> files asked for. Class files are <strong>not</strong> needed, and any student giving in only a class file will not receive any marks for that part of the coursework assignment, <strong>so please be careful about what you upload as you could fail if you submit incorrectly</strong>.




<ul>

 <li>Please only hand in the Java files asked for, and not any additional files.</li>

 <li>Please put your name and student number as a comment at the top of each Java file that you hand in.</li>

</ul>




There is one mark allocated for handing in uncompressed files – that is, students who hand in zipped or .tar files or any other form of compressed files can only score 99/100 marks.




There is one mark allocated for handing in just the Java files asked for without putting them in a directory; students who upload their files in a directories can only achieve 99/100 marks.




There are two marks for (1) not changing the names of the classes given to you, and (2) for naming any classes that you have to write (in this assignment <em>MatchResultsClient.java</em>) <strong><em>exactly</em></strong> as you have been asked to name them.




Anything added to the names given means that your files are incorrectly named, for example the following count as wrong names:




<ul>

 <li><em>JSmith_ MatchResultsClient.java </em></li>

 <li><em>cwk2- MatchResultsClient.java </em></li>

 <li><em>JSmith-220-assignment2- MatchResultsClient.java </em></li>

 <li><em>MatchResultsClient .java (note space before .java) </em></li>

</ul>




Using a file name that differs from the class name leads to a compilation error caused by a file name / class name mismatch.




<strong>The examiners will compile and run your Java programs. For this reason, programs that will not compile will not receive any marks. </strong>

<strong> </strong>

You are asked to give your classes certain names, please follow these instructions carefully. If your file does not compile <strong><em>for any reason</em></strong> (except file name / class name mismatch) you will receive no marks for that part of the assignment. In particular, files that contain Java classes that cannot be compiled because they are the wrong type (<em>e.g.</em> PDFs) will not be given any marks.

<h1><a name="_Toc17208"></a>Part A</h1>

The <em>LeagueTableCreatorGui</em> class constructs a football league table and displays the result on the JTextArea of the GUI. The league can be constructed from text files or serialized files. Serialized files must contain an ArrayList of <em>DatedMatchResult</em> objects, and text files must be laid out in a particular way for successful parsing to a <em>DatedMatchResult</em> object. The files you have been given will construct the English Premier League table for 2017-18; naturally other league tables are possible with different data.




The <em>2017-18 Premier League Results.txt </em>file has all the games played in the 2017-18 season, and the serialized file, <em>2017-18 Premier League Results.ser, </em>contains all the 2017-18 results as an ArrayList of <em>DatedMatchResult</em> objects.




The GUI also has a JScrollPane displaying a clickable list of dates. Clicking on a date gives the partial league results up to and including that date. This could allow a user, for example, to trace their team’s progress throughout the football season.




League tables can be constructed either in one go, or by adding in extra results to a partial league table. In the second case the GUI’s <em>addNewResults(List&lt;DatedMatchResult&gt;)</em> method is used to make sure that the same match result is not added twice.




<h2><a name="_Toc17209"></a>Overriding Object’s equals() method</h2>

Note every Java class inherits from Object, hence they inherit its public methods, one of which is the <em>equals()</em> method. The API notes that “this method returns true if and only if [both objects] refer to the same object” – see:

<u><a href="https://docs.oracle.com/javase/7/docs/api/java/lang/Object.html">https://docs.oracle.com/javase/7/docs/api/java/lang/Object.html</a></u>




This means that the method returns true only if two objects are pointing to the same place in memory. Hence, two objects may be in the same state (<em>i.e</em>. their instance variables hold or point to the same values), but if they are held in different places in memory they are not the same.




However, you can use equals to compare Strings, and to compare LocalDates to see if their fields are pointing at or holding the same data, because both classes override <em>equals().</em>  – see <u><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">https://stackoverflow.com/questions/2265503/why</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">do</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">i</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">need</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">to</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">override</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">the</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">equals</a></u><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java</a><u><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">and</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">hashcode</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">methods</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">in</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">java</a></u> for more information.




<h2><a name="_Toc17210"></a>The JFileChooser class</h2>

The <em>LeagueTableCreatorGui</em> class uses the Swing class JFileChooser for selecting files to open and to save to. The class is itself a GUI used for navigating the local file system. More information can be found at the following links:




<ul>

 <li><u><a href="https://docs.oracle.com/javase/7/docs/api/javax/swing/JFileChooser.html">https://docs.oracle.com/javase/7/docs/api/javax/swing/JFileChooser.html</a></u></li>

 <li><u><a href="https://docs.oracle.com/javase/tutorial/uiswing/components/filechooser.html">https://docs.oracle.com/javase/tutorial/uiswing/components/filechooser.html</a></u></li>

</ul>




<h2><a name="_Toc17211"></a>Why you should use at least Java 8 to compile and test your work</h2>

The classes you have been given for this assignment use the diamond operator, the Files and LocalDate classes that are not available in earlier versions of Java.




<h2><a name="_Toc17212"></a>The diamond operator (from Java 7)</h2>

Some of the classes you have been given for part A use <strong>the diamond operator</strong>, meaning that the type of an ArrayList can be inferred by the JVM. For example this declaration in the <em>buildDateList()</em> method of the <em>LeagueTableCreatorGui</em> class:




List&lt;LocalDate&gt; dates = new ArrayList&lt;&gt;();




From the left side of the declaration, the JVM infers that the ArrayList is of type

LocalDate.




<h2><a name="_Toc17213"></a>The Files class (from Java 7 and 8)</h2>

Files, introduced in Java 7, is a class with static methods that operate on files and related data structures, it includes the method <strong><em>readAllLines(Path, Charset)</em></strong><em>. </em>This method reads all lines from a file, recognises standard line endings, and closes the file after use.




The <em>parse(File</em>) method in the <em>DatedMatchResultParser</em> class uses the Java 8 Files method <strong><em>Files.readAllLines(Path)</em></strong> that takes only a Path parameter. Bytes from the file are decoded into characters using the UTF-8 Charset.




For more information on the Files class, see the API: <u><a href="https://docs.oracle.com/javase/8/docs/api/java/nio/file/Files.html">https://docs.oracle.com/javase/8/docs/api/java/nio/file/Files.html</a></u>




<h2><a name="_Toc17214"></a>The LocalDate class (from Java 8)</h2>

We are using the LocalDate class in preference to the Calendar or Date classes. LocalDate is simpler to use than the Calendar class. Note also that some of the constructors and methods of the Date class are now deprecated.




The LocalDate class overrides <em>equals()</em> from the Object class, so that comparing two LocalDate variables with <em>equals()</em> gives the result we expect – they are equal if they both point at the same date; dates do not have to be in the same place in memory. LocalDate is a final class so it cannot be extended, and has both instance and static methods. Static methods include <em>now(),</em> for example:




LocalDate date = LocalDate.now();




will give a new LocalDate object initialised with today’s date.




LocalDate has a <em>toString()</em> method so its output can be formatted as a String.







<h2><a name="_Toc17215"></a>The LeagueTableCreatorGui class</h2>

Compile and run the <em>LeagueTableCreatorGui</em> class. Choose one of the buttons under the label Create New League Table. If you choose the Parse Match Results button and then the <em>2017-18 Premier League Results.txt </em>file you will see that the GUI displays nothing on the JTextArea, as in the screenshot below.













If you click the Deserialize Match Results button and choose the serialized file, <em>201718 Premier League Results.ser</em>, then you will see that the GUI displays the final rankings of the English Premier League for the 2017-18 football season, as in the screenshot below.










<h2><a name="_Toc17216"></a>The questions</h2>

Please complete the following tasks:




<ol>

 <li>When you compile and run the GUI, and choose the Parse Match Results button and then the <em>2017-18 Premier League Results.txt </em>you will find that the JTextArea is empty. This is because the <em>DatedMatchResultParser</em> class is not parsing the results given to it to a <em>DatedMatchResult </em>objects successfully. You will also see the shell displaying information about a NullPointerException that has been thrown by the <em>updatePlayedStats(DatedMatchResult)</em> method in the <em>LeagueTableCreator</em> NullPointerException is an unchecked sub-class of Exception and hence it has not been handled with try/catch. The exception will not be thrown once the<em> parseLine(String, LocalDate)</em> method works as it should.</li>

</ol>




The following methods called by the <em>parseLine(String, LocalDate)</em> method in the <em>DatedMatchResultParser</em> class return dummy values in order that the GUI will compile. Complete the methods so that the <em>parseLine(String, LocalDate)</em> method works as it should to parse its String and LocalDate parameters to a new <em>DatedMatchResult </em>object.




<ul>

 <li><em>parseHomeTeam(String[ ]) </em></li>

 <li><em>parseHomeScore(String[ ]) </em></li>

 <li><em>parseAwayTeam(String[ ]) </em></li>

 <li><em>parseAwayScore(String[ ])</em> <strong>[12 marks] </strong></li>

</ul>

<ol start="2">

 <li>If the user clicks on the Serialize Match Result button, the GUI takes no action. What should happen when the button is pressed is that the JFileChooser asks the user for a file name to serialize</li>

</ol>

to, then a serialization method in the <em>SerializationUtil</em> class is called, and the ArrayList <em>matchResults</em> containing <em>DatedMatchResults</em> objects will be serialized into the file named by the user.




<ul>

 <li>Write the serialized method in the <em>SerializationUtil </em></li>

 <li>Write the inner class <em>SerializeButtonAction </em>and remove the comment marks from the statement given below to test your work.</li>

 <li>Write an appropriate constructor for the <em>SerializationUtil </em></li>

</ul>




The statement:

serializeButton.addActionListener(new

SerializeButtonAction());

has been commented out. You will need to remove the comment

marks from the statement to test your work.                                               <strong>[18 marks] </strong>

<ol start="3">

 <li>When you press the <sub>Save League Table As Text File </sub>button,</li>

</ol>

the JFileChooser asks for a file name to save to, however no file is made and nothing is saved.




The <em>saveLeagueTable(File)</em> method of the <em>LeagueTableCreatorGui </em>class uses the <em>getText()</em> method from the JTextArea class to take the contents of the JTextArea, which includes line breaks, as a String and send it to the <em>write(String, File) </em>method of the

<em>LeagueTableFileWriter </em>class. The <em>write(String, File) </em>method’s body is empty, hence no file is made and nothing is saved. Complete the method, being sure to save the text to a file with the UTF-8 charset.




Note that the <em>getText()</em> method is inherited by the JTextArea class

from JTextComponent. See the API for more details.                             <strong>[6 marks] </strong>

<ol start="4">

 <li>In order to be able to add new results to the league, while excluding any duplicate results, we need to override <em>equals()</em> in the <em>DatedMatchResult</em> class so that the comparison works when two <em>DatedMatchResult</em> objects are compared that are in different places in memory. With the system as it is given to you, you can check that the current methods of excluding duplicate entries from the <em>matchResults </em></li>

</ol>

ArrayList do not work, by first constructing the league with the

Deserialize Match Results button and the serialized file,

<em>2017-18 Premier League Results.ser. </em>After this, press the

Deserialize Match Results And Add To League Table

button and choose the <em>2017-18 Premier League Results.ser </em>file again.




Overriding <em>equals() </em>means we also have to override Object’s <em>hashCode()</em> method, which has been done.




Complete the <em>equals()</em> method in <em>DatedMatchResult</em> so that the

buttons to add extra results work as they should.                                       <strong>[12 marks] </strong>

<ol start="5">

 <li>The <em>LeagueStandingComparator </em>class compares points to find teams’ standing in the league. If teams are equal on points then it compares goal difference. If teams are equal on points and goal difference then they are equal. Change the comparator so that it implements an additional comparison: if teams are equal on points and goal difference, then the comparator compares the number of goals scored by each team. The team with the higher number is ahead of the other</li>

</ol>

team in the league. However, if both teams have scored the same

number of goals then they are equal.                                                          <strong>[12 marks] </strong>

<ol start="6">

 <li>Describe how the <em>LeagueTableCreatorGui</em> class can give the results of the league up to a particular date, when the user clicks on that date. You do not need to describe in detail how each method and class involved in producing this result works: a high level overview will be enough.</li>

</ol>




For example, you might want to begin your explanation as follows:




The <em>createDatesScrollPane()</em> method in the

<em>LeagueTableCreatorGui </em>class makes a JScrollPane

displaying a JList – in this instance a clickable list of objects of type LocalDate. An inner class implementation of the ListSelectionListener interface listens to the JList and when a date is clicked by the user it…




Give your explanation as a long comment at the bottom of the <em>LeagueTableCreatorGui </em>class<em>. </em>A long comment means 2 or 3

paragraphs at most. A paragraph is at most 8 sentences.                          <strong>[6 marks] </strong>

<ol start="7">

 <li>When adding new methods and variables, or renaming existing ones, please remember to make your names as meaningful as possible,</li>

</ol>

following the advice from <em>Clean Code </em>given in coursework

assignment 1, and reproduced here in Appendix A.                                   <strong>[3 marks] </strong>




<h2><a name="_Toc17217"></a>Reading for part A</h2>

The following chapters and pages of volume 2 of the subject guide, and associated <em>Head First Java </em>(HFJ) readings:




<ul>

 <li>Subject guide chapter 2, sections 2.2, 2.11 and HFJ 275-278 (static utility classes)</li>

 <li><u><a href="http://www.javapractices.com/topic/TopicAction.do?Id=40">http://www.javapractices.com/topic/TopicAction.do?Id=40</a></u> (private constructors)</li>

 <li>Subject guide chapter 3, sections 3.2, 3.3, 3.5, 3.6 and HFJ 319-326, and 329-333 (handling exceptions)</li>

 <li>Subject guide chapter 5, sections 5.3 and HFJ 447, 452-454 and 458-9 (files, parsing with <em>split(), </em>streams including <em>BufferedReader</em> and <em>BufferedWriter</em>)</li>

 <li>Subject guide chapter 6, sections 6.2, 6.3, 6.4 and HFJ 429-438; 441-3 (serialization)</li>

 <li><u><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">https://stackoverflow.com/questions/2265503/why</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">do</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">i</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">need</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">to</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">override</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">the</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">equals</a></u><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java</a><u><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">and</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">hashcode</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">methods</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">in</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">–</a><a href="https://stackoverflow.com/questions/2265503/why-do-i-need-to-override-the-equals-and-hashcode-methods-in-java">java</a></u> (overriding <em>equals()</em>)</li>

</ul>




<h2><a name="_Toc17218"></a>Deliverables for part A</h2>

<em>Please put your name and student number as a comment at the top of your Java files. Please only hand in the files asked for. </em>




Please submit an electronic copy of your amended classes as follows:

<ul>

 <li><em>java</em></li>

 <li><em>java </em></li>

 <li><em>LeagueTableCreatorGui.java (with your changes plus your answer to Q6) </em></li>

 <li><em>LeagueTableFileWriter.java </em></li>

 <li><em>java </em></li>

 <li><em>java </em></li>

</ul>







<h1><a name="_Toc17219"></a>Part B</h1>

<h2><a name="_Toc17220"></a>Introduction</h2>

You have been given the file <em>ThreadedMatchResultsServer.java</em>, together with <em>DatedMatchResultV2.java </em>and<em> 2017-18-PLResults.ser</em>.




The <em>ThreadedMatchResultsServer </em>class is threaded, this means that it can connect to multiple clients at the same time. It also means that a particular client can connect and disconnect repeatedly, as the <em>ThreadedMatchResultsServer </em>does not die when a client disconnects (which it would do if not threaded).




The <em>ThreadedMatchResultsServer </em>sends a serialized ArrayList to the client. The ArrayList is deserialized from the file <em>2017-18-PLResults.ser</em>.




<h2><a name="_Toc17221"></a>The questions</h2>

Please complete the following tasks:




<ol>

 <li>Write the class <em>MatchResultsClient</em>. The <em>MatchResultsClient </em>should do the following:</li>

</ol>




<ul>

 <li>connect to the <em>ThreadedMatchResultsServer</em> and</li>

</ul>

accept the serialized ArrayList from the server

<ul>

 <li>deserialize the ArrayList</li>

 <li>print the contents of the deserialized ArrayList to standard output, by printing each ArrayList element individually in an enhanced for</li>

 <li>handle exceptions. Your class should not have an Exception catch block, but instead should have one catch block for each of the possible sub-classes of Exception that the class could throw.</li>

 <li>Each catch block should give some information about the exception thrown.</li>

</ul>

<strong>[18 marks] </strong>

<ol start="2">

 <li>Write a <em>toString()</em> method in the <em>DatedMatchResultsV2</em> Your method should print the fields of the class in the order: <em>date, homeTeam, awayTeam, homeScore, awayScore</em>. Your method should output results in columns, such that they are easy for the user to read, as in the example below.</li>

</ol>

<strong>[6 marks] </strong>

<ol start="3">

 <li>While writing your class please remember to make your</li>

</ol>

names as meaningful as possible, following the advice from

<em>Clean Code </em>(see appendix A).                                                      <strong>[3 marks] </strong>




<h2><a name="_Toc17222"></a>Example of first three lines of output of the deserialized ArrayList, using a toString()</h2>

<h2><a name="_Toc17223"></a>method in DatedMatchResultV2</h2>




2018-05-13      West Ham        Everton         3 1

2018-05-13      Spurs           Leicester       5 4

2018-05-13      Swansea         Stoke           1 2




<h2><a name="_Toc17224"></a>Reading for part B</h2>

<ul>

 <li>Subject guide volume 1 sections 6.3 and HFJ page 116 (the enhanced for loop)</li>

 <li>Subject guide volume 2, sections 3.1 – 3.6 and HFJ 319-326, and 329-333 (handling exceptions)</li>

 <li>Subject guide volume 2, sections 7.1 to 7.10 (clients and servers)</li>

 <li><u><a href="https://www.geeksforgeeks.org/java-string-format-examples/">https://www.geeksforgeeks.org/java</a><a href="https://www.geeksforgeeks.org/java-string-format-examples/">–</a><a href="https://www.geeksforgeeks.org/java-string-format-examples/">string</a><a href="https://www.geeksforgeeks.org/java-string-format-examples/">–</a><a href="https://www.geeksforgeeks.org/java-string-format-examples/">format</a><a href="https://www.geeksforgeeks.org/java-string-format-examples/">–</a><a href="https://www.geeksforgeeks.org/java-string-format-examples/">examples/</a></u> (using Java String <em>format()</em> with examples). Note that the LocalDate class has its own <em>toString()</em> method and hence can be formatted as a String.</li>

 <li>Subject guide volume 2 Chapter 12 (Threads).</li>

</ul>




<h2><a name="_Toc17225"></a>Deliverables for part B</h2>

<ol>

 <li>An electronic copy of your class:<em>java</em></li>

 <li>An electronic copy of your amended class:<em>java</em></li>

</ol>







<h1><a name="_Toc17226"></a>Appendix A: advice on readable code from coursework assignment 1</h1>

<strong> </strong>

<strong>1.0 Readable code </strong>

In his book <em>Clean Code: A Handbook of Agile Software Craftsmanship</em> (published in 2008 by Prentice Hall, ISBN 978-0132350884). Robert C Martin describes a system for writing readable code.




Mr Martin writes:




One difference between a smart programmer and a professional programmer is that the professional understands that <em>clarity is king</em>. […] We want to use the popular paperback model whereby the author is responsible for making himself clear and not the academic model where it is the scholar’s job to dig the meaning out of the paper.




Mr Martin writes that ‘making your code readable is as important as making it executable’. He believes that names of variables, methods and classes are a major part of what makes our code readable:




The name of a variable, function or class should answer all the big questions. It should tell you why it exists, what it does, and how it is used. If a name requires a comment, then the name does not reveal its intent.




Martin dislikes comments, noting that as code is updated comments are rarely updated at the same time, so however helpful a comment at the start, once a class has been in use for a while any comments are likely to be outdated and confusing. He believes that code should be written with names that make the intent clear, such that comments are redundant.




You should note that the programmer has tried to follow the advice given by Martin in writing classes. However, Martin himself notes that names can always be improved, and that we should not be afraid to keep refining our code.




See Appendix B for an example of renaming a simple class to make it more readable.




When answering questions in this assignment, please note the following rules outlined by Martin:




<strong>1.1 Formatting </strong>

<strong> </strong>“You should take care that your code is nicely formatted. You should choose a set of simple rules that govern the layout of your code, and then you should consistently apply those rules. […] It helps to have an automated tool that can apply those formatting rules for you.”




<strong>1.2 Methods </strong>

<ul>

 <li><strong>Method should do one thing only</strong>. If your method does more than one thing, break it into separate methods.</li>

 <li><strong>Do not repeat yourself</strong> – if you find yourself writing the same code more than once, put it into a method.</li>

 <li><strong>Too many arguments (parameters to a method).</strong> “No argument is best, followed by one, two and three. More than three is very questionable and should be avoided with prejudice.”</li>

</ul>




<ul>

 <li><strong>Comments </strong></li>

</ul>

If you do write a comment, make sure it is grammatical, short, does not state the obvious and is really needed.




<ul>

 <li><strong>Names </strong></li>

</ul>

<ul>

 <li><strong>Choose descriptive names </strong>“Names in software are 90% of what makes software readable”.</li>

 <li><strong>Unambiguous names</strong> “choose names that make the workings of a function or variable unambiguous”.</li>

 <li><strong>Names should describe side effects</strong>, <em>g</em>. a method getOos() will make an ObjectOuputStream if one does not already exist, so should be called createOrReturnOos()</li>

</ul>




<strong>1.5 General </strong>

<ul>

 <li><strong>Obscured intent</strong> – make the code as expressive as possible such that its intention is clear from a first reading.</li>

 <li><strong>Put conditional statements into a method to make their intention and effect clear</strong>, <em>g. </em></li>

</ul>

<strong>BAD</strong> if (guessedWord.length()&lt; shortestLength)

<strong>GOOD</strong> if(guessedWordIsTooShort(guessedWord))




<strong> </strong>

<strong> </strong>

<h1><a name="_Toc17227"></a>Appendix B</h1>




A simple example of renaming methods and variables for greater readability.




<strong><em>Original </em></strong>




public class Calculator{




public static void calc(int x){

if (x &gt;= 70){

System.out.println(“grade = A”);

return;

}

if (x &gt;= 60){

System.out.println(“grade = B”);

return;

}

if (x &gt;= 50){

System.out.println(“grade = C”);

return;

}

if (x &gt;= 40){

System.out.println(“grade = D”);

return;

}

if (x&lt;40) System.out.println(“grade = F”);

}




public static void main(String[] args) {

calc(90);             calc(53);            calc(30);

}

}




<strong><em>Renamed </em></strong>

<strong><em> </em></strong>

public class GradeCalculator {




public static void calculateAndPrintGrade(int finalMark){             if (finalMark &gt;= 70){

System.out.println(“grade = A”);

return;

}

if (finalMark &gt;= 60){

System.out.println(“grade = B”);

return;

}

if (finalMark &gt;= 50){

System.out.println(“grade = C”);

return;

}

if (finalMark &gt;= 40){

System.out.println(“grade = D”);

return;

}

if (finalMark&lt;40) System.out.println(“grade = F”);

}

public static void main(String[] args) {        calculateAndPrintGrade(90);           calculateAndPrintGrade(53);           calculateAndPrintGrade(30);

}

}

<h1><a name="_Toc17228"></a>Appendix C: The List interface</h1>




You will note that in the classes given, ArrayLists are of type List.




List is an interface: <u><a href="https://docs.oracle.com/javase/7/docs/api/java/util/List.html">http://docs.oracle.com/javase/7/docs/api/java/util/List.html</a></u>




Explanation below, modified from Effective Java, 2nd edition by Joshua Bloch:




<em>You should use interfaces rather than classes as parameter types. More generally, you should favour the use of interfaces rather than classes to refer to objects. If appropriate interface types exist, then parameters, return values, variables, and fields should all be declared using interface types. </em>




Get in the habit of typing this:




// Good – uses interface as type

List&lt;Subscriber&gt; subscribers = new ArrayList&lt;Subscriber&gt;();




rather than this:




// Bad – uses class as type!

ArrayList&lt;Subscriber&gt; subscribers = new ArrayList&lt;Subscriber&gt;();




If you get into the habit of using interfaces as types, your program will be much more flexible. If you decide that you want to switch implementations, all you have to do is change the class name.




For example, the first declaration could be changed to read:

List&lt;Subscriber&gt; subscribers = new LinkedList&lt;Subscriber&gt;();

and all of the surrounding code would continue to work. The surrounding code was unaware of the old implementation type, so it would be oblivious to the change.
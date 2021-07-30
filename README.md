# JMeter-Script-July201

-- Open **ApacheJMeter.jar** to create script

-- Add the **Thread group** where we can record and play our workfolw

-- Setting before recording

-- I Used Google Chrome and setup proxy for communication between JMeter and Chrome - We can use any browser but we have to make sure JMeter and Browser setting have same port so that can help to record the script

## Recording

-- Add the **HTTP(S) test Script Recorder under test plan** - you can get this under **Non-Test Elements** - ( I removed after recoding and also disable unnecessory calls)

-- Recording start with Google Chrome First land on Podium Home page

-- Second step under Prodcut click VideoChat

-- Under Video Chat Response I found the response for "Personalize their experience" and "Shorten the sales cycle"

-- How I found the Response, so I add the "View Results tree" under the thread group (Listner) where we can see request and response 

### Logic applied and Post Processor applied in script

-- To Handele word count and text print (print the line in file) follow below steps

-- Add two **regulaer expression extractor** under VideoChat request (Inside Post Processor) to capture the "Personalize their experience" and "Shorten the sales cycle" text message response 
 
 ![image](https://user-images.githubusercontent.com/88197312/127676305-fe727edf-3f28-4b31-8384-05d4164ce2ef.png)
 ![image](https://user-images.githubusercontent.com/88197312/127676455-a9d2dd3d-c979-49f8-936d-da4b5a2c3370.png)

-- Also, I added **Debug Sampler** under the Thread Group for validate we capture the correct correlation from the Regualer expresion extractor

-- Add **BeanShell PostProcessoer** under the VideoChat request to counting the word and Print message (text or sentence) in the file

"Code Return in script pan for the output (BeanShell PostProcessor)"

--import org.apache.commons.lang.StringUtils;
/*
para1 = vars.get("c_paragraph1_g1");
String ch = vars.get("c_paragraph1_g1");
para2 = vars.get("c_paragraph2_g1");

// Splits string into an array (space, tabs, ., etc)
  String[] words = ch.split("\\s+");
  
//Write output in the file
f = new FileOutputStream("pararesult.txt", true);
p = new PrintStream(f); 
this.interpreter.setOut(p); 
print("count of words in paragraph Personalize their experience = "+words.length);
print("\nParagraph Personalize their experience = "+para1 + "\nParagraph Shorten the sales cycle = " + para2);
f.close();
*/

#### Replay and output from the Script

-- I make this scripts to play 1 iteration and file will generate under the JMeter software --> bin folder

-- I didn't put any particular path so you can execute without any issue. You need JMeter installation in your system, and under apache_JMeter folder you find the bin folder and under that folder you can see file **pararesult.txt** will created after the running **PodiumScript.jmx** file

-- Every run you can delete that file, otherwise every run message is appending in the same file 

--For Example:
![image](https://user-images.githubusercontent.com/88197312/127678208-a3eca992-b330-4722-9614-0fb42f07efca.png)







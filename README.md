# WiSDOM

> This repository contains the prototype for WiSDOM obfuscation module concept. Created during HackDSC'21 under Open Innovation in Data Privacy and Security domain. 

> This project is in active development phase.

![](docs/bannerblack.png)

**WiSDOM : WriterScript based Data Obfuscation Module**

WiSDOM is a strategic Data Obfuscation Module that takes your sensitive data and converts it into a work of literature.
This means that even if your data is intercepted the original content will be secure and the attacker will see something else altogether. You can disguise your Bank Account details as a chapter from Harry Potter and no one would be the wiser.
Even if your sensitive data is intercepted chances are that it will be ignored due to its innocuous appearance. With the increasing use of cyberspace, everything is online and thus accessible to attackers. From Private messages to Financial Details everything can be intercepted online.

WiSDOM can obfuscate your plaintext/data structure/ binary data (<1MB) into **infinite** combinations of random data for transmission over insecure internet protocols like HTTP, TELNET, and FTP. This **can also be extended to store data in databases** where heavy encryption algorithms cannot be implemented due to resource constraints or instant messaging services. More accessible than many encryptions algorithms, efficient on low-end systems.

WiSDOM provides easy-to-use API and GUI (made in Python3 Flask). Herokuapp has been used to deploy and manage WiSDOM for increased accesibility.

Currently WiSDOM is viable for use with files smaller than **1MB** due to the increased sie of file after conversion to WriterScript but adding a suitable file compression module before transmissio or storage is in pipeline and would be incorporated soon'.
The webapp currently only has a modue for credit card details obfuscation, for all other data WiSDOM would have to be installed and data would have to be manually converted but making the webapp available for general data obfuscation is underway. 


**Installation**
------------
**Docker (recommended)**
```shell
docker pull x64mayhem/writerscript

docker run -it -v .:/writerscript/ x64mayhem/writerscript
```


**Stable-ish (From PyPI):**
```shell
python3 -m pip install writerscript
```

**Bleeding Edge (From Source) :**
```shell
git clone https://github.com/Saket-Upadhyay/WriterScript.git
cd WriterScript/WriterScript/

python3 setup.py install
```
> NOTE : Alternately for credit card details obfuscation you can use the WiSDOM webapp.


**Usage**
**Using the webapp for credit card details**


![image](https://user-images.githubusercontent.com/57125431/122719663-2270bc00-d28c-11eb-9b52-03bdbb137099.png)

**Step 1 :** visit https://wisdomdemo.herokuapp.com and select credit card demo.
> NOTE : If https://wisdomdemo.herokuapp.com/checkformdatarender crashes then please **refresh** the page, there is some unknown bug in heroku deployment that does not happen in local execution.


![image](https://user-images.githubusercontent.com/57125431/122719709-374d4f80-d28c-11eb-910a-6e6fa0f35672.png)

**Step 2 :** Enter credit card details and click on submit.


![image](https://user-images.githubusercontent.com/57125431/122719892-6d8acf00-d28c-11eb-99cf-e609042b47a9.png)

**Step 3 :** Your credit card details will be sent over the WiSDOM server in the above format.


![image](https://user-images.githubusercontent.com/57125431/122722053-ebe87080-d28e-11eb-9c34-89bd180219ed.png)

**Step 4 :** To decode the obfuscated data select the decode ption on the main page of the webapp and paste the the obfuscated data and click on ubmit to API to get the original data.

**Using command line and writerscript module**
**Step 1 :** Install the writerscript module following the installation instructions in this README.

**Step 2 :** Copy the source to a text file

**Step 3 :** Replace the following elements with null -
```
, -> null
. -> null
r'\n' ->null

r'\[([a-z])*|([0-9])*\]' -> null
```
For Data from WikiPedia :
Remove all [0-9] index by replacing `r'\[[(0-9)]*\]'` with  ` `.
and all [a-z] index by replacing `r'\[[a-z]*\]'` with  ` `.

**For Example** 
```
A programming language is a notation for writing programs, which are specifications of a computation or algorithm.[3] Some authors restrict the term "programming language" to those languages that can express all possible algorithms.[3][4] Traits often considered important for what constitutes a programming language include:

Function and target
  A computer programming language is a language used to write computer programs, which involves a computer performing some kind of computation[5] or algorithm and possibly control external devices such as printers, disk drives, robots,
[6] and so on. For example, PostScript programs are frequently created by another program to control a computer printer or display.
More generally, a programming language may describe computation on some, possibly abstract, machine. It is generally accepted that a complete specification for a programming language includes a description, possibly idealized, of a machine or processor for that language.
[7] In most practical contexts, a programming language involves a computer;
consequently, programming languages are usually defined and studied this way.
[8] Programming languages differ from natural languages in that natural languages are only used for interaction between people, while programming languages also allow humans to communicate instructions to machines.
```

Becomes ->

```
A programming language is a notation for writing programs which are specifications of a computation or algorithm Some authors restrict the term "programming language" to those languages that can express all possible algorithms Traits often considered important for what constitutes a programming language include: Function and target A computer programming language is a language used to write computer programs which involves a computer performing some kind of computation or algorithm and possibly control external devices such as printers disk drives robots and so on For example PostScript programs are frequently created by another program to control a computer printer or display More generally a programming language may describe computation on some possibly abstract machine It is generally accepted that a complete specification for a programming language includes a description possibly idealized of a machine or processor for that language In most practical contexts a programming language involves a computer; consequently programming languages are usually defined and studied this way Programming languages differ from natural languages in that natural languages are only used for interaction between people while programming languages also allow humans to communicate instructions to machines
```

**Step 4 :** Save with `.txt` extention.

**Step 5 :** Convert your formatted plaintext to brainfuck using an online plaintext to brainfuck converter.

**Step 6 :** Save your BrainFuck `oneliner` code as `.txt`


**Step 7 :** Run `wscript -g -sbf brainfuckfile.txt -stxt textfile.txt`

**Step 8 :** `out.pen` file will be created

**Test :** To test the code run `wscript -e -s out.pen` 





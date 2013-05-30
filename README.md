Setting up Selenide for the NTD Workshop
========================================

1. Install Mozilla Firefox
--------------------------
* http://www.mozilla.org/en-US/firefox/new/

2. Install JDK 7 (Java Development Kit)
--------------------------
* http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html

As a result, there should be ../Program Files/Java/jdk1.7.x_xx

3. Install IntelliJ IDEA Community Edition
--------------------------
* http://www.jetbrains.com/idea/download/

4. Start IDEA, Press 'Create New Project'
--------------------------

* On the Left, choose 'Maven Module'
* Change Project Name to be "Webtest"
* Project SDK... choose "1.7"
* If there is nothing in the selection, press 'New...' and locate the folder ../Program Files/Java/jdk1.7.x_xx

* Press Next
* Press Finish

5. IDEA has created a new project.
--------------------------

* On the left, there is a folder named Webtest, expand this folder.
* Open pom.xml file.

* Replace the contents with this:

         <?xml version="1.0" encoding="UTF-8"?>
         <project xmlns="http://maven.apache.org/POM/4.0.0"
                  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
             <modelVersion>4.0.0</modelVersion>
             <groupId>MySel20Proj</groupId>
             <artifactId>MySel20Proj</artifactId>
             <version>1.0</version>
             <dependencies>
                 <dependency>
                     <groupId>junit</groupId>
                     <artifactId>junit</artifactId>
                     <version>4.11</version>
                 </dependency>
                 <dependency>
                     <groupId>com.codeborne</groupId>
                     <artifactId>selenide</artifactId>
                     <version>2.0</version>
                 </dependency>
                 <dependency>
                     <groupId>org.seleniumhq.selenium</groupId>
                     <artifactId>selenium-java</artifactId>
                     <version>2.31.0</version>
                 </dependency>
                 <dependency>
                     <groupId>com.opera</groupId>
                     <artifactId>operadriver</artifactId>
                 </dependency>
             </dependencies>
             <dependencyManagement>
                 <dependencies>
                     <dependency>
                         <groupId>com.opera</groupId>
                         <artifactId>operadriver</artifactId>
                         <version>1.1</version>
                         <exclusions>
                             <exclusion>
                                 <groupId>org.seleniumhq.selenium</groupId>
                                 <artifactId>selenium-remote-driver</artifactId>
                             </exclusion>
                         </exclusions>
                     </dependency>
                 </dependencies>
             </dependencyManagement>
         </project>


* Now, on the right upper side there is a message: "Maven Projects need to be imported"
* Press 'Enable Auto-Import'

* Maven will now download all the needed stuff: junit, selenide etc.. (might take a while)
* When all red is gone, all packs have been downloaded.

6. Lets create the test class.
--------------------------

* On the left expand 'src' folder.
* Then expand 'test' folder.

* There is an item called 'java' with a green folder icon, right click on that.
* Select New -> Java Class
* Enter 'Webtest' as the class name.
* Press OK.

7. The first test...
--------------------------

* Open the newly created Webtest.java class
* Replace the contents with this:

         import org.junit.Test;
         
         import static com.codeborne.selenide.Condition.text;
         import static com.codeborne.selenide.Selenide.*;

         public class Webtest {
         
             @Test
             public void openTest(){
                 open("https://ntd2013-workshop.herokuapp.com");
                 $(".page-header").shouldHave(text("Articles"));
             }
         }
         
8. Run the test
--------------------------

* On the left, right click on our Webtest item.
* Click on Run 'Webtest'

Then a mozilla browser should start for a moment and then close.
* On the left, if there is a green text "All Tests Passed", you are ready for the NTD Selenide workshop

9. Eclipse users
--------------------------
Eclipse does not have Maven installed by default.

* Add Maven plugin to eclipse:
* Open Eclipse. Help -> Install new Software
* Work with, choose --All available Sites--
* Below, type 'Maven'
* Choose the newest 'm2e - Maven Integration for Eclipse'
* Press Next
* Next
* I accept
* Finish

* Then follow the IDEA steps to setup Selenide

Selenide wiki
--------------------------

* https://github.com/codeborne/selenide

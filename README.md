# IT_66_poe
create a web app that displays photographs of any 2 indian personalities .By clicking images a few inspirational quotes by these personalities shall be displayed 
use github/gitlab ,maven,tomcat with jenkins.automate deployment of application to a container using jenkins plugins ,"deploy to container". Also use "build pipeline" plugin.

6th aaya.....ye code naa 
WEB_MAVEN/src/main/webapp

/index.jsp..............index.jsp mein dal.....
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Indian Personalities</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f0f0;
        }
        header {
            background-color: #333;
            color: #fff;
            padding: 10px;
        }
        nav ul {
            list-style: none;
            padding: 0;
            display: flex;
            justify-content: center;
        }
        nav ul li {
            margin: 0 10px;
        }
        nav ul li a {
            text-decoration: none;
            color: #fff;
        }
        main {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        .personality {
            margin: 10px;
            text-align: center;
            cursor: pointer;
        }
        .personality img {
            width: 200px;
            height: auto;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease-in-out;
        }
        .personality img:hover {
            transform: scale(1.1);
        }
        .quote-container {
            text-align: center;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <header>
        <nav>
            <ul>
                <li><a href="#">HOME</a></li>
                <li><a href="#">ABOUT</a></li>
                <li><a href="#">CONTACT</a></li>
                <li><a href="#">ADMISSION</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <div class="personality" onclick="displayQuote(1)">
            <img src="indian_personality_1.jpg" alt="Indian Personality 1">
        </div>
        <div class="personality" onclick="displayQuote(2)">
            <img src="indian_personality_2.jpg" alt="Indian Personality 2">
        </div>
        <!-- Add more personalities as needed -->
    </main>
    <div class="quote-container">
        <p id="quoteDisplay"></p>
    </div>
    <script>
        function displayQuote(personalityId) {
            var quoteDisplay = document.getElementById("quoteDisplay");
            switch (personalityId) {
                case 1:
                    quoteDisplay.innerHTML = "Inspirational Quote by Personality 1";
                    break;
                case 2:
                    quoteDisplay.innerHTML = "Inspirational Quote by Personality 2";
                    break;
                // Add more cases for other personalities
                default:
                    quoteDisplay.innerHTML = "No quote available";
            }
        }
    </script>
</body>
</html>


jenkins aur tomcat open kar
localhost8080 and 8081

2)open jenkins localhost:8080 ,
6)go to Dashboard>new item write the project name and choose free style project
7)add the github account which you created  
under build Triggers go to poll scm and write five * with single space
Add a build step select Maven and in goal write “clean install
In post build select deploy war/ear to a container
Write this **/*.war and in context path you can write any name but keep in mind for deployment
Select add container and select the tomcat version which you have installed (in this case it is 9.0 version)
Now write the username(admin) and password(admin) which you have written in the tomact-user.xml click on add
Now you will able to see that under cerdentials click on it and write the tomcat url as it is (as suggested while downloading you have to change the port to 8081)
Now save and run it is successfully build 

Now to deploy just write “http://localhost:8081/MavenDeploy/ “ in browser

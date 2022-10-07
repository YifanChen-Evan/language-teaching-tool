README


A language teaching tool that allows users to customize learning materials of their own interest using native language video content on the YouTube platform, and to improve foreign language proficiency with the aid of listening comprehension quizzes.


------------------------Features------------------------

By analyzing the difficulties that Chinese learners generally face in English learning and combining my own experience of learning English, I have given this website two characteristics.

(1) The website supports user-made learning lessons, which not only allows learners to use their favorite videos as learning materials, but also provides a new teaching method for English teachers without any programming foundation. Teachers can use this website to prepare teaching content and quiz questions.

(2) The website encourages the use of Chinese TV dramas to learn English, so as to train learners' reaction speed in converting between Chinese and English.


------------------------3rd Party Libraries and Frameworks------------------------

1. JSON
JSON is a text format for storing and transporting data, which is “self-describing” and easy to understand. Although the JSON syntax is derived from JavaScript object notation, the JSON format is text only. So I chose to use JSON file format to define lessons. For some language teachers without knowledge of Vue.js, JavaScript and HTML, it is achievable to write a new JSON file with different video sources and their own questions etc.

2. Vue.js
The quiz panel needs to be repeatedly shown and hidden at specific timestamps and the data rendered to the DOM needs to be changed each time. If only JavaScript is used to manipulate the DOM, the code with the same logic is repeatedly written many times, which not only reduces the coding efficiency, but also increases the difficulty of maintaining the code in the future. Hence, using Vue.js to create the user interface for the quiz panel simplifies code and increases code reuse. The two-way coupling between data and DOM elements can reduce times from user interaction to result, remove or reduce page-refreshes, and allow for the potential of smooth transitions between page changes.


------------------------How to create lesson description file (LDF)------------------------

The lesson description file (LDF) is a file that stores various attributes of the lesson in JSON format, including 5 properties which are video title, video link, video cover, difficulty level and data related to quiz questions.

- The “title” key refers to the video title and its value is the English title and Chinese title of the video.

- The “iframeVideoUrl” key is used to store external links of embedded video. Its value can be obtained from the video's play page on YouTube by clicking the “Share” button, choosing “Embed” option and copying the source of the link.

- The relative path of the video cover is stored in the value of “videoImage” key. Users can also directly copy the link of the image on the Internet and paste it here.

- The “level” key refers to the overall difficulty level of the quiz questions in the video. Its value can be “Beginner”, “Intermediate” or “Advanced”.

-The value of the “jsonData” key is an array that stores 5 properties describing each quiz question. The number of JSON objects depends on the number of questions set by the user.

(1) The “timestamp” key is used to set the time point at which the quiz question pops up. Its value is the time in seconds. For example, to set the first quiz question at 4 minutes and 50 seconds, the value of the “timestamp” key would be 290 (60 * 4 + 50 = 290).
(2) The “question” property is the Chinese line at the timestamp, and it is also the question of the quiz. Users should translate Chinese lines into appropriate English lines.
(3) The options for the question are stored in the value of the “answer” key as an array. It usually includes the authentic expression that is used by native speakers, as well as two other less idiomatic translations but commonly used by Chinese students. But the user can also increase or decrease the number of options stored in the array.
(4) The value of the “correctAnswer” key is the index of the correct answer in the “answer” array.
(5) The grading weight for each question can be set individually without having to set the same score for all questions. But in the example shown in the figure, since the number of questions is 5, for the convenience of calculating the final quiz score, I set the “gradingWeights” of each question to 20.


------------------------Materials------------------------

1. index.html
The main HTML file including the home page, "Get started" page and "Lesson" page.

2. LDF.html
The instruction about how to write a Lesson description file (LDF).

3. help.html
The guidance of the website.

4. about.html
The introduction of the website and its author Yifan Chen.

5. index.css
The main CSS file.

6. quizStyle.css
The style sheet of quiz panel, result panel, review panel and modal warning panel.

7. index.js
It's used to hide/display the menu icon because it's a responsive website. When the size of screen turns to be small, the hamburger icon will appear and the navigation will be hidden.

8. vue.js
The reactivity of Vue.js framework is used to update data to the DOM element.

9. axios.js
I use axios to send a request to the server to get the "JSONFolder" folder.

10. "assets" folder
It contains 6 SVG images.

11. "img" folder
It contains 10 images.
- the background image of quiz panel
- the background image of the website
- the 4 covers of default lessons
- the mind map of "LDF" page
- the mind map of "Help" page
- the image of Yifan Chen
- the icon of website

12. JSONFolder
It contains 4 default lesson description files.


------------------------Assets Resources------------------------

1. YouTube API
https://developers.google.com/youtube/iframe_api_reference

2. Vue.js
https://vuejs.org/guide/quick-start.html#creating-a-vue-application

3. axios.js
https://github.com/axios/axios

4. arrow.svg
https://fonts.google.com/icons?selected=Material%20Symbols%20Outlined%3Aarrow_right_alt%3AFILL%400%3Bwght%40400%3BGRAD%400%3Bopsz%4048

5. menu.svg
https://fonts.google.com/icons?selected=Material%20Symbols%20Outlined%3Amenu%3AFILL%400%3Bwght%40400%3BGRAD%400%3Bopsz%4048

6. arrow_back.svg
https://fonts.google.com/icons?selected=Material%20Symbols%20Outlined%3Aarrow_back%3AFILL%400%3Bwght%40400%3BGRAD%400%3Bopsz%4048

7. arrow_forward.svg
https://fonts.google.com/icons?selected=Material%20Symbols%20Outlined%3Aarrow_forward%3AFILL%400%3Bwght%40400%3BGRAD%400%3Bopsz%4048

8. correct.svg
https://fonts.google.com/icons?selected=Material%20Symbols%20Outlined%3Adone%3AFILL%400%3Bwght%40400%3BGRAD%400%3Bopsz%4048

9. wrong.svg
https://fonts.google.com/icons?selected=Material%20Symbols%20Outlined%3Aclose%3AFILL%400%3Bwght%40400%3BGRAD%400%3Bopsz%4048

10. favicon.ico
https://www.google.com/url?sa=i&url=https%3A%2F%2Fspeechling.com%2Flistening&psig=AOvVaw22SlCjvG48sQmsZKYSuEIY&ust=1664896803510000&source=images&cd=vfe&ved=0CAwQjRxqFwoTCNjF7YauxPoCFQAAAAAdAAAAABAD

11. Desk.jpg
https://images.unsplash.com/photo-1518655048521-f130df041f66?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8ZGVza3xlbnwwfHwwfHw%3D&auto=format&fit=crop&w=800&q=60

12. Online.jpg
https://images.unsplash.com/photo-1484807352052-23338990c6c6?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHx2aXN1YWwtc2VhcmNofDF8fHxlbnwwfHx8fA%3D%3D&auto=format&fit=crop&w=800&q=60

13. 梦华录.jpeg
http://www.inewsweek.cn/2022/0613/U863P972DT20220613105452.jpg

14. 流光之城.jpeg
https://live.staticflickr.com/65535/51831650751_49b6ef14c6_b.jpg

15. 甄嬛传.jpeg
https://i04piccdn.sogoucdn.com/fcd757c9198709ce

16. 花千骨.jpeg
http://www.sinaimg.cn/dy/slidenews/24_img/2015_35/66519_1258354_791758.jpg

17. Evan01.png
My photo.

18. Get Started.png
I created the mind map using XMind.

19. Lesson Description File.png
I created the mind map using XMind.

The leftover f this project as I see it
*polish the voice system(the feedback, wakewords, form filling and dashboard integration)
*add emails to when calls startes
*polish the modals (comments/posts/and other display modals) 
*polish the call UI
*add prof status override other then relaying on the database
*all the theory side of this project is still waiting
###############################################
But from what I can call it, this project is well functional and great looking. 
When I come back with a clearer mind, this left overs would cross easy

###########################################################
if the doc about the original idea isnt here...i'll add it

FYI this is a self built learning base project, it is not perfect but very functional to all the levels I could think of
######################################################################################################################

The core idea and the base of the progress(the primary prototype description) are both available in the idk pdf in this project 
This project went through plenty of phases and changes, all lead to the best growth in both productivity and my skills
But the jurney is not over yet, this has more potentials to grow even more
Just not for the moment since I need to focus on other aspects

#############################

##########################################

for the override.....i have a table to explain what can be overridden
<img width="935" height="461" alt="image" src="https://github.com/user-attachments/assets/b4dcaa6d-d086-489f-93f1-b3589acd4447" />
######################################
python ahh comments.....either way just clearing this read me because i actually read what it had

############################################################
Back to being solo.....maybe for the best?time would tell. ...i was always solo. ...
I need to get back to the ovrride and add the prof status override at some point. ...
Right now, it happens that I don't have much to do in the improve list, but what is left is quite heavy and time consuming. ...
##################################################################################
<strong>Future improvs</strong>


More Collaborative Features:


Answered/Unanswered filtering — community can see what questions still need
help, encourages people to contribute(this,I think op should have control over)(DONE)

• Peer endorsements — users can endorse each other's expertise in a subject (like
LinkedIn skills but academic)(DONE)

• "Looking for study partner" posts — a specific post type for finding someone to
study with(DONE)

• Room chat improvs --- migrate from polling to WebSockets to support actual real(DONE---mostly functional)
time chats and future video and audio calls.


AI Features:
• full voice navigation and action for hands free experience

• the ai in the chat tab would support files and generate study material (resumes/
summaries,flashcards,quizzes….)(DONE)

• ai will be integrated more in the platform that it supports smart search and such.(satisfied by question-suggestion + difficulty tagging + AI chat)(DONE)

• AI question suggestions — when you're typing a question, AI checks if a similar one
was already asked(DONE)

• Smart study plan — AI generates a weekly study schedule based on your major and
upcoming exams(DONE. ..i love this one)

• AI-powered room summaries — weekly digest of the most useful content in your
subject room(DONE, just checked, prompt needs to be less hostile, but works)

• Difficulty tagging — AI auto-tags posts as beginner/intermediate/advanced(DONE)


Cross-speciality room(this could be the SHIT)
A room for inter communication between different majors….auto joined for everyone
A special room type — not owned by any one specialty — called something like an
"Interdisciplinary Space" or just "Cross-Specialty" zone.
The key difference from normal rooms is the post tagging system — when you post there,
you tag it with both the domain you're coming FROM and the domain you're asking INTO.
so,when you tag your major and the major you want to ask into,that post appears in both
feeds only instead of everywhere for everyone like public space do…..
this way, the og architecture stands and we get a clean cross-major collaboration without
contaminating each individual space….
AI angle to it:
AI suggests which specialty to tag based on your question content. So the interdisciplinary
space becomes one of the first places AI is deeply integrated.
-->AY YO THIS ONE IS WORKING TOO, AND GREAT. ....we making good progress

##########################################################
And I still need to fix my stupidity in build-->working on that+need to look at phone layout+better UI for the modals and such+ the diagrams and theory and such
####################
got me a diagram of the app via gitdiagram+ its mermaid code....cool as hell
[![Architecture diagram](https://gitdiagram.com/diagram-badge.svg)](https://gitdiagram.com/basmala-laouari/glaukopis?utm_source=readme&utm_medium=badge)

%% Generated by https://gitdiagram.com/basmala-laouari/glaukopis
flowchart TD

subgraph group_client["Web client"]
  node_webapp["Web app routes<br/>[App.jsx]"]
  node_dashboard["Dashboard<br/>[Dashboard.jsx]"]
  node_search["Smart search<br/>[SearchPage.jsx]"]
  node_liveclient["Call client<br/>[useWebRTC.js]"]
  node_httpclient["API client<br/>[axios.js]"]
end

subgraph group_api["API and access"]
  node_server["Express API<br/>[app.js]"]
  node_auth["Authentication<br/>[auth.controller.js]"]
  node_authgate["Request auth<br/>[authMiddleware.js]"]
  node_socialroutes["Community routes<br/>[post.routes.js]"]
end

subgraph group_community["Learning community"]
  node_posts["Posts and comments<br/>[post.controller.js]"]
  node_rooms["Rooms and membership<br/>[room.controller.js]"]
  node_messaging["Room messaging"]
  node_endorsements["Peer endorsements"]
  node_profiles["Profiles and connections<br/>[user.controller.js]"]
  node_moderation["Administration"]
end

subgraph group_ai["AI and assistance"]
  node_aiapi["AI tools<br/>[ai.js]"]
  node_studyplans["Study plans<br/>[studyPlan.js]"]
  node_summaries["Room summaries"]
  node_aiinstructions["AI prompts<br/>[aiPrompts.js]"]
end

subgraph group_platform["Platform services"]
  node_notify["Notifications"]
  node_calls["Call transport"]
  node_uploads["Media uploads<br/>[upload.js]"]
  node_email["Email delivery<br/>[email.js]"]
  node_repositories["Domain repositories"]
  node_database[("PostgreSQL<br/>[db.js]")]
end

node_student(("Learner"))
node_cloudinary["Cloudinary"]
node_ai_services["AI providers"]

node_student -->|"uses"| node_webapp
node_webapp -->|"routes to"| node_dashboard
node_webapp -->|"routes to"| node_search
node_dashboard -->|"requests through"| node_httpclient
node_search -->|"requests through"| node_httpclient
node_liveclient -.->|"coordinates calls"| node_calls
node_httpclient -.->|"sends API requests"| node_server
node_server -->|"mounts"| node_socialroutes
node_server -->|"mounts routes"| node_auth
node_server -->|"mounts"| node_aiapi
node_server -->|"mounts"| node_studyplans
node_socialroutes -->|"protects routes"| node_authgate
node_socialroutes -->|"dispatches"| node_posts
node_socialroutes -->|"dispatches"| node_endorsements
node_posts -->|"uses repositories"| node_repositories
node_posts -->|"requests notifications"| node_notify
node_auth -->|"uses repositories"| node_repositories
node_rooms -->|"uses repositories"| node_repositories
node_profiles -->|"uses repositories"| node_repositories
node_moderation -->|"uses repositories"| node_repositories
node_repositories -->|"queries"| node_database
node_aiapi -->|"uses prompts"| node_aiinstructions
node_aiapi -.->|"requests generation"| node_ai_services
node_studyplans -.->|"generates plans"| node_ai_services
node_summaries -.->|"summarizes rooms"| node_ai_services
node_rooms -.->|"supports room chat"| node_messaging
node_rooms -.->|"supports live calls"| node_calls
node_uploads -->|"stores uploads"| node_cloudinary
node_auth -.->|"sends account email"| node_email
node_notify -->|"persists notifications"| node_database

click node_webapp "https://github.com/basmala-laouari/glaukopis/blob/main/something-frontend/src/App.jsx"
click node_dashboard "https://github.com/basmala-laouari/glaukopis/blob/main/something-frontend/src/pages/Dashboard.jsx"
click node_search "https://github.com/basmala-laouari/glaukopis/blob/main/something-frontend/src/pages/SearchPage.jsx"
click node_liveclient "https://github.com/basmala-laouari/glaukopis/blob/main/something-frontend/src/components/useWebRTC.js"
click node_httpclient "https://github.com/basmala-laouari/glaukopis/blob/main/something-frontend/src/api/axios.js"
click node_server "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/app.js"
click node_auth "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/controllers/auth.controller.js"
click node_authgate "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/middleware/authMiddleware.js"
click node_socialroutes "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/routes/post.routes.js"
click node_posts "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/controllers/post.controller.js"
click node_rooms "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/controllers/room.controller.js"
click node_messaging "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/controllers/message.controller.js"
click node_endorsements "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/controllers/peerEndorsement.controller.js"
click node_profiles "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/controllers/user.controller.js"
click node_moderation "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/controllers/admin.controller.js"
click node_aiapi "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/routes/ai.js"
click node_studyplans "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/routes/studyPlan.js"
click node_summaries "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/controllers/roomSummaryController.js"
click node_aiinstructions "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/services/aiPrompts.js"
click node_notify "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/services/notificationService.js"
click node_calls "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/services/mediasoup.manager.js"
click node_uploads "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/middleware/upload.js"
click node_email "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/config/email.js"
click node_repositories "https://github.com/basmala-laouari/glaukopis/tree/main/something-backend/repositories"
click node_database "https://github.com/basmala-laouari/glaukopis/blob/main/something-backend/db.js"

classDef toneNeutral fill:#f8fafc,stroke:#334155,stroke-width:1.5px,color:#0f172a
classDef toneBlue fill:#dbeafe,stroke:#2563eb,stroke-width:1.5px,color:#172554
classDef toneAmber fill:#fef3c7,stroke:#d97706,stroke-width:1.5px,color:#78350f
classDef toneMint fill:#dcfce7,stroke:#16a34a,stroke-width:1.5px,color:#14532d
classDef toneRose fill:#ffe4e6,stroke:#e11d48,stroke-width:1.5px,color:#881337
classDef toneIndigo fill:#e0e7ff,stroke:#4f46e5,stroke-width:1.5px,color:#312e81
classDef toneTeal fill:#ccfbf1,stroke:#0f766e,stroke-width:1.5px,color:#134e4a
class node_webapp,node_dashboard,node_search,node_liveclient,node_httpclient toneBlue
class node_server,node_auth,node_authgate,node_socialroutes toneAmber
class node_posts,node_rooms,node_messaging,node_endorsements,node_profiles,node_moderation toneMint
class node_aiapi,node_studyplans,node_summaries,node_aiinstructions toneRose
class node_notify,node_calls,node_uploads,node_email,node_repositories,node_database,node_student,node_cloudinary,node_ai_services toneIndigo

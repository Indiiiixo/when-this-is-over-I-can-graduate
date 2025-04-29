# when-this-is-over-I-can-graduate
# The script of the game goes in this file.

# Declare characters used by this game. The color argument colorizes the
# name of the character.

define e = Character("Alita", color="#c8ffc8") 
define l = Character("Nyle", color="#ffc8c8") 
define a = Character("Ben", color="#c8c8ff") 
define r = Character("Ryan", color="#ffcc99")

image Alita = "Alita.jpg" 
image Nyle = "Nyle.jpg" 
image Ben = "Ben.jpg" 
image ryan = "ryan.jpg"
image grad_alita = "Alita_grad.jpg"

image college_campus ="college_campus.jpg"
image dorm ="dorm.jpg"
image party ="party.jpg"
image grad ="grad.jpg"
image caf ="caf.png"
image study_room = "study_room.jpg"




# The game starts here.

label start:

    # Show a background. This uses a placeholder by default, but you can
    # add a file (named either "bg room.png" or "bg room.jpg") to the
    # images directory to show it.

    scene college_campus

    # This shows a character sprite. A placeholder is used, but you can
    # replace it by adding a file named "eileen happy.png" to the images
    # directory.

    show Alita

    # These display lines of dialogue.

    e "Wow, I’m finally here. College life, here I come!"

    menu:
        "Meet the Roomate":
            e "I should go meet my roommate, Nyle!" 
            jump meet_roommate 
 
        "Go to the Cafeteria Alone": 
            e "I’ll grab breakfast alone and explore the campus." 
            jump meet_ryan 

label meet_roommate: 
    scene dorm
    show Nyle 
    l "Hi, I’m Nyle! Nice to meet you." 
    e "Hey, I’m Alita. Let’s get to know each other better!" 
    l "I just got invited to this party. Do you want to come with me?"
    jump party_invite_n
    hide Nyle
    
 
label meet_ryan:
    scene caf
    show ryan 
    r "Hey, are you new here? I’m Ryan." 
    e "Yeah, I just arrived. Nice to meet you!" 
    r "I'm having this party tonight. Do you want to come?"
    jump party_invite_r

  #  e "Once you add a story, pictures, and music, you can release it to the world!"

label party_invite_r: 
    #e "I’ve been invited to a party this weekend." 
 
    menu: 
        "Go to the Party": 
            e "Yea, I'll definetely be there. Could I grab your number and you send me the address? " 
            r "Of course, let me see your phone."
            hide ryan
            jump party_time2
 
        "Skip the Party to Study": 
            e "I really need to study for the exam, so I don't think I can go." 
            r "It's okay I understand. I'll see you around."
            jump study_time1

label party_invite_n: 
    #e "I’ve been invited to a party this weekend." 
 
    menu: 
        "Go to the Party with Friends": 
            e "I think I’ll go with Nyle and meet some new people!" 
            jump party_time1 
 
        "Skip the Party to Study": 
            e "I really need to study for the exam, so I’ll skip the party." 
            jump study_time1
 
label party_time1: 
    scene party
    show Ben 
    a "Hey, my name is Ben, I'm one of Nyle's friends. How's your college experience going so far?" 
    e "It's okay so far I have really done much yet."
    a "Well if you want to, we can eat at the caf tomorrow and I can show you around"
    e "* I still have an exam though, what should I do?*"
    menu:
        "Go to Caf With Ben":
            e "Okay! that's perfect, I'll meet you there at 2 tomorrow"
            jump ben_end_caf
        "Study for Exam":
            e "I still need to focus on my studies first. But can I have your number just incase I finish early."
            a "Yea, of course. Just text me if have some free time."
            jump study_time2

    #e "Thanks, Ben! This is so much fun!" 
   # jump romance_choice 

label party_time2: 
    scene party
    show ryan
    r "Glad you could make it to the party, Alita!" 
    e "Thanks, Ryan! This is so much fun!" 
    jump romance_choice 

label study_time1:
    scene study_room
    show Alita
    e "I can't afford, to spend time on other things, I have to pass all my classes."
    jump end_2

label study_time2: 
    scene study_room
    show Alita
    e "I stayed home to study. It's a little lonely, but I feel good about the exam." 
    e "Maybe, I should ask Ben if he still wants to grab food, even though its late"
    menu:
        "Study More":
            e "There's no harm in studying more, I need to maintain my GPA"
            jump end_2
        "Call Ben":
            a "Hey, Alita what's up?"
            e "I just found some free time and wondered if you wanted to hang out."
            a "Yea of course, I'll meet you in front of the main building in an hour."
            hide Alita
            jump ben_end_fb


label romance_choice: 
    e "*I’m starting to like Ryan, but should I focus on my studies or go after him?*" 
 
    menu: 
        "Ask Ryan Out": 
            e "*I think I’ll ask Ryan to study with me.*" 
            jump date_time 
 
        "Focus on Studies First": 
            e "I’ll wait. I don’t want to get distracted." 
            jump study_focus 
 
label date_time: 
    scene college_campus
    show ryan
    e "Hey, do you wanna study together. I've seen you in some of my classes."
    a "I’d love to study with you, Alita!" 
    e "Great! Let’s make it a study date." 
    jump end_1
 
label study_focus:
    show Alita
    scene dorm
    e "I focus on my studies and do well on the exam. But I wonder what could’ve been with Ryan." 
    jump end_3

label ben_end_fb:
    scene college_campus
    show Ben
    a "Hey, Alita I'm happy you called."
    e "Me too, what's the plan for today?"
    a "It's a surprise but I'm sure you'll like it."
    return

label ben_end_caf:
    scene caf
    show Ben
    a "Hey, Alita how are you doing?"
    e "I'm doing pretty well, I'm happy I got some stuyding in."
    a "That's great, do you want to go grab some food."
    e "Yea, that sounds great let's go."
    hide Ben
    scene college_campus
    show Alita
    e "I ended up dating Ben, and we had a great time together. College life is perfect!"
    return

label end_1: 
    scene grad
    show grad_alita
    e "I ended up with Ryan, and we dated all throughout college. I'm so happy I asked him out that day!" 
    return 
 
label end_2: 
    scene grad
    show grad_alita
    e "I focused on my studies and graduated with great results. I’m proud of what I accomplished!" 
    return 
 
label end_3: 
    scene college_campus
    e "I had a lot of fun and learned a lot. Even though things didn’t work out with Ryan, I’m excited for the future!"
    # This ends the game.

return

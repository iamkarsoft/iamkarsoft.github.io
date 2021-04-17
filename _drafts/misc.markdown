---
title: misc
layout: post
date: 
categories: tag tag
---
Listen
Tell us about your business. We'll assist you in the process of identifying your needs

2
Think
Understand the proper way to digitalize your processes and operations

3
Document
Write down the project's technical specifications in a shared platform where you have access too.

4
Develop
Build your custom crafted solution in a transparent way. Get constant feedback from you

5
Test
Enter the testing phase and adjust the last details.

6
Launch
Get your new application into production

===============================================================
what we do
We develop through agile software development methods, targeting the intersection between customer needs and business goals, balancing aesthetics and functionality. 
We are experienced in REST APIs, Real-Time Search Engines, Single Page.

Applications and Content Management Systems.
 With our 360 degrees approach we integrate requirements gathering, analysis, design, development, testing, deployment, implementation and support for all our solutions.


=================================================================


   <div class="flex items-center justify-center my-5 space-x-4">
        <div class="h-px bg-gray-300 w-36"></div>
        <p class="text-md text-gray-80000">or</p>
        <div class="h-px bg-gray-300 w-36"></div>
      </div>
      
      
      5 0 * * * php /var/www/edwuma.wor
k/public_html/artisan schedule:run >> /dev/null 2>&1


As a web developer, I specialise in the Laravel Framework and love the freedom it gives me to build things quickly.
 My web development skills extend to frontend aspects of web development including JavaScript and Vue, 
 LESS/Sass/CSS, as well as designing databases and building applications that can scale.

=========================================================================

 0:00​ - Intro & Slides
7:17​ - User Generator Mini Project (CDN)
21:35​ - Vue CLI Setup
24:30​ - Files, Dev Server & Cleanup
28:22​ - Global Styles
29:06​ - Header Component
30:44​ - Component Props
32:06​ - Button Component
35:25​ - Events
36:09​ - Task Data & created() Method
38:22​ - Tasks Component & v-for Loop
41:09​ - Single Task Component
44:34​ - Dynamic Classes
45:53​ - Emit Events (Delete Task)
52:14​ - Toggle Reminder
56:20​ - AddTask Component & v-model
1:04:57​ - Toggle Form & Template Conditionals
1:11:20​ - Building For Production
1:13:33​ - JSON-Server Setup
1:17:18​ - Refactoring to Use The Backend
1:30:48​ - Implementing the Router
1:48:23​ - Restrict a Component to a Route
=====================================
Halo, Battleborn, Star Wars: Battlefront II, Black Ops 3

================
Minimum viable product
Complete solution
Business process optimization
Brief advice on architecture and technologies

=======================
I am a self-starter, a leader, and most importantly a team player. I've had the pleasure of working for a start-up from infancy to launch and now serving over 1,000 users and counting. Throughout that journey, I went from being an intern to a full-time Software Engineer and finally to leading a team of 3 Software Engineers. During my time at Cashaam, I successfully built, maintained, and upgraded 3 different e-commerce web applications helping small businesses both in the United States and in Nigeria.

Specialties:
• Ability to quickly learn new skills and programming languages, problem-solving, responsive design principles, and Model View Controller (MVC) methods of organizing code.
• JavaScript, React, Next Js, Node.js, Express.js, HTML5, CSS3, PostgreSQL, Firebase, Python, Django, jQuery, AJAX, Bootstrap and Git/GitHub. 
=====================


### Google function for saving event in calendar

```
    public function store(Request $request, Event $event, Google $google, Calendar $calendar, UserSocial $userSocial, $optionalParams = []) {

        $validated = $request->validate([
            'title' => 'required',
            'calendar_id' => 'required',
            'datetime_start' => 'required|date',
            'datetime_end' => 'required|date',
        ]);

        //getting socialite details of user
        $user = $userSocial->where('user_id', auth()->user()->id)->first();

        // assigning request inputs to variables
        $calendar_id = $validated['calendar_id'];
        $title = $validated['title'];
        $start = $validated['datetime_start'];
        $end = $validated['datetime_end'];

        //parsing dates through carbon
        $start_datetime = Carbon::parse($start)->format('Y-m-d H:i:s');
        $end_datetime = Carbon::parse($end)->format('Y-m-d H:i:s');

        // connecting to calendar service and calendar event
        $cal = $google->connectUsing($user->token)->service('Calendar');
        $google_event = $google->connectUsing($user->token)->service('Calendar_Event');

        //setting title data
        $google_event->setSummary($title);

        // setting event start date
        $start = $google->connectUsing($user->token)->service('Calendar_EventDateTime');
        $start->setDateTime(Carbon::parse($start_datetime)->toAtomString());
        $google_event->setStart($start);

        // setting event end date
        $end = $google->connectUsing($user->token)->service('Calendar_EventDateTime');
        $end->setDateTime(Carbon::parse($end_datetime)->toAtomString());
        $google_event->setEnd($end);

        // saving event on google calendar
        $created_google_event = $cal->events->insert($calendar_id, $google_event);

        //store event in our database
        $event = new Event;
        $event->title = $request->input('title');
        $event->calendar_id = auth()->user()->email;
        $event->user_id = auth()->user()->id;
        $event->datetime_start = $request->input('datetime_start');
        $event->datetime_end = $request->input('datetime_end');
        $event->save();

        if ($event->save()) {
            return redirect()->route('events', [
                'error' => false,
                'messages' => [
                    'type' => 'success',
                    'text' => 'Event Created',
                ],
            ]);
        }

        return Inertia::render('User/TestEventCreation', [
            'error' => true,
            'messages' => [
                'type' => 'failed',
                'text' => 'Something went wrong',
            ]]);

    }

```
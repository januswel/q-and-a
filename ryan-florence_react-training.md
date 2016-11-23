| username | question |
| ---: | --- |
| Gabe | hey all welcome to the Q&A! thanks for being here @ryanflorence |
| **ryanflorence** | Woah, I've never had to be silent for that long before... |
| Gabe | lol |
| **ryanflorence** | my pleasure! |
| brandon | welcome :smile: |
| aaronjensen | **how do you `<Match exactly pattern="">` (the parent match only, no sub /foo)** |
| **ryanflorence** | @aaronjensen  I don't know, can you visit that url in a browser? |
| aaronjensen | @ryanflorence the analog to matching pattern="foo"... which could match /bar/baz/foo if the parent match was /bar/baz/:id?. |
| aaronjensen | I want to match when :id is blank |
| **ryanflorence** | @aaronjensen open an issue and we can try to figure it out. @mjackson has been working on the <Link to/> prop and will support "relative urls" to the matched location, which might be what you're talking about |
| aaronjensen | Will do, thanks. |
| sean | **More React30 episodes when?** |
| **ryanflorence** | @sean oh man ... we're so booked lately and have stepped up our OSS game so it's hard to find time for it all. We have a whole list of folks and topics we want to cover. I have no specific dates when we'll do the next one, but ... soon? |
| EvNaverniouk | **React Router v4 looks very cool. What's the idea behind the version 3 beta? Why not jump right into the work being done on version 4?** |
| **ryanflorence** | @EvNaverniouk version 3 is just version 2 w/o deprecation warnings. @timdorr is working on getting that shipped so he'd be better to ask |
| antmdvs | **How do you feel about stateless functional components? You used createClass() in your last presentation. Do you prefer that over ES6 classes and SFCs?** |
| **ryanflorence** | @antmdvs so there are a lot of ways to create a component right? even the old-school 2006 "module pattern" works as a component |
| **ryanflorence** | in our workshops we switched to classes about a year ago |
| **ryanflorence** | it was a TRAIN WRECK! |
| **ryanflorence** | because understanding JS context is hard |
| **ryanflorence** | and so people had a really hard time getting through the exercises |
| **ryanflorence** | so then it gets us really introspective |
| **ryanflorence** | if this is a pain in the neck in a workshop, what about in your actual code w/ your team? |
| **ryanflorence** | I dunno! |
| **ryanflorence** | but anyway, we still use createClass in our workshops but we may be switching to classes because of create-react-app's support of "class property declarations" |
| **ryanflorence** | since that's getting a lot of attention... |
| antmdvs | are there any actual benefits to SFC besides terseness? |
| **ryanflorence** | seems like it's okay to use the "not-yet-javascript" that it uses |
| **ryanflorence** | one sec |
| maxdeviant | That basically answered my question :smile: |
| **ryanflorence** | I'll get there! |
| mattste | **Does v4 have a solution for passing props to a component besides HoC? It'd be nice to do something like ** |
| mattste | `<Match pattern="/myprofile"><Profile type="personal" /></Match><Match pattern="/mypubicprofile"><Profile type="public" /></Match>` |
| mattste | Passing component to `<Match />` seems like holdover from the old way of doing things instead of rendering it's children. I may be thinking about this wrong. Awesome job to you and the team on this release. It feels a lot better. |
| threepointone | @mattste `<Match pattern="/myprofile" render={x => <Profile type='personal' {...x} />}/>` |
| threepointone | [sorry, jumped in] |
| mattste | @threepointone thanks, but That still makes me believe my comment still stands that passing a render prop isn't the component-based path v4 strives to be. It just feels odd |
| **ryanflorence** | okay, @mattste: |
| **ryanflorence** | looks up a gist |
| **ryanflorence** | struggles to find the gist |
| **ryanflorence** | FOUND IT! :tada: |
| **ryanflorence** | https://gist.github.com/ryanflorence/a301dc184f75e929a263dc1e80399a28 |
| **ryanflorence** | @mattste ^ read that, that's why we don't do the "children as elements" in the Match API |
| **ryanflorence** | so class property declarations aren't JS yet, so we are hesitant to use them in workshops, but in my own code I use them and that's the only way I can bear to use ES classes because they make "auto binding" really nice |
| **ryanflorence** | as for SFC |
| **ryanflorence** | those are basically just really cool templates, right? |
| **ryanflorence** | so if I don't need the lifecycle hooks, and just need to tuck some "markup" away, a SFC is great |
| **ryanflorence** | so I use classes when I need hooks and state, SFC when I don't |
| Foxhoundn | I think that's a hard thing for beginners to process |
| Foxhoundn | There are Components, PureComponents and Stateless components |
| Foxhoundn | We have moved to using only Stateless components with recompose and I have way less gray hair |
| mattste | Okay, thanks :smiley: |
| CPT | **Is there planned support for param default values?** |
| **ryanflorence** | @CPT  this.props.params.foo || 'foo' seems like enough? |
| CPT | That makes components less reusable** |
| **ryanflorence** | `<Match render={(props) => <Component params={addDefault(props.params)}/>}/>` |
| **ryanflorence** | wrap that up in a MatchWithDefaults component |
| **ryanflorence** | BOOM bob's your uncle |
| CPT | thanks |
| timarney | **outside of classes what's the most common point of confusion people have in your workshops?** |
| **ryanflorence** | hmm ... hard to pick "one thing" |
| **ryanflorence** | people struggle with just JavaScript itself |
| **ryanflorence** | like, not knowing there's [].map and [].filter |
| **ryanflorence** | how to mess around w/ objects in JS |
| **ryanflorence** | React really throws JS back in your face |
| **ryanflorence** | and lots of people haven't done much ... uh ... "real work" with JS before |
| timarney | Interesting |
| **ryanflorence** | the other thing is probably what a valid JS expression is |
| **ryanflorence** | we can say "once you do {} in JSX, any valid expression can go there, because it's really just an argument to React.createElement" |
| **ryanflorence** | but most of us haven't done very much w/ JS expressions before React |
| **ryanflorence** | but the questions we get in a workshop are rarely react related, usually they're JS questions :joy: |
| timarney | Ya I guess timing of ES2015 + React |
| aaronjensen | **Why isn't render children it seems more common than what is currently used for children** |
| **ryanflorence** | children in Match will always render if it matches or not |
| **ryanflorence** | check out the animation demo |
| aaronjensen | yes, i know I was just curious as to why the render prop and the children prop aren't reversed since so far the render prop seems to be used more and the children prop is more "natural" |
| **ryanflorence** | we decided htat since one rendred conditionally and the other was always, that children made more sense to "always render" since you typically expect that API. |
| aaronjensen | got it, thanks. |
| sandeshsoni | **scenario : I have login container that does part of login. After login, I want to switch to dashboard container. how do I do this? I have react router. If question is incorrect, suggest a post/gist that looks useful.** |
| **ryanflorence** | https://react-router.now.sh/auth-workflow |
| EvNaverniouk | **If you could wave a magic wand and fix one thing about the JS/React community, what would it be?** |
| **ryanflorence** | Aside from normal social justice problems that are just problems w/ the whole world, I guess I don't know what's broken! I love both JS and React communities, so much exploring, so many ideas. It's a blast to be a JS developer today. |
| **ryanflorence** | so I would leave the wand in its case probably |
| antmdvs | would you like a magic wand to answer all these questions? |
| antmdvs | i noticed @en_js went Twitter-silent after that :smiley: |
| antmdvs | **This may be a sore subject, but I saw a lot of FUD around the RRv4 preview and Relay (lack of static route config?). Can you talk to (or point me to) the latest developments on that discussion? I'm not using Relay right now, but keeping an eye on it.** |
| **ryanflorence** | first of all, you can use `<Relay.Renderer>` anywhere in a router v4 app and it just works™ |
| **ryanflorence** | heh, well, now relay has to solve it instead of us |
| **ryanflorence** | that was actually really liberating for us to not be int he game of "knowing what to render before we render" |
| antmdvs | good deal |
| **ryanflorence** | here's a repo I hope people who are interested in a static route config analysis will get involved: https://github.com/ReactTraining/react-router-addons-routes |
| antmdvs | :thumbsup: |
| Mohan | **Thank you for then awesome library. RR4 is turning out to be really cool. Any way RR4 can support code splitting like predecessor?** |
| **ryanflorence** | it doesn't have to, you can code split anywhere you want. The react-router.now.sh website uses code splitting with a component called <LoadBundle/> |
| **ryanflorence** | here's a cool example by andrew clark: https://gist.github.com/acdlite/a68433004f9d6b4cbc83b5cc3990c194 |
| threepointone | @Mohan https://github.com/ReactTraining/react-router/blob/v4/website/routes.js https://github.com/ReactTraining/react-router/blob/v4/website/components/LoadBundle.js |
| threepointone | working on PRPL ootb as we speak |
| Mohan | Thank you |
| antmdvs | code splitting = lazy loading comps for routes? |
| rgdelato | **I love your workshop (attended one on my own dime early this year), but it's very limited to specific times/locations ...do you have any plans to teach in an online format, or does that lose too much of the magic?** |
| **ryanflorence** | THANK YOU!! |
| brandon | I would be interested in an online course from you as well |
| **ryanflorence** | we've done 3 private "online workshops" and they're pretty good |
| **ryanflorence** | still toying w/ it before we do them publicly |
| **ryanflorence** | we also have some online content in the works |
| **ryanflorence** | self-paced stuff |
| **ryanflorence** | the trick w/ online live workshops is time zones, when do you take a lunch break?! ha! |
| **ryanflorence** | (and me not feeling like I'm talking to myself for 7 hours straight() |
| rgdelato | Thank you! I was in the process of changing jobs and I knew I wanted to work with React, so your workshop was wonderful :smile: |
| **ryanflorence** | which workshop was it? |
| rgdelato | was in Carlsbad, in February, I think |
| **ryanflorence** | ooh, with the fancy stage! |
| **ryanflorence** | https://cdn.discordapp.com/attachments/193117606629081089/231127237829591041/unknown.png |
| **ryanflorence** | so fancy! |
| rgdelato | yep, that was it! so fancy |
| rgdelato | drove down from LA |
| **ryanflorence** | @mjackson lives there now |
| **ryanflorence** | carlsbad |
| **ryanflorence** | loved it so much |
| antmdvs | **On the converse, are you still "touring?"** |
| antmdvs | I work for a F500 company in Jacksonville, FL and my .NET team is considering adopting React for a large Silverlight app conversion |
| **ryanflorence** | yep, we've just had a lot of private workshops lately |
| **ryanflorence** | before the year is up we'll be in SF, Boston, Phoenix, and maybe NYC for some public workshops |
| brandon | **What interests you in the React ecosystem beyond RR?** |
| iamdustan | :wave: |
| **ryanflorence** | hmm |
| **ryanflorence** | I dont' get to spend any time w/ them, but I love all the custom renderers |
| **ryanflorence** | like @iamdustan's react hardware |
| **ryanflorence** | I like thinking about describing any system with components |
| iamdustan | :heart_eyes: I came in at the right time! |
| **ryanflorence** | haha yeah! |
| **ryanflorence** | I also like figuring out the optimal way to deliver an app over the network |
| **ryanflorence** | like PRPL, and service worker app shells, server rendering, etc. |
| **ryanflorence** | like what will be the standard practice in 5 years for delivering these big apps over a network? |
| **ryanflorence** | hard to tell right now, but there are so many cool things happening |
| **ryanflorence** | I've been chasing those questions for like 4 years, fun to see some better answers than some terrible ruby scripts I was writing |
| **ryanflorence** | speaking of PRPL, this guy @threepointone is working on that w/ router v4 |
| **ryanflorence** | where's a link to your work? |
| **ryanflorence** | or tweets at least? |
| threepointone | this is initial work https://github.com/threepointone/react-modules, more as it happens |
| **ryanflorence** | that's the beauty of composable routing, you can compose! |
| threepointone | **yo ryan, how and when did you and michael get 'together'?** |
| iamdustan | **What would you most like to see changed or done next with React?** |
| antmdvs | **Our app is going to be `<input/>` dense. Any advice for authoring complex forms in react? What do you do? Any libs or just vanilla?** |
| **ryanflorence** | okay I'm going to tackle sunil's question about me and michael |
| **ryanflorence** | then @iamdustan, then @antmdvs |
| Gabe | :tada: |
| **ryanflorence** | EVERYBODY ELSE COOL IT :stuck_out_tongue_closed_eyes: |
| Gabe | hahaah |
| **ryanflorence** | plays some gentle jazz guitar |
| **ryanflorence** | so there I was |
| **ryanflorence** | feeling like a foreigner at mountain west ruby conference in utah |
| **ryanflorence** | one of my co-workers went to BYU with @mjackson |
| **ryanflorence** | and was like "hey Ryan, come meet my friend, he's another JavaScripter here" |
| **ryanflorence** | and then I met him, and somehow we talked about AMD cause I was way into back then |
| **ryanflorence** | from there I was the AMD-guy to him |
| **ryanflorence** | and we were just twitter acquaintances |
| **ryanflorence** | then we both ended up doing ember, he hired me to help him get some code going w/ his startup from a few years ago |
| **ryanflorence** | it was like a month or two of work |
| **ryanflorence** | then we started tweeting at each other about react |
| **ryanflorence** | I showed him my 100 line hilarious router prototype |
| **ryanflorence** | he got involved |
| **ryanflorence** | then we both spoke at the first react conf |
| **ryanflorence** | both had people asking us to come do consulting/training for their teams |
| **ryanflorence** | and decided to partner up and start reacttraining.com |
| **ryanflorence** | I love working with him |
| **ryanflorence** | we balance each other really well |
| **ryanflorence** | I'm a dirty hacker and he's a thoughtful engineer |
| **ryanflorence** | so that's the story :smile: |
| **ryanflorence** | if you ever want to start a company, I highly suggest getting a partner, I can't imagine doing this alone. |
| threepointone | :smiley: great answer, thank you! |
| **ryanflorence** | > What would you most like to see changed or done next with React? |
| **ryanflorence** | not sure, really. fibers looks interesting, streamed rendering is going to be cool |
| **ryanflorence** | we do some crazy hacks with router v4 to get sibling `<Match/>` `<Miss/>` to "know about" each other |
| **ryanflorence** | I'd love to figure out a way to establish relationships between siblings/descendants the way a `<form>` `<button>` and `<input>` all kind of work together |
| **ryanflorence** | like ... |
| **ryanflorence** | when you key down "enter" in a text input |
| **ryanflorence** | if there's a button in the form, it'll submit |
| **ryanflorence** | but if there isn't a button in the form (and there's at least another non-button input) then it won't submit! |
| **ryanflorence** | that's a lot like Match and Miss |
| **ryanflorence** | so right now we can't server render a Miss and get the checksum to match up on the client |
| **ryanflorence** | but, it's a miss so... hopefully people aren't too bothered by that |
| **ryanflorence** | sebastian says he likes the match miss api and wants to figure out a way to support it more officially too, so we'll see what happens there |
| **ryanflorence** | would also love to see it get faster |
| **ryanflorence** | too many apps need shouldComponentUpdate |
| **ryanflorence** | which totally bums me out |
| **ryanflorence** | it's a huge buzz kill for the "always rerender" paradigm of react |
| **ryanflorence** | > Our app is going to be `<input/>` dense. Any advice for authoring complex forms in react? What do you do? Any libs or just vanilla? |
| **ryanflorence** | I get this question a lot at workshops |
| **ryanflorence** | forms are hard, no matter where you go, and while React makes them easier for me to manage w/ it's declarative model, it's a LOT of code. |
| **ryanflorence** | but no, I have no suggestions there. |
| TheZanke | holy cow, am I really caught up?? |
| antmdvs | :frowning: |
| **ryanflorence** | it's tempting w/ forms to want to abstract like crazy |
| **ryanflorence** | but just make sure you don't "take rendering away" in those abstractions |
| **ryanflorence** | that's my problem with all the form libs I've looked at, they do the rendering |
| **ryanflorence** | and so you always end up w/ some limitation and I hate saying "no" to things |
| **ryanflorence** | I hven't looked in a while though, so maybe there's some awesome ones now |
| antmdvs | i'd like something to generate forms, but i don't want to maintain another schema for form meta |
| **ryanflorence** | > holy cow, am I really caught up?? |
| **ryanflorence** | man, these questions are getting weird |
| **ryanflorence** | Yes. |
| **ryanflorence** | You are caught up. |
| **ryanflorence** | :joy: |
| TheZanke | Hahahaha, I just scrolled all the way up to read past questions and thought there was no way I'd catch up.. I was wrong! :tada: |
| antmdvs | **You growing your beard back?** |
| **ryanflorence** | https://cdn.discordapp.com/attachments/193117606629081089/231132644937695232/Photo_on_9-29-16_at_12.18_PM_2.jpg |
| antmdvs | niiiiice |
| TheZanke | it's the not bad face |
| **ryanflorence** | my wife is happy |
| **ryanflorence** | she HATED my face. |
| antmdvs | a little bit De Niro |
| TheZanke | I see it |
| **ryanflorence** | are there other questions I've missed? |
| Gabe | I think you are good |
| antmdvs | **When's your next conf talk?** |
| **ryanflorence** | no talks coming up |
| TheZanke | **This isn't router related.. but... Thunks or Sagas?** |
| sean | or observables :stuck_out_tongue: |
| antmdvs | @TheZanke https://medium.com/@jeffbski/where-do-i-put-my-business-logic-in-a-react-redux-application-9253ef91ce1#.x4awa4007 |
| antmdvs | so many options |
| **ryanflorence** | > This isn't router related.. but... Thunks or Sagas? |
| **ryanflorence** | man, I barely use thunks in redux |
| **ryanflorence** | someAction(this.props.dispatch) |
| **ryanflorence** | like ... why not just pass dispatch in myself? |
| **ryanflorence** | I dunno |
| **ryanflorence** | I have no good opinion on thunks v. sagas. I would say, explain to the newest dev on the team how to use each and then whichever sounds less crazy, go with that! |
| TheZanke | If I did that, I'd be using jquery, not react |
| **ryanflorence** | ha! |
| jmurzy | **Hey! re: your getting started with RN tweet a couple day ago. Do you have any intentions to support RN with v4?** |
| **ryanflorence** | @jmurzy it's already supported with `<MemoryRouter/>` |
| **ryanflorence** | looks up an article about it |
| jmurzy | Oh dude. You guys keep saying that but no that's not enough haha v3 had memory history as well. :joy: |
| **ryanflorence** | this dev just busted it out w/o us even knowing, like the day after our announcement of the preview: https://medium.com/@jschloer/react-router-v4-with-react-native-5f2005ab2a72#.tz0wpwsyb |
| jmurzy | I am talking about transitions etc |
| jmurzy | Have you see my comment reply to that? |
| **ryanflorence** | "support" and "deep integration" are kind of different |
| jmurzy | Oh then I guess I meant deep integration :yum: |
| **ryanflorence** | but I'm sure somebody will figure that stuff out, and if not, then perhaps our routing model isn't satisfactory for some use-cases on mobile |
| **ryanflorence** | too many conversations around that for me to remember who, but I know somebody is working on figuring out how to do the native transitions w/ the new api |
| jmurzy | I am only asking cuz I am working on it but if you guys are I don't want to waste time |
| jmurzy | Especially if it's going to live in the core |
| **ryanflorence** | oh, maybe it's you! |
| **ryanflorence** | ha, no, we wont' be doing that ourselves any time soon. |
| jmurzy | Gotcha. Thanks! |
| **ryanflorence** | we may have like react-router/dom and react-router/native or something for stuff like Link between platforms |
| **ryanflorence** | but I suspect that code for native will come from the community and not us, we haven't done a whole lot with native |
| jmurzy | Yeah that's cool. Do you want me to send in a PR for Link? |
| **ryanflorence** | absolutely! |
| jmurzy | Great will do. |
| antmdvs | **What's the craziest/awesomest example of `<Rethink stop={false} />` that you've seen from the community? (that's a reference to Ryan's last talk)** |
| **ryanflorence** | oooh |
| **ryanflorence** | basically anything @threepointone and ken wheeler have been doing |
| antmdvs | i'm not familiar |
| **ryanflorence** | Sunil's got this express server, that's booted up by rendering to the DOM in electron a `<Server/>` |
| **ryanflorence** | @threepointone link this fine gentleman |
| **ryanflorence** | https://twitter.com/threepointone/status/769977693517520896 |
| **ryanflorence** | rather: https://twitter.com/threepointone/status/769932779790348288 |
| antmdvs | kewl |
| bkonkle | **When you're conducting React training, what are some of the most common things that trip up people relatively new to JavaScript?** |
| **ryanflorence** | we have a pre workshop survey that dumps some "new JS" in front of them |
| **ryanflorence** | and says "does this look like JavaScript?" |
| **ryanflorence** | scale of 1-5 |
| **ryanflorence** | a year ago, answers were mostly left of 3 |
| **ryanflorence** | lately it's always right of 3 |
| **ryanflorence** | so people are catching up to the language |
| **ryanflorence** | but arrow function syntax mixed with JSX is probably the hardest |
| bkonkle | \o/ |
| **ryanflorence** | I think mostly because their editors dont' know what the heck to do about it |
| **ryanflorence** | destructuring sometimes doesn't click very quickly either. |
| Mohan | **Have you ever tinkered with elm?** |
| **ryanflorence** | yeah, I built a little "people counter" with it |
| **ryanflorence** | was kinda fun, I didn't ever get used to the syntax |
| **ryanflorence** | every task was really hard for me |
| **ryanflorence** | mostly copy/paste, tweak and not really understanding what I was doing, but it was fun anyway! |
| **ryanflorence** | in other words, I didn't transcend the lowly languages like I was supposed to :frowning: |
| antmdvs | it takes a trained eye bc destructuring can look exactly like object property shorthand notiation, just on the other side of = |
| Gabe | any other questions for @ryanflorence? |
| Gabe | we have 25 minutes left |
| bkonkle | **Static typing - worth the effort?** |
| **ryanflorence** | I'm not qualified to answer that |
| **ryanflorence** | been in JS my whole life |
| bkonkle | /nod |
| **ryanflorence** | did a thing w/ go, I was amazed at what my editor could tell me! |
| **ryanflorence** | I was told: |
| **ryanflorence** | "if it compiles, it'll work" |
| **ryanflorence** | turns out, that just meant I couldn't get it to compile |
| **ryanflorence** | :stuck_out_tongue: |
| bkonkle | :smile: |
| bkonkle | PureScript felt the same way for a while. |
| antmdvs | **Bro.doYouEven('Redux')?** |
| **ryanflorence** | Do I redux? I like it for shared or persistent state, but I hesitate to relegate React to nothing but a cool way to generate markup. |
| Mohan | **What's the most impressive thing you've seen in programming outside of js?** |
| **ryanflorence** | I watch the spaceX rockets land on a boat and realize I'm an idiot. |
| bkonkle | **Do you see any potential successors to React on the horizon?** |
| **ryanflorence** | I dunno, depends on what the people decide about components and state |
| **ryanflorence** | if we go the elm/redux/om way of globalizing state, then it'll probably get replaced by something that's just a smart markup renderer |
| bkonkle | Yep, that makes sense. |
| **ryanflorence** | if we don't, then React has a long plateau |
| **ryanflorence** | I was talking to somebody at adobe |
| **ryanflorence** | forgot who |
| **ryanflorence** | but she has been following programming trends for 20 years or so |
| **ryanflorence** | she predicted angular's rise |
| **ryanflorence** | and when react came out, she said something like "it's not going to peak as high as angular, but it's going to plateau for a LOT longer" |
| **ryanflorence** | I think that sounds about right to me |
| bkonkle | Wow, prescient! |
| **ryanflorence** | I'm really happy I spelled plateau correctly |
| Gabe | lol |
| bkonkle | Ha! I think you're right about React not being the first choice anymore for global state devotees like myself. |
| bkonkle | I think eventually something optimized for that case will come out. |
| Gabe | **You still rocking that Brad Pitt desktop/login screen?** |
| **ryanflorence** | hahaha |
| bkonkle | lol @Gabe ! |
| **ryanflorence** | when did you see that? |
| **ryanflorence** | I gotta find that |
| **ryanflorence** | https://www.minnpost.com/sites/default/files/images/articles/BradPittWaving640.jpg |
| Gabe | you sat next to me at react conf... and I asked you if that was Brad Pitt... cause it was blurry |
| **ryanflorence** | "Hey Ry! I saved you a seat!" |
| **ryanflorence** | makes me feel so good. |
| bkonkle | Aww, but the bloom has fallen off of that rose. :sob: |
| bkonkle | (the rose being Brad Pitt) |
| Vinnymac | **How do you find time to manage life/family, work, and OSS?** |
| **ryanflorence** | I don't! |
| **ryanflorence** | my wife is always angry, my kids think I'm a jerk, and we ruined everybody's life with router v4 |
| Vinnymac | hahahaha |
| **ryanflorence** | seriously though |
| **ryanflorence** | I'm really fortunate to be in a position to have a job like I have |
| **ryanflorence** | when we're flying and at hotels, we get uninterrupted time to work on code |
| **ryanflorence** | and it pays the bills well enough to take vacation and stuff w/ my family |
| **ryanflorence** | so when it's flexible, it's really flexible. but it's hard to balance for sure. |
| **ryanflorence** | I had no idea how much paperwork running a business required |
| Vinnymac | Launching rockets can end lives, idk if router v4 will. But it is good to know it is possible to juggle so much, I hope to achieve that level of stress management. |
| **ryanflorence** | need a physical thing to balance the stress |
| **ryanflorence** | I used to play on 2 indoor soccer teams, but that doesnt' work w/ my travel anymore |
| **ryanflorence** | so I started doing P90X3 and it's a great way to balance the sitting-and-thinking-and-stressing way of life |
| **ryanflorence** | (FYI this is my new background: http://ryanflorence.com/i-heart-react.jpg) |
| Gabe | very nice @ryanflorence but you should bring back Brad for next react conf.. he is lonely |
| **ryanflorence** | for real |
| **ryanflorence** | for real |
| Vinnymac | Compiling/Transpiling/Updating === Workout Time |
| Vinnymac | A developers guide to a happy lifestyle by Ryan Florence |
| **ryanflorence** | :thumbup::skin-tone-3: |
| Gabe | Any other questions for @ryanflorence ? we have a few minutes before we end |
| rgdelato | **What's your current favorite React CSS solution?** |
| **ryanflorence** | jsxstyle |
| **ryanflorence** | https://github.com/smyte/jsxstyle |
| **ryanflorence** | the reason why is simple |
| **ryanflorence** | I know how to compose my UI with components |
| **ryanflorence** | and now i get to compose not just their content and behavior, but also their looks |
| **ryanflorence** | so I never switch gears from "JS" to "CSS" |
| **ryanflorence** | and when I refactor, I don't have to go find stuff from other files |
| **ryanflorence** | if I cut/paste some JSX, the styles come with it |
| **ryanflorence** | so it completely eliminates a whole set of tasks when writing code for me |
| rgdelato | thanks! I'll definitely look into it! |
| rgdelato | this was my first search result, lol: https://cl.ly/3W3r3W1l0X0y/Image%202016-09-29%20at%2012.53.09%20PM.png |
| **ryanflorence** | basically every CSS question becomes a component question, and i like the answers there :smiley: |
| **ryanflorence** | JSXStyle: the best version of your components |
| **ryanflorence** | I like it |
| Gabe | haha nice.... got time for 1 or 2 more q's... |
| codiro | @ryanflorence what do you mean actually under "long plateau"? will react stand straight for a long time? |
| **ryanflorence** | yeah, I think it's seen a ton of adoption |
| **ryanflorence** | so it has grown tremendously |
| **ryanflorence** | eventually it'll stop growing |
| **ryanflorence** | but people who picked it before continue to pick it again |
| **ryanflorence** | so after it peaks, we'll see years of "boring" usage |
| antmdvs | **What if i want the URL to not reflect the route, i.e. keep it opaque for security reasons in a LOB?** |
| antmdvs | is that supported? |
| antmdvs | maybe i'm just being paranoid |
| **ryanflorence** | use MemoryRouter |
| antmdvs | gotcha |
| **ryanflorence** | no back button though |
| **ryanflorence** | but you can implement your own |
| **ryanflorence** | but sounds like you should rethink the data in your url :stuck_out_tongue: |
| **ryanflorence** | (also, what is a LOB?) |
| antmdvs | Line of business |
| **ryanflorence** | love those |
| Gabe | alright.. thats all the time we have... let's all thank @ryanflorence for answering all those questions!! |
| Gabe | we'll have a transcript up soon and we'll post it on twitter |
| sean | :clap: |
| antmdvs | Thanks, Ryan. That was awesome |
| **ryanflorence** | Thanks! |
| TheZanke | Thank you! |
| rgdelato | Thanks! |
| Gabe | thanks @ryanflorence :tada: :tada: |
| timarney | Thanks |
| antmdvs | Thanks, Ryan. That was awesome |
| antmdvs | You should have a canned response next time for the MJ story |
| antmdvs | :smiley: |
| **ryanflorence** | haha |
| bkonkle | Thank you! |
| threepointone | thanks ryan! |
| Gabe | if you all haven't seen the podcast Ryan is a part of... check it out: https://react30.com/ |

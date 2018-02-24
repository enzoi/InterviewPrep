# InterviewPrep

1. What have you learned recently about iOS development? How did you learn it? Has it changed your approach to building apps?

* I have brushed up fundamental iOS development concepts about how iOS apps should be structured. I learned it from an online class with multiple online resources. With a clear understanding of the architecture, I am comfortable with writing performant and clean codes.
* I have also learned AWS to compare with Firebase for real-time architectures and notifications. I learned it from AWS documentation, some online courses including YouTube channels. As I learn more development tools, I have a better understanding of what technology stack would work better for the app I am working on.

2. Can you talk about a framework that you've used recently (Apple or third-party)? What did you like/dislike about the framework?

* I have used Realm recently. I like its simple APIs and very fast compared to Core Data. It’s also thread-safe so no need to worry about it. Realm has offline first approach yet I can use the object online as well. What I didn’t like about it is that it’s still another dependency which I always try to minimize. Not like Firebase, there is no free tier for professional edition - only 30 days free trial is available and it doesn’t seem enough to test.

3. Describe how you would construct a Twitter feed application (here is an example of Udacity's Twitter feed) that at minimum can display a company's Twitter page. Please include information about any classes/structs that you would use in the app. Which classes/structs would be the model(s), the controller(s), and the view(s)?

* Model - I would use two structs for Model a) Tweet struct with 3 properties: user, message, createdAt, b) User struct with 4 properties: name, username, bio, profileImageUrl. 
* View - I would use two TableViewCells a) Tweet Cell with several properties: profile image view, message, buttons - like, reply, retweet, direct mention, b) User Cell with following properties: profileImageUrl, name, username, following button assuming the application has User page like the Twitter app.
* Controller - I would use a TableViewController to feed data from the network into the table view cells. For data source and network calls, I would create separate classes. 

4. Describe some techniques that can be used to ensure that a UITableView containing many UITableViewCell is displayed at 60 frames per second.

* Firstly, TableViewCell should be reused by dequeueReusableCell(withIdentifier:for:) method. Also, I would fetch data asynchronously so it doesn't block main UI thread.

5. Imagine that you have been given a project that has this ActorViewController. The ActorViewController should be used to display information about an actor. However, to send information to other ViewControllers, it uses NSUserDefaults. Does this make sense to you? How would you send information from one ViewController to another one?

* NSUserDefaults should not be used to pass data between view controllers. It is designed for storing user preferences or settings.
* There are many ways to pass data between view controllers. Among them, I would pass data forward when two view controllers are connected by segue and prepare(for:segue) method and backward by using unwind segue method if needed. Also, I would use a delegate/protocol pattern to pass data inside delegate method parameter. Tab bar controller or shared app state would be another option if applicable. However, I wouldn’t use a singleton (UserDefaults also work like a singleton) or notification (only consider when it is needed to pass data to multiple destinations). 

6. Imagine that you have been given a project that has this GithubProjectViewController. The GithubProjectViewController should be used to display high-level information about a GitHub project. However, it’s also responsible for finding out if there’s network connectivity, connecting to GitHub, parsing the responses and persisting information to disk. It is also one of the biggest classes in the project. Follow-up question:: How might you improve the design of this view controller?

* The view controller does too many things. I would create separate data source classes for both TableViewDataSource and CollectionViewDataSource. Instead of fetching data in viewDidLoad(), all networking related functions are called in the Classes to fetch data from GitHub. The view controller would be much easier to understand by doing only view related tasks here.

7. If you were to start your iOS developer position today, what would be your goals a year from now?

* First of all, I would like to see much more users who love new features I have experimented or prototyped. I would also like to influence decision-making process about all of the features on our product roadmap as well as detailed functional and technical requirements.

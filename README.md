# What I Learn

## 3 August 2025

Today, I worked on UI in GymCoach iOS and fixed a bug in the logic for deleting a template workout from the local database. The PlanView UI got better visuals for edited the set, rep, and weight values for an exercise. I updated the logic for showing the "add new exercise" button, which previously would not appear sometimes when a workout had no exercises. 

For the backend, the app would *sometimes* (but not always) crash when a template workout was deleted. I realized that the .delete method of PlanView's ViewModel was attempting to delete the same workout from persistent storage twice, causing a stale reference to a no-longer-existent template the second time deletion was attempted. I have rewritten the logic for deletion in PlanView.ViewModel and uncommented the line in the .delete method that was responsible for propagating the delete to a companion Apple Watch. I'd previously thought that that was the cause of the crash. 

Currently, two of the three main pages of the iOS app are MPV-ready. Those are the RecordView (for recording workout sessions) and PlanView (for planning workout sessions). Tomorrow, I will create a TimeKeeper class that will keep track of the inter-set timing. This is a core feature of the app that tells users how long it's been since their last completed set (a feature I've really needed at the gym). I will also move work on the AnalyzeView, where users will be able to view their weight progression for each exercise (e.g. bench press, leg press, etc.). 

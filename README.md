# Android-Practice

Writing an Android app could be hard if you did not have good practice.
However, this file is written for you to read if you want to write an Android application easily and you have some basic knowledge in writing an Android application.

The first thing you need is a set of good tools that could help you.

Good Tools:
====
1. ButterKnife
----
A very good view binder that can remove all the needs of findViewById().
Include the library and you will find it useful and easy to find a view object in your layout.
- ``compile 'com.jakewharton:butterknife:8.5.1'``
- ``annotationProcessor 'com.jakewharton:butterknife-compiler:8.5.1'``

Practices:
====
1. User defined Classes
----
- First, determine whether you wanted to store the object into database and whether you need to display the object in the GUI.
- If you need to store it in a database, create constant String value in the object class for database column title.
- If you need to display the object in the GUI, NEVER include the View field in your object class.
  - Create another ViewHolder class for the object class with the field you wanted to show ONLY.
  - Put all the setter into the view holder class but not the getter unless it require input from user.
  - This is because what we need to display could be information that was processed from the raw data.
  - If we do not separate into object class and view holder class, the programmer will tend to store more field in the object class and use up more memory space during the run time.
  
2. Model View Presenter Architecture
----
- First, separate an activity into 4 interfaces.
  - MvpView: Passive View layer API for the Presenter to call 
  - MvpVPresenter: Activity flows API for the interaction of user called from View. (Look at this to understand the program)
  - MvpMPresenter: API provided for model to call for updating View and notify methods.
  - MvpModel: Business logic of the program for Presenter to call;
- Button pressed method should be included in MvpView interface.
- Provide API that consume Exception and show it to the user to remove crashing.
- Methods in MvpModel can always throw Exception and MvpMPresenter should always catch the Exception and show it in View.
- Provide API that suite your programming style in the MvpModel interface.

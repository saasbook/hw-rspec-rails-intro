# Submission Instructions

You will be tested on both correctness and testability of your app. Deploy your app to Heroku using the same technique as in CHIPS 5.3 (you may need a force push!). You should set up the database as well, running the appropriate database setup commands on the Heroku server. Once you are confident the functionality works correctly on Heroku, submit the URI of your deployed app in a text file called `rottenpotatoes-url.txt` with no other contents.

**Please be careful** to use **http** and not **https**, that is, submit `http://your-app.herokuapp.com` **and NOT** `https://your-app.herokuapp.com`.

You will only see a subset of failing tests, however you will still be able to see your final grade. To get pull points we encourage to write your own tests. Looking into TMDb APIs more thoroughly and fuzz testing could be good approach in finding bugs in your app.

If you have correctly implemented the filtering and adding functions, **running the autograder will make changes to your Heroku database**. Subsequent runs of the autograder may not earn full credit, because the movies added to your database will be filtered out of search results in the future. One easy way to reset your database is just to destroy and re-create your Heroku app's database add-on before re-submitting to the autograder:

```sh
heroku addons:destroy heroku-postgresql -a <YOUR_APP_NAME>
heroku addons:create heroku-postgresql -a <YOUR_APP_NAME>
heroku run rails db:migrate
heroku run rails db:seed
```

> **Submission (100 points)**
>
> You should now be ready to submit your assignment. Remember to run your test cases once more, then submit your files to Gradescope, Codio or whichever platform your course is using.

---

[← Part 5: Implementing find_in_tmdb, and Stubbing the Internet](07-Part-5--Implementing-find-in-tmdb--and-Stubbing-the-Internet.md) | [Contents](README.md)

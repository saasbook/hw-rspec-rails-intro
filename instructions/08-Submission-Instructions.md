# Submission Instructions

You will be tested on both correctness and testability of your app. Deploy your app using the same technique as in CHIPS 5.3 (you may need a force push!). You should set up the production database as well, running the appropriate database setup commands for your platform. Once you are confident the functionality works correctly on your deployed app, submit the URI of that app in a text file called `rottenpotatoes-url.txt` with no other contents.

**Please be careful** to use **http** and not **https**, that is, submit `http://your-app.onrender.com` **and NOT** `https://your-app.onrender.com` (on Heroku, likewise `http://your-app.herokuapp.com`).

You will only see a subset of failing tests, however you will still be able to see your final grade. To get full points we encourage to write your own tests. Looking into TMDb APIs more thoroughly and fuzz testing could be good approach in finding bugs in your app.

If you have correctly implemented the filtering and adding functions, **running the autograder will make changes to your production database**. Subsequent runs of the autograder may not earn full credit, because the movies added to your database will be filtered out of search results in the future. So reset the database before you re-submit.

On Render, the free tier gives you no production shell, so reset the data from the build phase instead: temporarily add this line to `bin/render-build.sh`, push to trigger a deploy, then take it out again.

```sh
bundle exec rails runner 'Movie.delete_all; Rails.application.load_seed'
```

On Heroku, destroy and re-create the app's database add-on instead:

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

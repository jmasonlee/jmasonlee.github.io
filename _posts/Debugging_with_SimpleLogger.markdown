I’m used to working with the approvaltests library to quickly get legacy code under test for refactoring, but two weeks ago, I had the opportunity to use another tool, called SimpleLogger, which is surprisingly useful. 

I usually join [the Approvaltest.Python mob](https://github.com/approvals/ApprovalTests.Python/blob/main/docs/Contribute.md#join-our-weekly-mobbing-sessions) when I get a chance, but I’d been busy putting together a talk (and hiking!), so I hadn’t been able to attend for almost 6 months. 

Since I had a hackathon at work where I could work on any project I wanted to, I thought it would be a good opportunity to try and make up for all those missed sessions, so I asked Llewellyn if he’d like to spend a few days working on approvaltests. I was really excited when he agreed!

**_…and then he wanted to work on a LOGGER_** :persevere:

I'm not sure I can accurately convey how dissapointed I was. Logging is… useful, I guess, but also… _boring?_

It’s mostly glorified print statements, isn’t it? And if you really need to log errors, Python has a default logger built in. So why in the world would a custom logger for approvaltests not be reinventing the wheel?

**A day after we created SimpleLogger, I was using it**

We had a bug that only appeared when our job was run in production, so we had to debug it with logs. I'd just built a bunch of nice methods to log variables and events with SimpleLogger, so I decided to use those methods rather than building my own custom log messages. They add all of the information I care about when debugging an issue. Every log message gets a timestamp, variables can be printed with their types, and lists get expanded so you can see what's inside. 

Seeing the flow of data through my code became a trivial issue, and I saw the bug almost immediately - we were sending the wrong date to a third party service.

**This is when I fell in LOVE with SimpleLogger**

The code that sent the date was buried deep in the application, in a place that was impossible to test without significant refactoring. I needed to fix the issue quickly, but I also didn't have an easy way to verify the change I was about to make would result in the _right_ date being sent. 

We were under a time crunch, so I was about to make the change, deploy, and pray :pray:. Then I remembered I could use `verify_simple_logger`. 

This method lets you write tests on your log's output. I already had my logs in place, and they were already showing the buggy behaviour. I wrote a test:

```
def test_my_logs():
    with verify_simple_logger():
      run_my_job()
```

Then I checked the `test_my_logs.received.txt` file:

```
-> in: run_my_job() in my_batch_job
  -> in: send_dates() in my_batch_job
    variable: dates_to_send<list>.length = 2
      dates_to_send[0] = '2022-09-04' <str>
      dates_to_send[1] = '2022-09-05' <str>
  <- out: send_dates()
<- out: run_my_job()
```

We were only sending a list of two dates (`['2022-09-04', '2022-09-05']`), when we intended to send a list of three (`['2022-09-03','2022-09-04', '2022-09-05']`). This was causing some issues when we processed the response from the third party program that was receiving the dates. I made the change I thought would fix things, and I ran the tests again. The received file showed the change:

```
-> in: run_my_job() in my_batch_job
  -> in: send_dates() in my_batch_job
    variable: dates_to_send<list>.length = 3
      dates_to_send[0] = '2022-09-03' <str>
      dates_to_send[1] = '2022-09-04' <str>
      dates_to_send[2] = '2022-09-05' <str>
  <- out: send_dates()
<- out: run_my_job()
```

It was fixed!!!!  :tada:

I deployed the code, and got things working in production, Then I cleaned up my logs, and I wrote a better test.

**Many times, the code we work with isn't built for testability**

We can use things like proveable refactorings and approval testing to get the code to a point where we can test it, but those approaches take time. If I need to fix a bug _now_ I don't necessarily have that time to spare. By allowing me to easily document and verify the flow of data through my application, SimpleLogger allows me to quickly iterate on a fix so that I know it works without having to deploy it.

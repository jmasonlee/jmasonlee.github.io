I’m used to working with the approvaltests library to quickly getting legacy code under test, so I can refactor it, but two weeks ago, I had the opportunity to add another tool, called SimpleLogger, which is surprisingly useful. 

I usually join [the Approvaltest.Python mob](https://github.com/approvals/ApprovalTests.Python/blob/main/docs/Contribute.md#join-our-weekly-mobbing-sessions) when I get a chance, but I’d been busy putting together my talk (and hiking!), so I hadn’t been able to attend regularly for almost 6 months. I had a hackathon at work where I could work on any project I wanted to, so I asked Llewellyn if he’d like to spend a few days working on approvaltests. I was really excited when he agreed!

**_…and then he wanted to work on a LOGGER_**

I am not sure I can convey my disappointment at this point. Logging was… useful, I guess, but also… _boring?_

It’s mostly glorified print statements, isn’t it? And if you really need to log errors, Python has a default logger built in. So why in the world would a custom logger for approvaltests not be reinventing the wheel?

**A day after we created SimpleLogger, I was using it**

I was working on a bug that only showed up in production. SimpleLogger has some nice methods to log variables, events, and entries and exits from methods,  and I enjoy saving myself a few keystrokes, so I decided to use them rather than building my own custom log outputs. These methods add all of the information I want in debug logs, but forget to add on my own. Every log gets a timestamp, variables can be printed with their types, and it even automatically expands Collections so you can see what's inside. Because of this, seeing the flow of data through my code became a trivial issue, and I saw the bug almost immediately - we were sending the wrong date to a third party service.

**This is when I fell in LOVE with SimpleLogger**

The code that sent the date was buried deep in the application, in a place that was almost inaccessible to tests without significant refactoring. I needed to fix the issue quickly, but I also didn't have an easy way to verify the change I was about to make would result in the _right_ date being sent. 

We were under a time crunch, so I was about to make the change, deploy, and pray. Then I realized approvaltests has a magic method, `verify_simple_logger`. 

This lets you write tests on your log's output. It looks like this:

```
def test_my_logs():
    with verify_simple_logger():
      the_thing_that_makes_the_logs()
```

I already had my logs in place, and they were already showing the buggy behaviour. I wrote a test:

```
def test_my_logs():
    with verify_simple_logger():
      run_my_job()
```

Then I checked the `test_my_logs.approved.txt` file:

```
-> in: run_my_job() in my_batch_job
  -> in: send_dates() in my_batch_job
    variable: dates_to_send<list>.length = 2
      dates_to_send[0] = '2022-09-04' <str>
      dates_to_send[1] = '2022-09-05' <str>
  <- out: send_dates()
<- out: run_my_job()
```

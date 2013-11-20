---
layout: post
title: 'Refactoring SMTP Diagnostics'
categories:
  - blogger

---

In a recent blog posting, I talked about <a href="http://www.thecave.com/archive/2005/09/02/convincing_a_client_it_is_time_to_refactor.aspx">convincing a client it's time to refactor</a>.  Well, I have spent the last few days convincing myself that it is time to do some refactoring of <a href="http://www.smtpdiagnostics.com/">SMTP Diagnostics</a>.<br /><br />For those who don't know, SMTP Diagnostics is a mailer program enabling you to troubleshoot problems with outgoing email and assist with configuring outgoing (SMTP) servers.<br /><br />I have been putting off refactoring while still adding new features.  I did this to "save time" but the code base has reached a point where it is now more time consuming then it should be to add new features.  I can put it off no longer.<br /><br />What's fun about this exercise is that I get to build from the knowledge obtain thus far.  Version 1.0 did not have a solid object model and a lot of the code was specific to this one project.  Version 1.2 and 1.3 moved away from that by incorporating common code, or a common framework, that I'm using in a second product code-name Vertigo.  Version 1.4, which is the next release, will finally have a reusable object model that will make adding new features much easier.  For example, adding command line support will be a snap once the new object model is in place.  <br /><br />Look for the beta release for version 1.4 in a few days.
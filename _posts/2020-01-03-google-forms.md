---
title:  "Working Google App Scripts to populate a form from Sheets pt. 1"
date:   2020-01-03
categories: [Web development]
tags: [blog]
---
Over the past view days I've been working on a couple of things for project with
with Google Forms integrating with Google Sheets. Exporting user input from Forms
to Sheets is already built in to the UI. But populating a form with date from Google
Sheets is what I was after. At first I thought that I might try to reverse
engineer this [html form](https://github.com/cameroncrobinson/Form-Export-Questionaire-)
that submits the input to a row on a sheet.

Instead, I found tutorial to populate areas in Google forms. The code their will be the basis of
what I create for the form. The basic idea for this form is to have a list of possible dates for
volunteers to work that gets pulled from one Sheet and the list of available volunteer that gets
pulled from another Sheet. So far I've gottent the dates working. The main snag that I've hit is
with the way the dates are formatted in Sheets vs Google's App Script (which is kind of like js).
For now I've done this to simplify the date output in Form:

  for(let i = 0; i < datesValues.length; i++)
  if(nameValues1[i][1] == null)
  volunteerDates[i] = new Date(datesValues[i][0]).toString();
  for(let i = 0; i < volunteerDates.length; i++){
  volunteerDates[i] = volunteerDates[i].split(' 00:')[0];
  }

  I'm sure there is a cleaner way to clean up the code but for now it's a good fix I'll figure out
  how to filter out dates based on whether cells are empty within the same row or not.

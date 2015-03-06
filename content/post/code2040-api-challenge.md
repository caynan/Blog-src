+++
categories = ["coding"]
date = "2015-01-02T23:23:06-05:00"
description = "What is CODE2040? And the process of applying for it."
keywords = ['code2040', 'api']
slug = "code2040-api-challenge"
title = "CODE2040 API challenge"

+++

### Overview

> CODE2040[^1]  is a nonprofit organization that creates pathways to
> educational, professional and entrepreneurial success in technology for
> underrepresented minorities with a specific focus on Blacks and Latino/as.

I was told about this program by a friend (Yuri) who was a Fellow in 2012, if
you understand Portuguese and want to hear a little about his experience you
could hear this interview[^2] with him.  This is a great opportunity to get to
know like minded people, that are interested in growing as IT professionals,
since and also great opportunity to got a great internship in which your are
not only going to learn on the internship, but with the various workshops that
the CODE2040 organize along the duration of the program.

One of the key objective of the program is to get people engaged, and to create
a community of people that represents the minorities in the IT world, seriously
they even make you sign a honor contract that you are going to help others.

So as obvious as it sounds I got interested in the hole idea of the program,
also in the opportunities that it creates, and went to their website to
apply[^3].

### Applying

As part of the process to apply there is some questions that I think are trying
to evaluate your soft skills, also your interest in the program as I said the
idea is to create a community of people that are going to help and spread the
knowledge in their communities.

After the Demographic questions and the skills to access how you match the
profile they are trying to find, we get to a really interesting part.

### API Challenge

The API challenge is a way to test if you are able to code a solution to simple
problems on your own. The problems are really basic, you have to GET some
values from their API process them and POST the results back. I'll explain the
logic of each problem, and later (after the application period ends) I'll
create specific articles for each implementation that I've made.

#### Stage I: Reverse a string You are going to receive a string, that you have
to reverse it, most modern languages have builtin functions that do this.
After you reverse the string you have to POST the result as a  json object in
the format

```javascript
{ token: '<The token you received>', string: 'reversed string' }
```
Pretty straight forward, right?

#### Stage II: Needle in a haystack You are asked to given a list/array
(haystack) and a value (needle) find in which position the needle is in the
zero based list/array. Again really simple question, depending on the language
you could have a builtin function, if not you could always iterate over the
elements and find the index.  After you find the position you have to POST the
result as a json object in the format

```javascript
{ token: '<The token you received>', needle: index }
```


#### Stage III: Prefix You are asked to given a list/array, return a list/array
with all the elements that *don't* start with the given `prefix`. Again many
modern languages have builtin functions that do this, if you are is a more low
level language, you could use a for loop in each input, up to the size of the
prefix, removing the element every time you find a match.  After you filter the
input array you have to POST the result as a json object in the format

```javascript
{ token: '<The token you received>', array: [ 'filtered', 'array'] }
```


#### Stage IV: The dating game This was probably the most 'difficult' problem
of all, you have to receive a date in the ISO 8601 format add an interval in
seconds and return the final time in the ISO 8601 format. Many languages have
libraries to work with time, take a look in the documentation of your chosen
language, it's almost sure your are going to find something that could help a
lot.  After you find the final `datestamp` you have to POST the result as a
json object in the format

```javascript
{ token: '<The token you received>', datestamp: 'datestamp' }
```


### Final Considerations

I really enjoyed doing this challenge, and I have plans to keep using it, if it
keeps working after the application period, to learn new languages and
frameworks. Since it's a great way to get a quick sense of a new tool. If you
are part of a minority group you should really apply for the CODE2040 program I
think it's a great opportunity.


So Long, and Thanks for All the Fish



[^1]: http://code2040.org
[^2]: https://www.youtube.com/watch?v=BT6UNiIzx34
[^3]: http://code2040.org/apply/</The>

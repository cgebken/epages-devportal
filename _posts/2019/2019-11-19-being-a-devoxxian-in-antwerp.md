---
layout: post
title: Being a Devoxxian in Antwerp
date: 2019-11-19
header_image: private/devoxx-be-header.jpg
header_position: top
header_overlay: true
category: events
tags: ["conference", "java11", "rest", "spring", "security"]
authors: ["Donaldo"]
about_authors: ["dlika"]
---

In this post I am going to tell you about my experience at [Devoxx Belgium 2019](https://devoxx.be){:target="_blank"}.
It took place at Kinopolis in Antwerp, Belgium.
The talks were held in the cinema auditoriums, guaranteeing top seats, top audio, and top visual quality.
As the tickets were sold out so early this year, the rooms and the venue were packed to the rim with people.

{% image_custom image="/assets/img/pages/blog/images/devoxx-be-room.jpg" width="50" lightbox %}

## Qualities of a Highly Effective Architect

First I have to say that this talk was really inspiring and made me think of changing some things of the way I behave in certain situations.

The conference kicked off with a keynote by [Venkat Subramaniam](https://twitter.com/venkat_s){:target="_blank"}, who listed a set of qualities an architect should have, but in my opinion the same qualities apply for developers and engineers.
Venkat amazingly explained those qualities by providing his own experiences.

{% image_custom image="/assets/img/pages/blog/images/devoxx-be-venkat.jpg" width="50" lightbox %}

This keynote left everyone including me highly motivated and inspired.
Here are the key points I took with me:

- Knowledge is a wealth that grows when given
- Criticize ideas, not people
- Architecting is evaluating tradeoffs
- Stop being biased when it comes to technology decisions
- Guide, don't dictate
- Proactive Collective Ownership
- Prototypes beat any arguments
- Comfort is your enemy

{% twitter https://twitter.com/venkat_s/status/1767761478 %}

## How to get properly hacked, [Julien Topçu](https://twitter.com/julientopcu){:target="_blank"}

This talk was held by Julien Topçu, a member of the OWASP Foundation whose mission is to increase the visibility of security on applications, so that people and organizations can make informed decisions.

{% image_custom image="/assets/img/pages/blog/images/devoxx-be-julien.jpeg" width="50" lightbox %}

He made the attendees discover security holes through the story of Candide admiring his mentor, who decides to create his own commercial site "Pangloss", where you can find books and video game consoles.
He showed us through his adventures how Candide discovered the vulnerabilities of his site, starting from the well-known SQL injection which allows, among others, to log in as an administrator, to less known vulnerabilities that can execute code from remote.

What I particularly appreciated in this presentation was the ease with which I understood and followed this subject that was so well brought.
It was easy to put myself in Candide's place and from now on I would be more vigilant in my code to avoid security breaches.

### Java Language Futures, [Brian Goetz](https://twitter.com/BrianGoetz){:target="_blank"}

When it comes to Java, it has been declared dead many times, but in reality it is the world's most popular programming platform.
And next year (2020) Java will be 25 years old, for coincidence next year I will also be 25 years old 😃.

*Brian Goetz*
{% image_custom image="/assets/img/pages/blog/images/devoxx-be-java-upgrade.jpg" width="50" lightbox %}

Here are some of the language features coming up which will make it easier to build and maintain reliable programs:

#### Switch statement

 * Switch can now be either a statement or an expression
 * Multiple cases at once are allowed
 * No fallthrough allowed, break rarely needed
 * More concise, less error-prone

{% highlight java %}
int numLetters= 
        switch(day){
                case MONDAY,FRIDAY,SUNDAY -> 6;
                case TUESDAY -> 7;
                case THURSDAY,SATURDAY -> 8;
                case WEDNESDAY -> 9;
                // no default needed - all cases are covered
        }
{% endhighlight %}

#### Text Block
* Text can span multiple lines
* Incidental indentation is stripped away by the compiler
{% highlight java %}

String html = """
            <html> 
                <body>
                    <p>Hello ePages </p>
                </body>
            </html>
            """;
{% endhighlight %}

#### Record classes
* Transparent, shallowly immutable data aggregate
* Reduce boilerplate code
* Similar to data classes in Kotlin

{% highlight java %}
record Range(int low,int high){};
{% endhighlight %}

Here is an example of using the records as temporary variables on the stream's intermediate operations:

{% highlight java %}

List<Person> getTopNPersonsByScore(List<Person>list,int n){

    record PersonX(Person person, int score){};

    return list.stream()
               .map(p -> new PersonX(p, calculateScore(p)))
               .sorted(Comparator.comparingInt(PersonX::score))
               .limit(n)
               .map(PersonX::person)
               .collect(toList());
}

{% endhighlight %}

## Tools

Below is a fair list of tools, services, technologies that came to my attention during the entire conference.
I found them interesting and I would like to try them out.

- [ArchUnit](https://www.archunit.org/){:target="_blank"} Unit test your Java architecture
- [Bombardier](https://github.com/codesenberg/bombardier){:target="_blank"} HTTP benchmarking
- [Karate (DSL)](https://github.com/intuit/karate){:target="_blank"} Open-source tool to combine API test-automation, mocks and performance-testing into a single, unified framework
- [Dive](https://github.com/wagoodman/dive){:target="_blank"} Inspecting container image layers
- [DeckDeck Go](https://deckdeckgo.com/){:target="_blank"} Presentation Editor

## Final Summary

Devoxx BE 2019 was once again a great conference.
My "to-learn-list" is filled to the brim, and I also feel like I have to take time to look at the talks again, trying things out for myself. 

All in all, it is always refreshing to step out of your everyday tasks and let your mind stock up on new experiences.
I urge anyone who is passionate about development to visit, it is a place where knowledge and experiences are shared in the best way.
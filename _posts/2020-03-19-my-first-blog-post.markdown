---
layout: post
title:  "my first blog post :)"
date:   2020-03-19 11:23 +0000
---
Starting a blog to help me think (and because a potential employer might look at this and think "this guy kinda knows what he's doing wowee"). There'll be posts about development projects and probably math and probably bideo games in general. Check out my Github and Linkedin!

{% highlight c++ %}
#include <string>

enum MathTopic
{
    Topology,
    Algebra,
    Analysis
};

class Mathematician
{
    MathTopic m_favoriteSubject;

public:
    Mathematician(MathTopic favoriteSubject)
        : m_favoriteSubject(favoriteSubject)
    {}
};

class Billy: public JuniorDev, public Mathematician
{
    std::string m_name;

public:
    Billy(std::string name)
        : Mathematician(MathTopic::Topology),
        m_name("billy")
    {}
};
{% endhighlight %}
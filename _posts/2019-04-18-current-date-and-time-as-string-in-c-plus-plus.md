---
layout: post
title: Current date and time as string C++
---


Non `C++11` solution: With the `<ctime>` header, you could use `strftime`. Make sure your buffer is large enough, you wouldn't want to overrun it and wreak havoc later.

{% highlight c %}
#include <iostream>
#include <ctime>

int main ()
{
  time_t rawtime;
  struct tm * timeinfo;
  char buffer[80];

  time (&rawtime);
  timeinfo = localtime(&rawtime);

  strftime(buffer,sizeof(buffer),"%d-%m-%Y %H:%M:%S",timeinfo);
  std::string str(buffer);

  std::cout << str;

  return 0;
}
{% endhighlight %}

Since `C++11` you could use `std::put_time` from `iomanip` header:

{% highlight c %}
#include <iostream>
#include <iomanip>
#include <ctime>

int main()
{
    auto t = std::time(nullptr);
    auto tm = *std::localtime(&t);
    std::cout << std::put_time(&tm, "%d-%m-%Y %H-%M-%S") << std::endl;
}
{% endhighlight %}

`std::put_time` is a stream manipulator, therefore it could be used together with

`std::ostringstream` in order to convert the date to a string:

{% highlight c %}
#include <iostream>
#include <iomanip>
#include <ctime>
#include <sstream>

int main()
{
    auto t = std::time(nullptr);
    auto tm = *std::localtime(&t);

    std::ostringstream oss;
    oss << std::put_time(&tm, "%d-%m-%Y %H-%M-%S");
    auto str = oss.str();

    std::cout << str << std::endl;
}
{% endhighlight %}

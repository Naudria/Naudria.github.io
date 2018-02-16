---
layout: post
title:      "The Joys and Miseries of Coding"
date:       2018-02-16 22:02:58 +0000
permalink:  the_joys_and_miseries_of_coding
---


One of the things that attracts me most to code is the logic. It may take a while to understand, but eventually, when you get it, it's a "Eureka!" moment. I enjoy struggling for that moment.

Every once a while, however, my code works, and I have no idea why. That drives me NUTS. I want to know WHY something worked, not just memorize it for future use. For instance, I recently completed the Oxford Comma Lab in the Procedural Ruby section. It took me a loooooong time to figure out how to take the array, convert it into a string, add a comma and a final "and" before the last element of an array, and ensure arrays longer than 3 were formatted correctly. I hit on the answer by sheer trial and error:

```
def oxford_comma(array)
  if array.count <= 1
    array.join
  elsif array.count == 2
    array.join(" and ")
      else array.count >= 3
        last = array.pop
        array.join(", ") + ", and " << last
      end
end
```

Oh, good, I passed the lab. But HOW? I didn't even think I could throw a "+" in there and it would connect everything together. Or did I? Is that how the "+" works in ruby normally? Am I agonizing over nothing? The wrong thing? Also, who knew I could snap off the last element of the array then stick it back in whenever? 

As I've continued to read up on arrays and progressed a little further in the lesson, it's beginning to make more sense, but not completely. Hopefully it will be clear as crystal soon... Like, before I move on to OO Ruby. 


# Death works!

![](https://github.com/ikeos2/RPGProject/blob/main/Images/DeathWorks.gif)

Since last time, I was having trouble getting my death animation to play. After some finagling and waggling, I figured out the animation fade in time was set to 100%, resulting in no animation occurring. To remedy this, I moved it the other, now there's no transition between previous animation and the death animation, so character should just drop.
# Stats

*Now* I just need to get death to actually work hah. Luckily, I already have a "stats" system set up. Another place of work - I need some way of displaying dictionaries in Unity.

![](https://github.com/ikeos2/RPGProject/blob/main/Images/Stats.png)

I don't know if I like the stat system I have now, so I'm considering other ways to store this kind of data. 

Pros: 
* Simple + easy
* Done
Cons:
* How do I calculate sum functions? Ie add up all armor worn + all buffs?
	* Do I need to recalculate every time? is there a base stat? temps? So confused.
* Health is going to accessed **alot** - is this the best way to access it?

~ Some time passes

After spending the better part of the day pondering the matter, I *think* I have come up with a solution for handling summing functions of stats that allows me to have as many stats as I want.

First, we need to make the dictionary slightly more complicated. 
Right now, we have `Dictionary<Stat, float>` - we are going to create a new object to hold stat info with a tag, like this

```C#
public class StatHolder  
{  
    public Stat Stat { get; set; }  
    public string SourceTag { get; set; }  
    public float Value { get; set; }  
}
```

and then we can adjust the dictionary to

```C#
Dictionary<Stat, List<StatHolder>> _stats
```

Now, we'll need to adjust all the getter and setter fields, something I hadn't considered before.
My initial thought is to have the basic getter function to return a sum of all holders affects `<Stat>`. I think I will also add an "Apply Damage" function that will allow me to start implementing my special, proprietary damage formula(R)!

I *think* I'm happy with this systems now - can still apply damage and such, but should be more flexible in the future.

What's next? Here's my todo list, and that's just the stuff I think I can do! Excited as always to keep trucking along :)

![](https://github.com/ikeos2/RPGProject/blob/main/Images/todo-2.png)
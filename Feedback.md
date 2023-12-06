## Feedback 

> I'm really curious why my data wasn't at 100% the same as original data. I ended up
> getting really close on my first try, then made a change which took a very long time to get working
> that seemed to get me 0.00000001% closer and decided that continuing to work on it was a little crazy.

I mean, let's not ignore the possibility that I screwed something up in my version! 


> I really enjoyed this project I worked on it every chance I got until it was done, data engineering
> is awesome. The hardest parts were issues with different things trying to infer intended datatype,
> especially inferring int from x.0 numbers. For some reason it took me a while to find a solution that properly
> handled nan while also creating floats not ints, partly because i wasn't understanding this was where the problem was.

Yeah, I find DE satisfying in a strange way. Alyssa Toay mentioned that she had "good attention to detail" so that she
found a lot of DS work pretty fun. I think she's getting at the same thing I enjoy, that moment when all the pieces click together. 


> Also a weird thing happened where even though I was trying to replace tables when uploading,
> it seemed to try to use the schema of the old table, which compounded the issue of floats vs ints.
> I think there was a point where I found then gave up on the right solution because GBQ was using the old table's
> schemas which was throwing the error. Eventually when I realized this and deleted the whole dataset
> before each retry, it became alot easier.

That is, indeed, super weird. I passed it on to Spencer and I'm hoping it helps him out. I haven't seen this one before. 

> ChatGPT led me on some wild goose chases but I'm sure it would have taken me 5-10x
> longer without it. It basically did tasks 2 and 3 with minimal guidance,
> for task 1 I had to really understand everything and break it down to get it working.

Yeah, that 5-10x seems to optimal multiplier for unfamiliar tasks. (2-5x seems to be what I'm getting
on familiar things.) The lack of ChatGPT integration with Posit (nee R Studio) is making this 
the first time I've found myself dissatisfied with that IDE.

Your code looks good and clean overall. This line, `first_two_lines = [next(file) for x in range(2)]`, looks a 
little wierd to me. I'd probably just do: 
```
first_two_lines = [file.readline()]
first_two_lines = first_two_lines.append(file.readline())
```

This is extremely slick: 
```
with ThreadPoolExecutor(max_workers=4) as executor:
    list(tqdm(executor.map(upload_to_gbq, os.listdir(directory)), total=len(os.listdir(directory))))
```

I need to start multithreading more of my code....

On Task 2, I appreciate that you took the time to do it the reproducible way. This is much superior to the thing most people did, solving the whole problem with a SQL query. 

Task 3 looks pretty identical to my version, I think. 

Nice job!

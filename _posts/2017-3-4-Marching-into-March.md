---
layout: post
title: Marching into March
---

### What did I do this week?
It was exam week! My takeaway: shoulda memorized those gosh darned function headers.

I spent the past week learning way more than I had ever hoped to about the Python specifications. For instance why doesn't Python support tail call optimization? Guido van Rossum gives a syntatically-valid-yet-Lovecraftian-horrifying [example](http://neopythonic.blogspot.com.au/2009/04/tail-recursion-elimination.html). Could this be rectified by including a function in its own namespace so that defining a new function with the same name doesn't break recursive calls unless you explicitly change scope? Beats me, I'm just providing a hot take!

Playing the long game: my infiltration of the Python irc channel has begun. I'm hoping I can convince them that `tuple(iterable)` would be better as `tuple(iterable, *a)` before the semester's over to retroactively recover 5 points on my exam.

### What is in my way?
Finding good source material for our project. Discogs.com has great data but doesn't share URIs with dbpedia, which is pretty disappointing. Alas, Pokémon really would be such a good source for this. Creatures, abilities, locations, and items would provide 4 solid tables with plenty of foreign keys to click through...

Oh, and TACC Stampede queues. Is there nothing more mojo-killing than not knowing if you fixed your code for 45 minutes?

### What will I do next week?
I think for IDB we're going to use Discog, but it only provides a model for album, artist, and label. I think we should be able to interpolate a 4th model for songs using title string similarity and duration for record matching. For that we'd need to spin up our own triple store for the songs and the album tracklists that will now point to them. As far as I can tell we wouldn't need to doctor the artist data. I think hand curating the labels to distinguish the majors from indie wouldn't be too daunting as there's only a limited number of major labels.

_(Ed. Note: total tangent)_ As a pet project I'd like to try my hand making a site for a game very similar to Pokémon, Dragon Warrior Monsters, for the interesting optimization problem its breeding system creates (merge 2 monsters into one, not commutative). Given a collection of monsters, what's the strongest thing you can create? I believe a brute force approach for the possible outcomes from n monsters would have O(n!&sup2;) complexity? Yikes.

I think it'd be a pretty interesting exercise in heuristics to break one of the ultimate bosses into more and more component monsters and see for what size collection I'm able to reconstruct it. `(arctan)`

### What is my experience of this class?
It's a tale of two curricula: software engineering and the ins-and-outs of Python. We just got Google Cloud Platform credit and will get a primer from some of their engineers next week that I'm pretty hyped for. We will also probably learn about more built-in Python functions. Python: at least it's not Scheme.

I like to drag Python, but last week my friend needed to convert geohashes into lat/lon coordinates he could use in Tableau and I wasn't about to teach him Fortran90 for that (despite its _**superior**_ indexing conventions).

### What is my **tip-o-the-week**?
Don't forget to merge your private and classroom repos. Whoops.

OK here's a better tip: defaults! Python lets you make arguments optional by providing defaults. These defaults are stored in a tuple as the function's `__defaults__` attribute with the rightmost positional parameter corresponding to the rightmost tuple element. I wanted to believe it works by grabbing a trailing slice of the tuple and unpacking that into the call, but for some reason it doesn't support lists. ¯\\\_(ツ)_/¯ No idea why this bothers me so much, but I believe that mandating a Tuple when an Indexable would do is unpythonic.

Anyway, since it's stored as a tuple, what `__defaults__` points to is immutable. Not a problem though, this is Python and functions are objects so you can go ahead and point the function's `__defaults__` attribute to a new tuple with your updated defaults. Et voilà! The application that comes to mind is a default valued integer representing an incrementing serial number that you can choose to override.

Tying it all back to including a function in its own namespace: Is there a way for a function to reference itself independent of name? Because my implementation breaks if a function loses its name. All I've found is the `sys` module lets you access stack frames with the warning that it's not for mere mortals, and there's no guarantee it's even implemented.

### Continuous Integration in the News!
Malicious actors have been using bots to make bogus pull requests on open source repos so they can harness the CI testing cycles to mine bitcoin. [Genius.](https://motherboard.vice.com/en_us/article/bitcoin-mining-github-open-source-bots)

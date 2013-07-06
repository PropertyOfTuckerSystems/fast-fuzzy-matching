fast-fuzzy-matching
===================

Burkhard-Keller tree implementation. Uses Damerau-Levenshtein algorithm for metric calculation.
Based on http://blog.notdot.net/2007/4/Damn-Cool-Algorithms-Part-1-BK-Trees
http://en.wikipedia.org/wiki/Damerau%E2%80%93Levenshtein_distance

If you wish to use BK-tree with your custom types,
**implement the following interface**
```c#
public interface IDistanceMeasurer<in T>
{
    int Measure(T x, T y);
}
```

But take into account that any implementation **MUST form a Metric Space** (http://en.wikipedia.org/wiki/Metric_space).

fast-fuzzy-matching comes with a **Damerau-Levenshtein** algorithm for distance calculation.

### Sample app
```console
SampleApp.exe <pathToFileWithSomeWords> <desiredWordsCount> <maxWordDistanceToMatch> [<randomQueriesToRun>]
```

If you omit last argument, app will launch in interactive mode.
If you do not have file with enough number of words, download one from 
http://dumps.wikimedia.org/enwiki/latest/ (all en_wikipedia titles).

Sample app loads distinct words from file in lowercase (number of words to load can be limited using **desiredWordsCount**
then **shuffles** them with http://en.wikipedia.org/wiki/Knuth_shuffle.

Output (on my machine, MBA mid 2012) for 
```cmd
SampleApp.exe C:\Users\Taras\Desktop\enwiki-latest-all-titles-in-ns0 10000000 2 10000
```
(loading file into memory and building tree omitted for obvious reasons)
```cmd

```

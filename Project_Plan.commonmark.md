# Korean-English Code-switching by Popular Korean Artists
Nicole Giles
2025-10-06

\#Project Plan

**Introduction**: The Korean music industry has grown and is amassing
global attention like never before. The genre of popular Korean music
has changed due to this global audience, but the language choice of
lyrics has also notably shifted in recent years to include more and more
English language. There are even many artists who release songs entirely
in English in what seems to be an effort to reach an international
audience and arguably to break into the hard-to-crack Western music
industry. I am interested in seeing if artists who have been in the
industry for a long time change their language (i.e. use more English
and less Korean) as their popularity grows.

**Research Questions** - Does an artist adapt their language choice
(Korean vs. English) depending on their rising popularity?  
- Is popularity (album sales) correlated to language use (Korean
vs. English lyrics)? - Does the place in the structure of a song have
any correlation to which language is used?

**The Data:**

Seventeen (2015- present) is a boy group that holds the current record
for best-selling album from a Korean artist with their 2023 album *FML*.
They have released music since then and have a long list of frequent
(annual) releases since their 2015 debut a whole decade ago. I plan to
look at the language use of all of the songs from 4 albums from
Seventeen:  
Their debut album (EP), 2015  
An album from the middle of their career, 2020  
Their best-selling album, 2023  
Their most recent album, 2025

Lyrics for each album’s main promoting tracks are easily available
online in their raw, romanized, and English-translated forms. The
website, colorcodedlyrics.com is a reliable source to find the lyrics of
all of the songs that I need. I will need to sort the data by language
of lyrics, English or Korean. I hope to do this with either the
**textcat** package or the **cldr** package (I don’t know much about
these yet.). There are functions in these packages that can identify the
language of each word for me, so that I can sort them by English or
Korean. There is potential for the inclusion of a third language such as
Spanish or Japanese, as terms from these languages are sometimes
borrowed, which the packages should also be able to identify for me.
Other variables would include year, word type (Nouns vs. Verbs, Content
vs. Structure Words), title versus non-title track song, and place in
song (chorus, verse, bridge, etc.). I will likely need to code this
information by hand. Most importantly, I will have to do a
cross-analysis of lyric language and word choice change over time. I
believe that place in the song may also show differences in language
choice and vary depending on when the album was released.

**Working Hypothesis**:

I predict that there will be an increase in English use after the
release and success of Seventeen’s best-selling album to reflect the
group’s likely intent to increase their global influence. English as a
lingua-franca would reach the most people across the world and can be
understood by a larger amount of people groups.

I hope to discover insight into how language is adapted based on the
perceived or intended audience. I have done previous research
surrounding audience design and am curious to see how a popular medium
like music blends with linguistics to affect how we interact with each
other on a global scale.

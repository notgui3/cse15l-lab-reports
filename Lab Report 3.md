# **CSE 15L Lab Report 2** 

# **Part 1 - Bugs** <br>
I will be writing about the bug in the ```reversed``` method within ```ArrayExamples``` <br>
<br>

```
// Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }

```

```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {

  /* 
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 1, 2, 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
*/

  @Test
  public void testReversedFail() {
    int[] input1 = { 1, 2, 3  };
    assertArrayEquals(new int[]{3,2,1 }, ArrayExamples.reversed(input1));
    
  }

  @Test
  public void testReversedSuccess() {
    
    int[] input2 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input2));
    
  }
}

```
My failure-inducing JUnit test input was the array {1,2,3} which expected {3,2,1}, but did not get the expected value from the test. <br>
My non-failure-inducing JUnit test input was {}, which expected {}, and the test passed the test matched the expected. <br>

![Image](failSuccess.jpg) <br>
These are the symptoms for the two tests, ```testReversedFail``` with the {1,2,3} input failed and ```testReversedSuccess``` did not fail with an input of {}. <br>
```
// Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }

```
<br>

```
// Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```
The top is the original ```reversed``` method and the bottom has had its bug fixed. To fix the method I changed the line ```arr[i] = newArray[arr.length - i - 1];``` and ```return arr``` from the original to ```newArray[i] = arr[arr.length - i - 1];``` and ```return newArray``` to fix the bug. This was causing a bug because if you analyze the method, what we want to do is to create an array called newArray and put the elements from arr into newArray in reversed order and return newArray. However, the original code by putting ```arr[i] = newArray[arr.length - i - 1];``` and ```return arr``` was setting arr to elements within newArray then returning arr, causing the failure in the {1,2,3} input as it was putting the elements in newArray, which was empty, into arr, making arr empty and not returning the expected array. This also explains why {} as an input did not cause a failure because newArray was empty and its elements were replacing the elements within arr, causing it to be an empty array being returned and matching the expected. This change to ```newArray[i] = arr[arr.length - i - 1];``` and ```return newArray``` fixes the method because now it matches what it is supposed to do, which is to put the elements from arr into newArray in reversed order, then return newArray.

<br>
<br>
<br>


# **Part 2 - Researching Commands** <br>
grep <br>
-n for grep. <br>
```
Gui@DESKTOP-AGQV64K MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -n "BMI" technical/biomed/1468-6708-3-1.txt                                               
11:        between body mass index (BMI) and mortality, controlling
13:        excess risk for persons with very low BMI, but that persons
14:        with moderately high BMI had little or no extra risk except
24:        because few studies have examined the relation of BMI to
34:        events [ 10 ] . In this paper we study whether BMI at
66:          BMI was calculated as measured weight in kilograms
70:          BMI of 18.5 to 24.9; overweight as 25 to 29.9; and
72:          separately the group with BMI between 18.5 and 20, which
128:          with BMI. To adjust for possible confounding we chose
131:          and likely to be related to BMI. Self-reported covariates
166:          plotted mean adjusted YOL and YHL against BMI, and tested
167:          for difference among BMI groups using confidence
169:          the effect size for each measure, comparing each BMI
183:        smokers. Black women had a higher mean BMI and higher
184:        percent obese (BMI ≥ 30) than the other three groups. Black
207:        statistically significant (p <.05) except for BMI and
211:        significant differences between black and white for BMI,
216:        the difference in BMI was no longer statistically
218:        significantly on BMI, BMI>30, weight loss since age 50,
226:        We next examined the relationship of BMI to YOL and YHL.
232:        BMI below 18.5, but averaged 6.6 years for women with a BMI
235:        only discrepancy is for men with BMI < 18.5, a category
240:        with BMI from 18.5 to 20 would be considered 'normal' by
243:        increase sample size for those with low BMI, we combined
244:        the two lower categories, defining underweight as a BMI
247:        BMI. For each BMI category the mean and its 95% confidence
254:        between BMI and YOL for BMI above 20. Underweight women
265:        normal group. The relationship of BMI to YHL for men is
266:        similar, but differences among BMI groups were not
272:        to the normal BMI group. The effect sizes are shown in
318:          et al proposed a desirable BMI of
421:        BMI Body mass index
```

```
Gui@DESKTOP-AGQV64K MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -n "ADHD" technical/biomed/1471-244X-2-9.txt
18:        Attention Deficit/Hyperactivity Disorder (ADHD) is also    
23:        populations [ 11 12 ] . Persistence of ADHD into adulthood 
26:        is clear that adults with a history of ADHD in childhood   
28:        non-ADHD peers [ 15 ] . One example is the higher rate of  
29:        substance use disorders in ADHD adults compared to the     
34:        observed [ 17 ] , though not previously linked to ADHD.    
36:        sequelae, and that both obesity and ADHD have psychiatric  
39:        obesity and ADHD (OB+ADHD). However, one study [ 24 ]      
46:        behavior is common in adolescents with ADHD, pointing to a 
47:        connection between ADHD and development of obesity, an idea
49:        eating behaviors are common in adult and adolescent OB+ADHD
60:        (ADHD), a condition that was recognized in our clinical    
62:        Fortunately, ADHD patients often responded to
67:        Cumulative bariatric clinic experience showed OB+ADHD      
70:        that more information about OB+ADHD was needed and that    
80:        of ADHD among obese patients was higher than in the general
81:        adult population. In addition, it was anticipated that ADHD
83:        shorter duration of treatment than their non-ADHD peers.   
97:        ADHD entered in the record during the course of obesity
102:        without ADHD (NAD), those with ADHD symptoms or behaviors,
103:        but not meeting diagnostic criteria for ADHD (ADSx), and
104:        patients with ADHD (AD).
105:        Diagnosis of ADHD was made by the author during the
111:        having ADHD. Patients who had fewer than 6, but at least 3
113:        ADHD but not diagnosed as having the disorder. None of the
118:        considered a symptom of ADHD if occurring only in
121:        impairment associated with symptoms was required for ADHD
125:        prominent to obscure or account for ADHD behavior or
126:        impairment for the diagnosis of ADHD to be made.
137:        exception to DSM-IV ADHD diagnostic criteria was made
151:        inconsistent with ADHD in general, favoring an inference
158:        underdiagnosing ADHD were judged to be far more
160:        Accordingly, during treatment, diagnosis of ADHD was made
169:        specific point in early childhood in order to diagnose ADHD
170:        is not rational, that is, ADHD is better conceptualized as
172:        None of the ADHD group had a level of
175:        of ADHD.
202:        array which was suitable for determining prevalence of ADHD
203:        in whole sample and looking at the differences in ADHD
206:        ADHD group, contains 59, or 27.4% (95% CI:21.1% to 32.9%)
212:        proportion of patients having ADHD in obesity class III
218:        There were 26 patients with ADHD and Ob-III, which is
246:        ADHD status for members of this subgroup was: NAD 7.0 (SD
274:        The most important results are the prevalence of ADHD of
276:        association between ADHD and Obesity III. Nearly half,
277:        42.6%, of patients with Obesity III had ADHD, that is, the
278:        OB+ADHD population was concentrated in the obesity class
281:        Moreover, at all levels of obesity patients with ADHD
283:        non-ADHD peers. Compared to NAD, AD had a significantly
290:        "subthreshhold" ADHD symptoms reduces the effectiveness of
291:        obesity treatment. In other words, in OB+ADHD, treatment
292:        outcome has stronger association with symptoms of ADHD than
293:        level of obesity. Effect size of ADHD for the whole sample
310:        in ADHD has been previously reported [ 29 ] , and could be
313:        The reasons for a strong association between ADHD and
319:        genes, and in ADHD, the DRD4 [ 32 33 ] gene, have been
330:        ADHD [ 22 ] . The DRD4 gene has been associated with
334:        difficulties (e.g., having both ADHD and "reward deficiency
335:        syndrome") [ 30 ] , further suggesting obesity and ADHD
347:        dopamine-mediated psychiatric symptoms, including ADHD. No
352:        The 27.4% prevalence of ADHD in obese patients is
356:        ADHD or ADHD symptoms was also greater than in general, for
362:        most part. The prevalence of OB+ADHD in this report is
364:        The uniformity of the Inattentive subtype of ADHD in
367:        impulsive symptoms observed as children with ADHD grow into
370:        say that ADHD adults don't behave impulsively, simply that
373:        among their school-age counterparts. That is, while ADHD
378:        subtype of ADHD. DSM-IV ADHD subtyping, strictly applied,
383:        higher than nearly all ADHD adults will display, even if
401:        of prospective research designs. For example, ADHD research
403:        would likely identify fewer cases of ADHD than the "gold
409:        criterion for ADHD may increase difficulty of comparing
417:        be easily separable from those found in ADHD, and
418:        erroneously diagnosed as ADHD. Several disorders common in
426:        effort to avoid diagnosing ADHD if symptoms are not
429:        of comorbidities intercurrent with ADHD.
434:        the interviewer. For the OB+ADHD population, the idea is
436:        ADHD symptoms, instead of accepting more accurate
444:        depressed mood. Implications for the OB+ADHD population are
446:        research of ADHD prevalence have not received comparable
448:        encountering this bias in clinical work with adult ADHD
454:        OB+ADHD. At this point, it remains an open question,
469:        Some effects of demographic factors on diagnosis of ADHD
472:        conceivably affect the range and intesity of ADHD symptoms
504:        which makes awareness of the ADHD-obesity comorbidity
508:        recognizing and treating ADHD is only a modest contributor
510:        alone. Moreover, the impairment of ADHD is an intrinsic
513:        function in ADHD sufferers more often than not provides
515:        The apparent association of OB+ADHD, relatively poor
516:        obesity treatment outcome and high prevalence of OB+ADHD
518:        that comorbid ADHD increases the health risks of obesity,
520:        adds burden to the profound impairments common in ADHD. The
```

The -n command line option for grep takes in a string and finds all of the lines that contain that string within a file and prints the line out along with the line number, which can be very useful for things like indexing words.
<br>
<br>
<br>

-i for grep <br>
```
Gui@DESKTOP-AGQV64K MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -i "george" ./technical/911report/chapter-1.txt
    Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.
    while the children continued reading. He then returned to a holding room shortly before 9:15, where he was briefed by staff and saw television coverage. He next spoke to Vice President Cheney, Dr. Rice, New York Governor George Pataki, and FBI Director Robert Mueller. He decided to make a brief statement from the school before leaving for the airport. The Secret Service told us they were anxious to move the President to a safer location, but did not think it imperative for him to run out the door.
```

```
Gui@DESKTOP-AGQV64K MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -i "American" ./technical/911report/chapter-5.txt
            AL QAEDA AIMS AT THE AMERICAN HOMELAND
                but his involvement with al Qaeda appears to have inspired him to pursue American
                group to join him in a "jihad against the Americans." Although all were urged to
                November 2001 by an American air strike in Afghanistan.
                he collected Western aviation magazines; telephone directories for American cities
                anti-American opinions, ranging from condemnations of what he described as a global
                Saddam Hussein was an American stooge set up to give Washington an excuse to
                sessions at their Marienstrasse apartment that involved extremely anti-American
```
The -i command option for grep allows you to search with case insensitivity for a given string in a file which is useful for a general search when you don't exactly know what you need.
<br>
<br>
<br>


-c for grep <br>
```
Gui@DESKTOP-AGQV64K MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -c "abuse" ./technical/government/Alcohol_Problems/Session2-PDF.txt
18
```

```
Gui@DESKTOP-AGQV64K MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -c "money" ./technical/government/Gen_Account_Office/ai00134.txt
1
```
The -c command option for grep prints out the number of times the given string is found in a file which is useful for general data logging and can give you an idea of what the file is about.

<br>
<br>
<br>
-w for grep <br>
```
Gui@DESKTOP-AGQV64K MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -w "stem cell" ./technical/plos/journal.pbio.0020116.txt
        use of human embryonic stem cell research and somatic cell nuclear transfer techniques were
        “youth,” research into aging, including stem cell research, is predominantly to serve
        proportion of the experiments. Research on some of the reported adult stem cell
        cautioned that this has not been done for most adult stem cell preparations, and, even if
        properties of cells differentiated from adult stem cell preparations are to date
        more differentiated cells that can be derived from them—with other stem cell sources, such
        as the well-characterized hematopoietic stem cells, and with human embryonic stem cell
```

```
Gui@DESKTOP-AGQV64K MINGW64 ~/Documents/GitHub/docsearch (main)
$ grep -w "mRNA" ./technical/plos/journal.pbio.0020133.txt
        complex and the nature of the target sequence, the outcome can be either mRNA degradation,
        RNA interference (RNAi), in which dsRNA triggers sequence-specific mRNA degradation. The
        that are recognized today. In one type, silencing results from a block in mRNA synthesis
        (transcriptional gene silencing [TGS]); in the second type, silencing results from mRNA
        complementary mRNA of a plant gene, preventing its translation into protein. Although the
        control ‘sense’ transgene RNAs are unable to basepair to mRNA and hence should not induce
        and transgene mRNA (Lindbo et al. 1993). In addition to forging a link between RNA virus
        interfering'RNAs (siRNAs), derived from cutting longer dsRNA, can guide mRNA cleavage
        complex), a nuclease that associates with small RNAs and executes target mRNA cleavage
```
The -w command option for grep makes it so that it only prints out the line that matches the whole string, nothing more or less, in the given file. For example, if we search for "ball", lines with "football" or "balls" would not print, only lines with just "ball", and this is very useful for a focused search for a word or phrase so that you don't have to sift through junk matches with other commands.



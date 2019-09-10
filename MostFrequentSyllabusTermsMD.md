

```R
# load libraries

library(tm)
library(readr)
library(ggplot2)
```


```R
# upload BIOS512 syllabus for analysis
# use modified version of the syllabus consisting of Course Description-Final project
# modified version of the syllabus excludes sections Course Grading Scale(s)-Technical support

syllabuspath="C:\\Users\\A computer\\Documents\\MyPythonFiles\\Files\\SYLLABUSforanalysis.txt"

syllabustext=read_file(syllabuspath)

```


```R
# start cleaning syllabus text

syllabustext <- gsub("\n", " ", syllabustext)

print(syllabustext)
```

    [1] "# Course Description This course will be an introductory course to data science and is required for MPH students with concentration in Public Health Data Science. The goals of the course are to, 1. achieve proficiency in the R programming language, with particular emphasis    on the Tidyverse; 1. gain familiarity with a suite of data science tools; 1. master the practices of good data science; and, 1. learn how to apply the methods and tools to public health datasets.  # Prerequisites This course is required for MPH students with concentration in Public Health Data Science and is appropriate for master's students in quantitative fields. PhD students in computer science, business, psychology, social science, and science may also find this course useful. There are no pre-requisites beyond those required for entry into the MPH program.  # Instructor Chuck Pepe-Ranney, PhD   Visiting Lecturer   Department of Biostatistics   3101A McGavran-Greenberg Hall   Phone: 575-313-0993   Email: cpeperanney@agbiome.com    # Teaching Assistant *TBD*  # Office Hours: *TBD*  # Course Website: https://github.com/chuckpr/BIOS512  # Class Days, Times, Location: Tuesday and Thursday from 11am until 12:15pm.  # Course Overview This course will teach you the skills to build and communicate end-to-end data narratives.  We will specifically be focusing on the following techology: - [Tidyverse](https://www.tidyverse.org) - [Jupyter](https://jupyter.org/) - [Docker](https://www.docker.com/) - [Git](https://git-scm.com/) and [GitHub](https://github.com/) - (if time permits...) [scikit-learn](https://scikit-learn.org) and [Plotly](https://plot.ly)  # Course Format The course format will include two lectures each week. The lectures will be supplemented with in-class exercises, case studies, and examples of data science applications in public health settings.  # Course-at-a-glance The instructor reserves the right to make changes to the syllabus, including topics, readings, assignments, and due dates. Any changes will be announced as early as possible. For session-by-session course schedule details, please see the [course website](https://github.com/chuckpr/BIOS512).  # Course Assignments and Assessments This course will include the following graded assignments that contribute to your final grade in the course. For assignment descriptions and assignment grading rubrics, please see below.  | Assignments | Points/Percentages | | --- | ---: | | (approximately) Weekly exercises | 75 | | Final project | 20 | | Participation | 5 |  # Map of Competencies to Learning Objectives and Assessment Assignments Below you will see the competency you will develop in this course, the learning objectives that comprise the competency, and the assignment in which you will practice demonstrating this competency.  ## Competency: Select and use data visualization methods to interpret and communicate research results, with the overall objective of conducting reproducible research, both individually and in project teams.  ## Learning Objectives: 1. Achieve proficiency in the R programming language. 1. Gain familiarity with a suite of data science tools, including data    wrangling, data quality control, data cleaning/editing, exploratory data    analysis, and data visualization. 1. Understand the principles of good data science, particularly reproducible    research. 1. Become familiar with several software tools for best practices in data    science including Git, Docker, Jupyter, and Make. 1. Apply the data science tools and principles of best practice to real data    problems in public health settings.  ## Assessment Assignment: ### Assignments: Will require use of R and data science tools in solving real data science problems.  Projects will also require demonstration of the elements of reproducible research.  ### Final project: Will contain questions about the capabilities of different software tools and questions about the principles of good data science."
    


```R
# add a space between text and its hyperlink to prepare for later when punctuation is removed

syllabustext <- gsub("https", " https", syllabustext)

```


```R
# remove plurals

syllabustext <- gsub("s ", "  ", syllabustext)
print(syllabustext)
```

    [1] "# Course Description Thi  course will be an introductory course to data science and i  required for MPH student  with concentration in Public Health Data Science. The goal  of the course are to, 1. achieve proficiency in the R programming language, with particular emphasi     on the Tidyverse; 1. gain familiarity with a suite of data science tools; 1. master the practice  of good data science; and, 1. learn how to apply the method  and tool  to public health datasets.  # Prerequisite  Thi  course i  required for MPH student  with concentration in Public Health Data Science and i  appropriate for master'  student  in quantitative fields. PhD student  in computer science, business, psychology, social science, and science may also find thi  course useful. There are no pre-requisite  beyond those required for entry into the MPH program.  # Instructor Chuck Pepe-Ranney, PhD   Visiting Lecturer   Department of Biostatistic    3101A McGavran-Greenberg Hall   Phone: 575-313-0993   Email: cpeperanney@agbiome.com    # Teaching Assistant *TBD*  # Office Hours: *TBD*  # Course Website:  https://github.com/chuckpr/BIOS512  # Clas  Days, Times, Location: Tuesday and Thursday from 11am until 12:15pm.  # Course Overview Thi  course will teach you the skill  to build and communicate end-to-end data narratives.  We will specifically be focusing on the following techology: - [Tidyverse]( https://www.tidyverse.org) - [Jupyter]( https://jupyter.org/) - [Docker]( https://www.docker.com/) - [Git]( https://git-scm.com/) and [GitHub]( https://github.com/) - (if time permits...) [scikit-learn]( https://scikit-learn.org) and [Plotly]( https://plot.ly)  # Course Format The course format will include two lecture  each week. The lecture  will be supplemented with in-clas  exercises, case studies, and example  of data science application  in public health settings.  # Course-at-a-glance The instructor reserve  the right to make change  to the syllabus, including topics, readings, assignments, and due dates. Any change  will be announced a  early a  possible. For session-by-session course schedule details, please see the [course website]( https://github.com/chuckpr/BIOS512).  # Course Assignment  and Assessment  Thi  course will include the following graded assignment  that contribute to your final grade in the course. For assignment description  and assignment grading rubrics, please see below.  | Assignment  | Points/Percentage  | | --- | ---: | | (approximately) Weekly exercise  | 75 | | Final project | 20 | | Participation | 5 |  # Map of Competencie  to Learning Objective  and Assessment Assignment  Below you will see the competency you will develop in thi  course, the learning objective  that comprise the competency, and the assignment in which you will practice demonstrating thi  competency.  ## Competency: Select and use data visualization method  to interpret and communicate research results, with the overall objective of conducting reproducible research, both individually and in project teams.  ## Learning Objectives: 1. Achieve proficiency in the R programming language. 1. Gain familiarity with a suite of data science tools, including data    wrangling, data quality control, data cleaning/editing, exploratory data    analysis, and data visualization. 1. Understand the principle  of good data science, particularly reproducible    research. 1. Become familiar with several software tool  for best practice  in data    science including Git, Docker, Jupyter, and Make. 1. Apply the data science tool  and principle  of best practice to real data    problem  in public health settings.  ## Assessment Assignment: ### Assignments: Will require use of R and data science tool  in solving real data science problems.  Project  will also require demonstration of the element  of reproducible research.  ### Final project: Will contain question  about the capabilitie  of different software tool  and question  about the principle  of good data science."
    


```R
# convert the syllabustext into a corpus and inspect the corpus

syllabusCorpus <- Corpus(VectorSource(syllabustext))
inspect(syllabusCorpus)
```

    <<SimpleCorpus>>
    Metadata:  corpus specific: 1, document level (indexed): 0
    Content:  documents: 1
    
    [1] # Course Description Thi  course will be an introductory course to data science and i  required for MPH student  with concentration in Public Health Data Science. The goal  of the course are to, 1. achieve proficiency in the R programming language, with particular emphasi     on the Tidyverse; 1. gain familiarity with a suite of data science tools; 1. master the practice  of good data science; and, 1. learn how to apply the method  and tool  to public health datasets.  # Prerequisite  Thi  course i  required for MPH student  with concentration in Public Health Data Science and i  appropriate for master'  student  in quantitative fields. PhD student  in computer science, business, psychology, social science, and science may also find thi  course useful. There are no pre-requisite  beyond those required for entry into the MPH program.  # Instructor Chuck Pepe-Ranney, PhD   Visiting Lecturer   Department of Biostatistic    3101A McGavran-Greenberg Hall   Phone: 575-313-0993   Email: cpeperanney@agbiome.com    # Teaching Assistant *TBD*  # Office Hours: *TBD*  # Course Website:  https://github.com/chuckpr/BIOS512  # Clas  Days, Times, Location: Tuesday and Thursday from 11am until 12:15pm.  # Course Overview Thi  course will teach you the skill  to build and communicate end-to-end data narratives.  We will specifically be focusing on the following techology: - [Tidyverse]( https://www.tidyverse.org) - [Jupyter]( https://jupyter.org/) - [Docker]( https://www.docker.com/) - [Git]( https://git-scm.com/) and [GitHub]( https://github.com/) - (if time permits...) [scikit-learn]( https://scikit-learn.org) and [Plotly]( https://plot.ly)  # Course Format The course format will include two lecture  each week. The lecture  will be supplemented with in-clas  exercises, case studies, and example  of data science application  in public health settings.  # Course-at-a-glance The instructor reserve  the right to make change  to the syllabus, including topics, readings, assignments, and due dates. Any change  will be announced a  early a  possible. For session-by-session course schedule details, please see the [course website]( https://github.com/chuckpr/BIOS512).  # Course Assignment  and Assessment  Thi  course will include the following graded assignment  that contribute to your final grade in the course. For assignment description  and assignment grading rubrics, please see below.  | Assignment  | Points/Percentage  | | --- | ---: | | (approximately) Weekly exercise  | 75 | | Final project | 20 | | Participation | 5 |  # Map of Competencie  to Learning Objective  and Assessment Assignment  Below you will see the competency you will develop in thi  course, the learning objective  that comprise the competency, and the assignment in which you will practice demonstrating thi  competency.  ## Competency: Select and use data visualization method  to interpret and communicate research results, with the overall objective of conducting reproducible research, both individually and in project teams.  ## Learning Objectives: 1. Achieve proficiency in the R programming language. 1. Gain familiarity with a suite of data science tools, including data    wrangling, data quality control, data cleaning/editing, exploratory data    analysis, and data visualization. 1. Understand the principle  of good data science, particularly reproducible    research. 1. Become familiar with several software tool  for best practice  in data    science including Git, Docker, Jupyter, and Make. 1. Apply the data science tool  and principle  of best practice to real data    problem  in public health settings.  ## Assessment Assignment: ### Assignments: Will require use of R and data science tool  in solving real data science problems.  Project  will also require demonstration of the element  of reproducible research.  ### Final project: Will contain question  about the capabilitie  of different software tool  and question  about the principle  of good data science.
    


```R
# common cleaning of the corpus to convert all to lowercase, remove numbers and punctuation

syllabusCorpus <- tm_map(syllabusCorpus,tolower)

syllabusCorpus <- tm_map(syllabusCorpus,removeNumbers)

syllabusCorpus <- tm_map(syllabusCorpus,removePunctuation)


inspect(syllabusCorpus)

```

    Warning message in tm_map.SimpleCorpus(syllabusCorpus, tolower):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeNumbers):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removePunctuation):
    "transformation drops documents"

    <<SimpleCorpus>>
    Metadata:  corpus specific: 1, document level (indexed): 0
    Content:  documents: 1
    
    [1]  course description thi  course will be an introductory course to data science and i  required for mph student  with concentration in public health data science the goal  of the course are to  achieve proficiency in the r programming language with particular emphasi     on the tidyverse  gain familiarity with a suite of data science tools  master the practice  of good data science and  learn how to apply the method  and tool  to public health datasets   prerequisite  thi  course i  required for mph student  with concentration in public health data science and i  appropriate for master  student  in quantitative fields phd student  in computer science business psychology social science and science may also find thi  course useful there are no prerequisite  beyond those required for entry into the mph program   instructor chuck peperanney phd   visiting lecturer   department of biostatistic    a mcgavrangreenberg hall   phone    email cpeperanneyagbiomecom     teaching assistant tbd   office hours tbd   course website  httpsgithubcomchuckprbios   clas  days times location tuesday and thursday from am until pm   course overview thi  course will teach you the skill  to build and communicate endtoend data narratives  we will specifically be focusing on the following techology  tidyverse httpswwwtidyverseorg  jupyter httpsjupyterorg  docker httpswwwdockercom  git httpsgitscmcom and github httpsgithubcom  if time permits scikitlearn httpsscikitlearnorg and plotly httpsplotly   course format the course format will include two lecture  each week the lecture  will be supplemented with inclas  exercises case studies and example  of data science application  in public health settings   courseataglance the instructor reserve  the right to make change  to the syllabus including topics readings assignments and due dates any change  will be announced a  early a  possible for sessionbysession course schedule details please see the course website httpsgithubcomchuckprbios   course assignment  and assessment  thi  course will include the following graded assignment  that contribute to your final grade in the course for assignment description  and assignment grading rubrics please see below   assignment   pointspercentage         approximately weekly exercise      final project     participation      map of competencie  to learning objective  and assessment assignment  below you will see the competency you will develop in thi  course the learning objective  that comprise the competency and the assignment in which you will practice demonstrating thi  competency   competency select and use data visualization method  to interpret and communicate research results with the overall objective of conducting reproducible research both individually and in project teams   learning objectives  achieve proficiency in the r programming language  gain familiarity with a suite of data science tools including data    wrangling data quality control data cleaningediting exploratory data    analysis and data visualization  understand the principle  of good data science particularly reproducible    research  become familiar with several software tool  for best practice  in data    science including git docker jupyter and make  apply the data science tool  and principle  of best practice to real data    problem  in public health settings   assessment assignment  assignments will require use of r and data science tool  in solving real data science problems  project  will also require demonstration of the element  of reproducible research   final project will contain question  about the capabilitie  of different software tool  and question  about the principle  of good data science
    


```R
# remove stop words such as and, but, not, the

syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "and")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "but")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "not")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "the")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "to")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "that")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "they")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "you")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "are")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "for")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "will")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "this")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "thi")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "if")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "of")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "in")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "is")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "on")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "of")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "with")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "may")
syllabusCorpus <- tm_map(syllabusCorpus, removeWords, "all")


inspect(syllabusCorpus)
```

    Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "and"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "but"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "not"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "the"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "to"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "that"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "they"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "you"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "are"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "for"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "will"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "this"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "thi"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "if"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "of"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "in"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "is"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "on"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "of"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "with"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "may"):
    "transformation drops documents"Warning message in tm_map.SimpleCorpus(syllabusCorpus, removeWords, "all"):
    "transformation drops documents"

    <<SimpleCorpus>>
    Metadata:  corpus specific: 1, document level (indexed): 0
    Content:  documents: 1
    
    [1]  course description   course  be an introductory course  data science  i  required  mph student   concentration  public health data science  goal    course    achieve proficiency   r programming language  particular emphasi       tidyverse  gain familiarity  a suite  data science tools  master  practice   good data science   learn how  apply  method   tool   public health datasets   prerequisite    course i  required  mph student   concentration  public health data science  i  appropriate  master  student   quantitative fields phd student   computer science business psychology social science  science  also find   course useful there  no prerequisite  beyond those required  entry into  mph program   instructor chuck peperanney phd   visiting lecturer   department  biostatistic    a mcgavrangreenberg hall   phone    email cpeperanneyagbiomecom     teaching assistant tbd   office hours tbd   course website  httpsgithubcomchuckprbios   clas  days times location tuesday  thursday from am until pm   course overview   course  teach   skill   build  communicate endtoend data narratives  we  specifically be focusing   following techology  tidyverse httpswwwtidyverseorg  jupyter httpsjupyterorg  docker httpswwwdockercom  git httpsgitscmcom  github httpsgithubcom   time permits scikitlearn httpsscikitlearnorg  plotly httpsplotly   course format  course format  include two lecture  each week  lecture   be supplemented  inclas  exercises case studies  example   data science application   public health settings   courseataglance  instructor reserve   right  make change    syllabus including topics readings assignments  due dates any change   be announced a  early a  possible  sessionbysession course schedule details please see  course website httpsgithubcomchuckprbios   course assignment   assessment    course  include  following graded assignment   contribute  your final grade   course  assignment description   assignment grading rubrics please see below   assignment   pointspercentage         approximately weekly exercise      final project     participation      map  competencie   learning objective   assessment assignment  below   see  competency   develop    course  learning objective   comprise  competency   assignment  which   practice demonstrating   competency   competency select  use data visualization method   interpret  communicate research results   overall objective  conducting reproducible research both individually   project teams   learning objectives  achieve proficiency   r programming language  gain familiarity  a suite  data science tools including data    wrangling data quality control data cleaningediting exploratory data    analysis  data visualization  understand  principle   good data science particularly reproducible    research  become familiar  several software tool   best practice   data    science including git docker jupyter  make  apply  data science tool   principle   best practice  real data    problem   public health settings   assessment assignment  assignments  require use  r  data science tool   solving real data science problems  project   also require demonstration   element   reproducible research   final project  contain question  about  capabilitie   different software tool   question  about  principle   good data science
    


```R
# Create a Term Document Matrix

tdm_syllabus<-TermDocumentMatrix (syllabusCorpus)
tdm_syllabus
inspect(tdm_syllabus)



```


    <<TermDocumentMatrix (terms: 202, documents: 1)>>
    Non-/sparse entries: 202/0
    Sparsity           : 0%
    Maximal term length: 25
    Weighting          : term frequency (tf)


    <<TermDocumentMatrix (terms: 202, documents: 1)>>
    Non-/sparse entries: 202/0
    Sparsity           : 0%
    Maximal term length: 25
    Weighting          : term frequency (tf)
    Sample             :
                Docs
    Terms         1
      assignment  8
      competency  4
      course     17
      data       21
      health      5
      practice    4
      project     4
      public      5
      science    16
      tool        5
    


```R
TDM1<-as.matrix(tdm_syllabus, control=tf) #Convert this into a matrix format
TDM1
```


<table>
<caption>A matrix: 202 × 1 of type dbl</caption>
<thead>
	<tr><th></th><th scope=col>1</th></tr>
</thead>
<tbody>
	<tr><th scope=row>about</th><td>2</td></tr>
	<tr><th scope=row>achieve</th><td>2</td></tr>
	<tr><th scope=row>also</th><td>2</td></tr>
	<tr><th scope=row>analysis</th><td>1</td></tr>
	<tr><th scope=row>announced</th><td>1</td></tr>
	<tr><th scope=row>any</th><td>1</td></tr>
	<tr><th scope=row>application</th><td>1</td></tr>
	<tr><th scope=row>apply</th><td>2</td></tr>
	<tr><th scope=row>appropriate</th><td>1</td></tr>
	<tr><th scope=row>approximately</th><td>1</td></tr>
	<tr><th scope=row>assessment</th><td>3</td></tr>
	<tr><th scope=row>assignment</th><td>8</td></tr>
	<tr><th scope=row>assignments</th><td>2</td></tr>
	<tr><th scope=row>assistant</th><td>1</td></tr>
	<tr><th scope=row>become</th><td>1</td></tr>
	<tr><th scope=row>below</th><td>2</td></tr>
	<tr><th scope=row>best</th><td>2</td></tr>
	<tr><th scope=row>beyond</th><td>1</td></tr>
	<tr><th scope=row>biostatistic</th><td>1</td></tr>
	<tr><th scope=row>both</th><td>1</td></tr>
	<tr><th scope=row>build</th><td>1</td></tr>
	<tr><th scope=row>business</th><td>1</td></tr>
	<tr><th scope=row>capabilitie</th><td>1</td></tr>
	<tr><th scope=row>case</th><td>1</td></tr>
	<tr><th scope=row>change</th><td>2</td></tr>
	<tr><th scope=row>chuck</th><td>1</td></tr>
	<tr><th scope=row>clas</th><td>1</td></tr>
	<tr><th scope=row>cleaningediting</th><td>1</td></tr>
	<tr><th scope=row>communicate</th><td>2</td></tr>
	<tr><th scope=row>competencie</th><td>1</td></tr>
	<tr><th scope=row>...</th><td>...</td></tr>
	<tr><th scope=row>supplemented</th><td>1</td></tr>
	<tr><th scope=row>syllabus</th><td>1</td></tr>
	<tr><th scope=row>tbd</th><td>2</td></tr>
	<tr><th scope=row>teach</th><td>1</td></tr>
	<tr><th scope=row>teaching</th><td>1</td></tr>
	<tr><th scope=row>teams</th><td>1</td></tr>
	<tr><th scope=row>techology</th><td>1</td></tr>
	<tr><th scope=row>there</th><td>1</td></tr>
	<tr><th scope=row>those</th><td>1</td></tr>
	<tr><th scope=row>thursday</th><td>1</td></tr>
	<tr><th scope=row>tidyverse</th><td>2</td></tr>
	<tr><th scope=row>time</th><td>1</td></tr>
	<tr><th scope=row>times</th><td>1</td></tr>
	<tr><th scope=row>tool</th><td>5</td></tr>
	<tr><th scope=row>tools</th><td>2</td></tr>
	<tr><th scope=row>topics</th><td>1</td></tr>
	<tr><th scope=row>tuesday</th><td>1</td></tr>
	<tr><th scope=row>two</th><td>1</td></tr>
	<tr><th scope=row>understand</th><td>1</td></tr>
	<tr><th scope=row>until</th><td>1</td></tr>
	<tr><th scope=row>use</th><td>2</td></tr>
	<tr><th scope=row>useful</th><td>1</td></tr>
	<tr><th scope=row>visiting</th><td>1</td></tr>
	<tr><th scope=row>visualization</th><td>2</td></tr>
	<tr><th scope=row>website</th><td>2</td></tr>
	<tr><th scope=row>week</th><td>1</td></tr>
	<tr><th scope=row>weekly</th><td>1</td></tr>
	<tr><th scope=row>which</th><td>1</td></tr>
	<tr><th scope=row>wrangling</th><td>1</td></tr>
	<tr><th scope=row>your</th><td>1</td></tr>
</tbody>
</table>




```R
v <- sort(rowSums(TDM1),decreasing=TRUE)
d <- data.frame(word = names(v),freq=v)
shortlist <- head(d, 12)
shortlist

```


<table>
<caption>A data.frame: 12 × 2</caption>
<thead>
	<tr><th></th><th scope=col>word</th><th scope=col>freq</th></tr>
	<tr><th></th><th scope=col>&lt;fct&gt;</th><th scope=col>&lt;dbl&gt;</th></tr>
</thead>
<tbody>
	<tr><th scope=row>data</th><td>data      </td><td>21</td></tr>
	<tr><th scope=row>course</th><td>course    </td><td>17</td></tr>
	<tr><th scope=row>science</th><td>science   </td><td>16</td></tr>
	<tr><th scope=row>assignment</th><td>assignment</td><td> 8</td></tr>
	<tr><th scope=row>health</th><td>health    </td><td> 5</td></tr>
	<tr><th scope=row>public</th><td>public    </td><td> 5</td></tr>
	<tr><th scope=row>tool</th><td>tool      </td><td> 5</td></tr>
	<tr><th scope=row>competency</th><td>competency</td><td> 4</td></tr>
	<tr><th scope=row>practice</th><td>practice  </td><td> 4</td></tr>
	<tr><th scope=row>project</th><td>project   </td><td> 4</td></tr>
	<tr><th scope=row>research</th><td>research  </td><td> 4</td></tr>
	<tr><th scope=row>student</th><td>student   </td><td> 4</td></tr>
</tbody>
</table>




```R
library(ggplot2)
```


```R
p = ggplot(data = shortlist, aes(x = reorder(word, -freq), y=freq)) + geom_bar(stat="identity", color="blue", fill="white", width=0.7) 
p = p + theme(axis.text.x=element_text(angle=90))
p = p + ggtitle("The Twelve Most Frequent Terms in the Main Sections of the BIOS 512 Syllabus") +
  xlab("Terms") + ylab("Frequency")
p
```


![png](output_12_0.png)



```R

```

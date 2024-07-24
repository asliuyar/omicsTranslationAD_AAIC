---
source: Rmd
title: "Synapse and AD Knowledge Portal"
teaching: 40
exercises: 10
questions:
- "How to work with Synapse R client?"
- "How to work with data in AD Knowledge Portal?"
objectives:
- "Explain how to use Synapser Package."
- "Demonstrate how to locate data and metadata in the Portal."
- "Demonstrate how to download data from the Portal programmatically."
keypoints:
- "Use your Synapse login credentials to access the Portal."
- "Use Synapser package to download data from the Portal."
---



Author: Laura Heath / Sage Bionetworks


# Downloading and Exploring Data from Synapse

Before you begin, determine your working directory (get(wd) and set(wd)), and create two new folders within your preferred working directory entitled "data" and "results"

## Install and Load Packages

If you haven't already, install synapser (the Synapse R client), as well
as the tidyverse family of packages

~~~
# install synapser
install.packages("synapser", repos = c("http://ran.synapse.org", "http://cran.fhcrc.org"))
~~~
{: .language-r}



~~~
Installing package into '/Users/auyar/Library/R/arm64/4.3/library'
(as 'lib' is unspecified)
~~~
{: .output}



~~~
Warning: unable to access index for repository http://ran.synapse.org/bin/macosx/big-sur-arm64/contrib/4.3:
  cannot open URL 'http://ran.synapse.org/bin/macosx/big-sur-arm64/contrib/4.3/PACKAGES'
~~~
{: .warning}



~~~
installing the source package 'synapser'
~~~
{: .output}



~~~
# install tidyverse if you don't already have it
install.packages("tidyverse")
~~~
{: .language-r}



~~~
Installing package into '/Users/auyar/Library/R/arm64/4.3/library'
(as 'lib' is unspecified)
~~~
{: .output}



~~~
Error in contrib.url(repos, "source"): trying to use CRAN without setting a mirror
~~~
{: .error}
Load libraries

~~~
library(synapser)
~~~
{: .language-r}



~~~

TERMS OF USE NOTICE:
  When using Synapse, remember that the terms and conditions of use require that you:
  1) Attribute data contributors when discussing these data or results from these data.
  2) Not discriminate, identify, or recontact individuals or groups represented by the data.
  3) Use and contribute only data de-identified to HIPAA standards.
  4) Redistribute data only under these same terms of use.
~~~
{: .output}



~~~
library(tidyverse)
~~~
{: .language-r}



~~~
── Attaching core tidyverse packages ────────────────────────────────────────────────────────────────────────── tidyverse 2.0.0 ──
✔ dplyr     1.1.4     ✔ readr     2.1.5
✔ forcats   1.0.0     ✔ stringr   1.5.1
✔ ggplot2   3.5.1     ✔ tibble    3.2.1
✔ lubridate 1.9.3     ✔ tidyr     1.3.1
✔ purrr     1.0.2     
~~~
{: .output}



~~~
── Conflicts ──────────────────────────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
~~~
{: .output}



~~~
#library(clusterProfiler)
~~~
{: .language-r}
## Login to Synapse

Next, you will need to log in to your Synapse account.

*Login option 1*: Synapser takes credentials from your Synapse web session
If you are logged into the Synapse web browser, synapser will
automatically use your login credentials to log you in during your R
session! All you have to do is:


~~~
#synLogin()
~~~
{: .language-r}

If for whatever reason that didn’t work, try one of these options:

*Login option 2*: Synapse username and password In the code below, replace
the \<\> with your Synapse username and password.


~~~
#synLogin("<username>", "<password>")
~~~
{: .language-r}

*Login option 3*: Synapse PAT If you usually log in to Synapse with your
Google account, you will need to use a Synapser Personal Access Token
(PAT) to log in with the R client. Follow these instructions to generate
a personal access token, then paste the PAT into the code below. Make
sure you scope your access token to allow you to View, Download, and
Modify.


~~~
#synLogin(authToken = "<paste your personal access token here>")
~~~
{: .language-r}

























































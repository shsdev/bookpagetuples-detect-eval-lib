bookpagetuples-detect-eval-lib
==============================

Introduction
------------

DetectionResult evaluation against ground truth. The evaluation process first
creates the detection result and ground truth lists. It then counts each page
tuple from the detection result that is in the ground truth as correctly
identified tuple (true positive). Those that are not in the ground truth are
counted as incorrectly identified tuples (false positives), and finally,
those that are in the ground truth but not in the detection result are counted
as missed tuples (false negatives).

The precision is then calculated as the number of true positives (i.e. the 
number of items correctly labeled as duplicate page pairs) divided by the 
total number of elements assumed to be duplicate page pairs (i.e. the sum of 
true positives and false positives, which are items incorrectly labeled as 
being duplicate page pairs ). Recall is then defined as the number of 
true positives divided by the total number of elements of duplicate page 
pairs (i.e. the sum of true positives and false negatives, which are items 
have not been labeled as being duplicate page pairs but actually should have 
been).

The ground truth contains single page instances without duplicates and 
n-tuples (duplicates, triples, quadruples, etc.). n-tuples with n>2 are 
expanded, the result is a list of 2-tuples which is used to determine the
number of missed duplicates (false negatives).

Dependency
----------
There is an external dependency on the combinatoricslib:
    
    <!-- language: lang-xml -->
    <dependency>
        <groupId>org.paukov.combinatorics</groupId>
        <artifactId>combinatoricslib</artifactId>
        <version>0.2</version>
    </dependency>

Download the combinatoricslib jar from:

    http://combinatoricslib.googlecode.com/files/combinatoricslib-0.2.jar

and install it in your local repository:

    mvn install:install-file -Dfile=combinatoricslib-0.2.jar \
        -DgroupId=org.paukov.combinatorics -DartifactId=combinatoricslib \
        -Dversion=0.2 -Dpackaging=jar

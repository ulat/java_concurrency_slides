# Project Goals & Outcomes

In lectures this week, you learned about a new programming construct added in Java 8: streams. Java streams offer a functional way to perform operations over Java Collections, and include basically useful operations such as filter, map, reduce, and scan.

Parallel Java streams automatically parallelize the functional operations described above. A parallel Java stream is created by simply applying the parallel() operation to an existing Java stream. Any stream operation applied to a Java parallel stream may be executed using multiple threads as long as its parallel execution does not break the semantics of the operation.

In Demo Video 2 of Week 2, Professor Sarkar showed an example of analyzing student data using both imperative loops and functional streams, and showed how the parallel stream version was not only faster to finish but also much less verbose and error-prone. It is recommended you review this demo video before starting this mini-project.

In this mini-project, we will explore in that direction further by implementing parallel stream versions of several other imperative data analysis programs. Throughout this assignment you should feel free to refer to any useful Javadocs.

# Project Setup

Please refer to Mini-Project 0 for a description of the build and testing process used in this course.

Once you have downloaded and unzipped the provided project files using the gray button labeled miniproject_2.zip at the top of this description, you should see the project source code at:

miniproject_2/src/main/java/edu/coursera/parallel/StudentAnalytics.java
miniproject_2/src/main/java/edu/coursera/parallel/StudentAnalytics.java

and the project tests at

miniproject_2/src/test/java/edu/coursera/parallel/StudentAnalyticsTest.java.
miniproject_2/src/test/java/edu/coursera/parallel/StudentAnalyticsTest.java.

# Project Instructions

Your modifications should be done entirely inside of StudentAnalytics.java. You may not make any changes to the signatures of any public or protected methods inside of StudentAnalytics, or remove any of them. However, you are free to add any new methods you like. Any changes you make to StudentAnalyticsTest.java will be ignored in the final grading process.

Your main goals for this assignment are listed below. StudentAnalytics.java also contains helpful TODOs.

Implement StudentAnalytics.averageAgeOfEnrolledStudentsParallelStream to perform the same operations as averageAgeOfEnrolledStudentsImperative but using parallel streams.
Implement StudentAnalytics. mostCommonFirstNameOfInactiveStudentsParallelStream to perform the same operations as mostCommonFirstNameOfInactiveStudentsImperative but using parallel streams.
Implement StudentAnalytics. countNumberOfFailedStudentsOlderThan20ParallelStream to perform the same operations as countNumberOfFailedStudentsOlderThan20Imperative but using parallel streams. Note that any grade below a 65 is considered a failing grade for the purpose of this method.
You are free to refer to any online documentation that you find helpful. In particular, the documentation of the Java Stream class may be useful:

https://docs.oracle.com/javase/8/docs/api/java/util/stream/Stream.html

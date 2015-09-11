# cloudapp-mp2
Machine Programming Assignment for Cloud Application Course


To run :

export HADOOP_CLASSPATH=$JAVA_HOME/lib/tools.jar

hadoop com.sun.tools.javac.Main TopTitleStatistics.java -d build

jar -cvf TopTitleStatistics.jar -C build/ ./

hadoop jar TopTitleStatistics.jar TopTitleStatistics -D stopwords=/mp2/misc/stopwords.txt -D delimiters=/mp2/misc/delimiters.txt -D N=5 /mp2/titles /mp2/C-output

hadoop fs -cat /mp2/C-output/part*

hadoop fs -rm -r -f /mp2/A-output

hadoop fs -ls /mp2/A-output/

hadoop jar TitleCount.jar TitleCount -D stopwords=/mp2/misc/stopwords.txt -D delimiters=/mp2/misc/delimiters.txt /mp2/titles /mp2/A-output

hadoop jar TopTitles.jar TopTitles -D stopwords=/mp2/misc/stopwords.txt -D delimiters=/mp2/misc/delimiters.txt -D N=5 /mp2/titles /mp2/B-output


hadoop jar TopPopularLinks.jar TopPopularLinks -D N=5 /mp2/links /mp2/D-output

hadoop jar OrphanPages.jar OrphanPages /mp2/links /mp2/D-output

hadoop jar PopularityLeague.jar PopularityLeague -D league=/mp2/misc/league.txt /mp2/links /mp2/D-output 

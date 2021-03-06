# Gutenberg
A Content Based Recommender using Project Gutenberg's entire database of books

Team:  
Aniket Saoji  
Drew Hoo  
James LeDoux  

-----------

This project aims to classify texts based solely on content, and to form book recommendations using punctuation profiles, author name, book metadata, and content clustering using KNN, KMeans, and OLS regression. 

Results can be found in writeup.pdf

##Steps for Replication

### Data Collection
1. Run the shell script getBooks.sh to start pulling books from Project Gutenberg. Unzip the texts, then run strip_headers.py to get rid of the legal info in the headers and footers of all Project Gutenberg texts. This will take a while to run, and the entire text corpus may not be necessary (will be roughly 20gb in total). As an alternative, see the University of Michigan text corpus af 3000 books at http://web.eecs.umich.edu/~lahiri/gutenberg_dataset.html.

### Feature Extraction
1. Run in terminal: MoreEfficientPreprocessing.py. This creates an output file with '|' delimeted features. Runs sentiment analysis, takes punctuation profile, gets other basic features.

### Run TFIDF clustering
1. If set is small enough to run locally, run in terminal: /[usr dir]/spark-submit /[usr dir]/TFIDF_Kmeans.py "/[usr dir]/[data set input]/" "/[usr dir]/[output dir]". If using a larger text corpus, we recommend uploading the books to Amazon EC2 and running this script on Elastic MapReduce.
  - Generated outputs = file of cluster memberships. Format (BOOKID.txt, clusterID).

### Form Recommendations
1. run knn.py
- enter book title and author name exactly as entered in the data (it will ask you to try again if not)
- see 15 nearest neighbors to the book in question





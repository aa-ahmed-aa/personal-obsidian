https://stackoverflow.com/a/61416753/5701752

upon some investigation found that using flat function in some scripts that is running heavy sql queries to caclulate inconsistencies found that using this function is slowing this significantly 

also upon testing i was flatening (`.flat()`) results coming from sql query  this result is thousands and can be millions of nested rows so flatening this tribled the execution time for the script :(
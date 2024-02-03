Many of us have a C++ program that issues shortly after midnight the summary of the past day.  
It should issue the summary in a line appended to a file. That file should be in the csv format, for e.g. post processing in Excel.  
But you need to begin the line with a date identifier. And that identifier should be the day of yesterday (because you print it after midnight)  

I searched and did not find nice solutions.
So I dug into the guts of C++ ctime and propose that solution:

    //***Variables for Time***
    tm* timeinfo;  
    tm* yesterdaytimeinfo;  
    time_t now;
    time_t yesterdaynow;
    static char charbuff[120];  //Char buffer for many functions
     
     
    //*** In program ***
    yesterdaynow = now - 86400;
    yesterdaytimeinfo = localtime(&yesterdaynow);
    strftime(charbuff, 30, "%x ", yesterdaytimeinfo);
    println;
    print(charbuff);

That's it.

Enjoy !

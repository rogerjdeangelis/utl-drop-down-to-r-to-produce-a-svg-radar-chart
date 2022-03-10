# utl-drop-down-to-r-to-produce-a-svg-radar-chart
Drop down to r to produce a svg radar chart  
    %let pgm=utl-drop-down-to-r-to-produce-a-svg-radar-chart;

    Drop down to r to produce a svg radar chart

    To view svg plot (looks better locally)
    https://tinyurl.com/33y3vf68
    https://github.com/rogerjdeangelis/utl-drop-down-to-r-to-produce-a-svg-radar-chart/blob/main/rplots.svg

    github
    https://tinyurl.com/3fpvvtnn
    https://github.com/rogerjdeangelis/utl-drop-down-to-r-to-produce-a-svg-radar-chart

    see
    https://www.rgraph.net/svg/radar.html

    /*                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */
    options validvarname=upcase;

    libname sd1 "d:/sd1";

    data sd1.have;
     input math english biology music R_coding data_viz french physic statistic sport;
    cards4;
    20 20 20 20 20 20 20 20 20 20
    0 0 0 0 0 0 0 0 0 0
    5 7 2 15 2 8 18 19 20 15
    ;;;;
    run;quit;

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /* Up to 40 obs SD1.HAVE total obs=3 10MAR2022:16:20:03                                                                   */
    /*                                                                                                                        */
    /* Obs    MATH    ENGLISH    BIOLOGY    MUSIC    R_CODING    DATA_VIZ    FRENCH    PHYSIC    STATISTIC    SPORT           */
    /*                                                                                                                        */
    /*  1      20        20         20        20        20          20         20        20          20         20            */
    /*  2       0         0          0         0         0           0          0         0           0          0            */
    /*  3       5         7          2        15         2           8         18        19          20         15            */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    %utl_rbegin;
    parmcards4;
    library(fmsb)
    library(svglite)
    library(SASxport)
    library(haven)
    data<-read_sas("d:/sd1/have.sas7bdat");
    svglite("d:/svg/rplots.svg")
    radarchart( data  , axistype=1 ,
        #custom polygon
        pcol=rgb(0.2,0.5,0.5,0.9) , pfcol=rgb(0.2,0.5,0.5,0.5) , plwd=4 ,
        #custom the grid
        cglcol="grey", cglty=1, axislabcol="grey", caxislabels=seq(0,20,5), cglwd=0.8,
        #custom labels
        vlcex=0.8
        )
    ;;;;
    %utl_rend;

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */









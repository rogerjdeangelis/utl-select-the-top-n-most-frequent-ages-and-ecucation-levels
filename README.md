# utl-select-the-top-n-most-frequent-ages-and-ecucation-levels
Select the top three most frequent ages and ecucation levels 
    Select the top three most frequent ages and ecucation levels

    GitHub
    https://tinyurl.com/3fva52k7
    https://github.com/rogerjdeangelis/utl-select-the-top-n-most-frequent-ages-and-ecucation-levels

    /*
     _                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    data have;
      do subject=1 to 30;
        age = 16 + int(20*uniform(4321));
        educ= 12 + int(16*uniform(4321));
        output;
      end;
    run;quit;
    run;quit;

    /*                        _             _
      ___ __ _ ___  ___   ___| |_ _   _  __| |_   _
     / __/ _` / __|/ _ \ / __| __| | | |/ _` | | | |
    | (_| (_| \__ \  __/ \__ \ |_| |_| | (_| | |_| |
     \___\__,_|___/\___| |___/\__|\__,_|\__,_|\__, |
                                              |___/
    */

    Identify the top three most frequent education levels and ages
    I sorted the data to create a check

     SUBJECT    AGE    EDUC

        16       21     12
        21       27     12

        12       26     13
        15       22     13

         8       22     14  3rd most frequet ediucation lvel
         9       35     14
        27       20     14

         3       20     15
        13       33     15

         7       26     16  1st most frequent education level
        18       34     16
        20       20     16
        28       26     16

        19       29     17
        30       24     17
         4       20     19
        11       33     20
        22       17     21
        26       35     21
         5       19     22
         6       21     22

        10       28     23  2nd modt freqent education level
        17       31     23
        23       34     23

         1       20     24
         2       28     25
        24       17     26
        25       24     26
        14       31     27
        29       33     27

    /*           _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| `_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    */

      VAR     YEARS    SUBJECTS

      EDUC      16         4     Agrees with case study above
      EDUC      23         3
      EDUC      14         3

      AGE       20         5
      AGE       26         3
      AGE       33         3

    /*
     _ __  _ __ ___   ___ ___  ___ ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    */

    * create two views with desceding counts;

    proc sql;
      create
         view want_age as
      select
         'AGE ' as var
         ,age as years
         ,count(age) as subjects
      from
         have
      group
         by age
      order
         by subjects descending
    ;
      create
         view want_educ as
      select
         'EDUC' as var
         ,educ as years
         ,count(educ) as subjects
      from
         have
      group
         by educ
      order
         by subjects descending
    ;quit;

    * top 3 from each view;
     data                 ;
      set want_age(obs=3) want_educ(obs=3) ;
    run;quit;





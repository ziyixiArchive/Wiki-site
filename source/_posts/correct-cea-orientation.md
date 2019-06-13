---
title: correct_cea_orientation
toc: true
date: 2019-06-13 17:00:07
tags: cea
categories: Research note
---

## Overview

The cea data has mis-orientated before 09/2013. We have the [document](https://wiki.ziyixi.science/static/info/cmpaz_segment.txt) of how these stations are mis-orientated. (From Prof. Kai Tao and by Prof. Fenglin Niu) Dr. Chen has some data that have been processed before. So I'd like to compare the cmpaz of her processed data and the document mentioned above.

## Result

The data from the document has the form

```txt
#NET|STA|NO.EVENT|MEAN|STD|MEDIAN|MAD|STARTTIME|ENDTIME
```

### AH.BAS

```txt
AH|BAS|130|8.46|10.14|10.23|4.50|2008-03-11T14:37:00Z|2010-04-11T09:40:00Z
```

cmpaz = 1.000000e+01

### AH.BEB

```txt
AH|BEB|113|-4.82|20.58|-7.31|8.67|2007-10-02T03:43:00Z|2011-01-13T16:16:00Z
```

cmpaz = -7.000000e+00

### AH.DYN

```txt
AH|DYN|101|66.71|6.26|66.86|3.83|2007-08-27T17:11:00Z|2008-11-03T19:21:00Z
```

cmpaz = 6.500000e+01

### AH.FZL

```txt
#NET=AH,STA=FZL,MINCC=0.80,XYFILE=AH.FZL.XY
#NET|STA|NO.EVENT|MEAN|STD|MEDIAN|MAD|STARTTIME|ENDTIME
AH|FZL|3|-39.87|38.49|-60.75|3.94|2007-08-08T17:04:00Z|2007-08-15T20:22:00Z
AH|FZL|18|-20.44|29.88|-30.98|16.20|2007-09-12T11:10:00Z|2008-03-26T20:06:00Z
AH|FZL|3|3.09|87.01|14.27|103.34|2008-04-02T14:36:00Z|2008-04-10T04:29:00Z
AH|FZL|1|3.69|NA|3.69|0.00|2008-04-29T19:10:00Z|2008-04-29T19:10:00Z
AH|FZL|327|3.04|11.37|1.71|7.47|2008-05-02T01:33:00Z|2013-09-01T11:52:00Z
AH|FZL|0|NA|NA|NA|NA|NA|2013-09-01T11:52:00Z
AH|FZL||||||2013-09-01T11:52:00Z|NULL
```

cmpaz = -1.000000e+00

Here we don't have the data of the for the event 200804161919A.

### AH.HBE

```txt
AH|HBE|64|13.63|5.46|13.70|3.91|2007-08-01T17:08:00Z|2008-06-10T04:13:00Z
```

### AH.HEF

```txt
AH|HEF|58|-9.22|5.11|-9.29|3.71|2007-10-31T13:44:00Z|2010-02-01T22:28:00Z
```

cmpaz = -9.000000e+00

### AH.HSH

```txt
AH|HSH|108|-183.73|12.04|-180.53|5.63|2007-09-12T23:49:00Z|2010-05-27T17:14:00Z
```

cmpaz = -1.790000e+02

### AH.HUS

```txt
AH|HUS|59|-4.29|4.56|-4.26|2.56|2007-08-01T17:08:00Z|2008-07-06T01:00:00Z
```

cmpaz = 0.000000e+00

### AH.JZA

```txt
AH|JZA|96|0.13|16.51|2.94|9.54|2007-08-08T17:04:00Z|2010-03-05T16:07:00Z
```

cmpaz = 1.000000e+00

## Conclusion

It seems the mis-orientation data that Dr. Chen has used is slightly different from Dr. Tao has used. But they are similar to each other, only several degrees different.

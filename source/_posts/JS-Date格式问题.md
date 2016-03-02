title: JS Date格式问题
date: 2016-03-02 11:52:32
tags:
---

### Date格式问题

	new Date();
	//Fri Aug 21 2015 15:51:55 GMT+0800 (中国标准时间)

	new Date(1293879600000);
	new Date('2011-01-01T11:00:00') //chrome上表现为加12小时
	new Date('2011/01/01 11:00:00')
	new Date(2011,0,1,11,0,0)
	new Date('jan 01 2011,11 11:00:00')
	new Date('Sat Jan 01 2011 11:00:00')
	//Sat Jan 01 2011 11:00:00 GMT+0800 (中国标准时间)

	new Date('sss');
	new Date('2011/01/01T11:00:00');
	new Date('2011-01-01-11:00:00')
	new Date('1293879600000');
	//Invalid Date

	new Date('2011-01-01T11:00:00')-new Date('1992/02/11 12:00:12')
	//596069988000
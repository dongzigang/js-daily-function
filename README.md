# js-daily-function
js常用方法

```js
/**
 * 获取当前标准日期格式的年月日时分秒
 *@returns {String}  "2017-12-01 10:8:40"
 * */
function getNowFormatDate() {
    var date = new Date();
    var seperator1 = "-";
    var seperator2 = ":";
    var year = date.getFullYear();
    var month = date.getMonth() + 1;
    var strDate = date.getDate();
    if (month >= 1 && month <= 9) {
        month = "0" + month;
    }
    if (strDate >= 0 && strDate <= 9) {
        strDate = "0" + strDate;
    }
    var currentdate = year + seperator1 + month + seperator1 + strDate
            + " " + date.getHours() + seperator2 + date.getMinutes()
            + seperator2 + date.getSeconds();
    return currentdate;
}

/**
 * 字符串 0  1 转为布尔值
 * @param {string} "0"  "0"
 * @returns {boolean} 
 * */
function Str2Bool(str){
	num=parseInt(str)
	return Boolean(num)
}

/**
 * 布尔值 转为 数字 0  1 
 * @param {boolean}
 * @returns {number}
 * */
function Bool2Str(bool){
	return Number(bool)
}


/**
 * 返回一个对象的深复制
 * @param {object}
 * @returns {object}
 **/
function deepCopy(obj){
	var newObj={}
	for (var i in obj) {
		newObj[i] = obj[i]
	}
	return newObj
}

/**
 * 返回传入日期的下一天
 * @param   {string}  2017-11-23
 * @returns {string}  2017-11-24
 * */
function toTomorrow (date) {
	var today=date+" "+"00:00:00"
	var timestamp = Date.parse(new Date(today))
	var tomorrow = timestamp + 86400000
	
	var newDate = fmtDate(tomorrow)
	return newDate
}
function fmtDate(obj){
    var date =  new Date(obj);
    var y = 1900+date.getYear();
    var m = "0"+(date.getMonth()+1);
    var d = "0"+date.getDate();
    return y+"-"+m.substring(m.length-2,m.length)+"-"+d.substring(d.length-2,d.length);
}

/**
 * 去掉日期的字符串的横线方便比较大小
 * @param {string} "2017-11-27"
 * @return {number} 20171127
 * */
function date2Num(date){
	var test = new RegExp(/-/g);
	var dateNum = parseInt(date.replace(test,""));
	return dateNum
}


/**
 *判断每个月有多少天
 * @param {number}  12
 * @return {number} 31
 * */
function getCountDays(month) {
    var curDate = new Date();
    /* 获取当前月份 */
    var curMonth = month;
    /*  生成实际的月份: 由于curMonth会比实际月份小1, 故需加1 */
    curDate.setMonth(curMonth);
    /* 将日期设置为0, 这里为什么要这样设置, 我不知道原因, 这是从网上学来的 */
    curDate.setDate(0);
    /* 返回当月的天数 */
    return curDate.getDate();
}


/**
 * 判断是否为Null
 * @param {object}
 * @returns {Boolean}
 */
function isNull(object){
    if(object == null || typeof object == "undefined"){
        return true;
    }
    return false;
};

/**
 * 根据日期字符串获取星期几
 * @param {dateString} 日期字符串（如：2016-12-29），为空时为用户电脑当前日期
 * @returns {String}
 */
function getWeek(dateString) {
    var date;
    if(isNull(dateString)){
        date = new Date();
    }else{
        var dateArray = dateString.split("-");
        date = new Date(dateArray[0], parseInt(dateArray[1] - 1), dateArray[2]);
    }
    return "星期" + "日一二三四五六".charAt(date.getDay());
}
/**
*获取当前链接中的参数
*@param {string} name 要获取的参数名
*@param {function} url   decodeURI(window.location)    传入这个参数可以正确的显示参数中的汉字
*@returns {string} 
*/
function getUrlParam(name,url){
    var target = url ? url.substr(url.indexOf('?')) : window.location.search;
    var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)", "i");
    var r = target.substr(1).match(reg);
    if (r != null) return (r[2]);
}

```
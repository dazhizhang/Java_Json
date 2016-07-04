# Java_Json

1. 只需要解析部分属性，尤其是字符串属性，用 org.json就可以了。

import org.json.JSONArray;
import org.json.JSONException;
import org.json.JSONObject;

org json可以把json字符串中的属性取出来，如果想解析URL页面属性，先读取URL内容。
如果想解析文件，先读文件。
这个方法的好处是不用定义class，取部分属性的话可以直接取出来。
支持object的嵌套。

			String rootUrl = "https://api.goshippo.com/v1/tracks/usps/";
		    JSONObject json = new JSONObject(readUrl(rootUrl+uspsnumber));

		    ////////////////////////////////////////////////////////////////////////////////////////////////
		    my_package.tracking_number = (String)json.get("tracking_number");
		    
		    ////////////////////////////////////////////////////////////////////////////////////////////////
		    my_package.carrier = (String)json.get("carrier");
            
		    ////////////////////////////////////////////////////////////////////////////////////////////////
		    JSONObject tracking_status = (JSONObject)json.get("tracking_status");
		    my_package.tracking_status.object_created = (String)tracking_status.get("object_created");
		    my_package.tracking_status.status = (String)tracking_status.get("status");
		    



2. 如果需要把字符串转成一个完整object，用com.alibaba.fastjson.JSON;
定义好class以后，一行代码就搞定了。
String content = "json str";
Classname result =  JSON.parseObject(content, Classname.class);

这个方支持不定长的数组。



3. 

如果要把json字符串写入文件进行保存, 可以使用 org.apache.commons.io.FileUtils

先使用 com.alibaba.fastjson.JSON 把一个object转化成json字符串，

再用 FileUtils.writeStringToFile 方法把json字符串写入文件

ClassABC objectabc;

T t = objectabc;

String json = JSON.toJSONString(t, true);  
// 这个转换对于Class的memeber还有member的命名有一些规范，member名字首字母要小写
get和set function以get，set后面加首字母大写的member名字来命名。

FileUtils.writeStringToFile(filepath, json, Constants.UTF8);

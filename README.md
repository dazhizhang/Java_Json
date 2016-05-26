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

这个方还支持不定长的数组。

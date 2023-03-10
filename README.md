# SpringBootCode(스프링부트입문 길벗코드)

코드2-1
@RestController
class App {

	@RequestMapping("/")
	def home() {
		"Hello!!"
	}
}

코드2-2
@RestController
class App {

	@RequestMapping("/")
	def home() {
		def header = "<html><body>"
		def footer = "</body></html>"
		def content = "<h1>Hello!</h1><p>this is html content.</p>"
		
		header + content + footer
	}
}

코드2-3
<!DOCTYPE html>
<html>
<head>
	<meta http-equiv="Content-type" 
		content="text/html; charset=utf-8" />
	<title>Index Page</title>
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	</style>
</head>
<body>
	<h1>Hello!</h1>
	<p>this is sample web page.</p>
</body>
</html>

코드2-4
@Grab("thymeleaf-spring4")

@Controller
class App {

	@RequestMapping("/")
	@ResponseBody
	def home(ModelAndView mav) {
		mav.setViewName("home")
		mav
	}
}

코드2-5
html {
	head {
		title('index page')
	}
	body {
		h1('Hello')
		p('this is Groovy template!')
	}
}

코드2-6
html {
	head {
		title('index page')
	}
	body {
		h1('Hello')
		p('this is Groovy template!')
		div(){
			a(href:'http://google.com'){
				yield 'google link'
			}
		}
	}
}

코드2-7
<body>
	<h1>Hello!</h1>
	<p th:text="${msg}">this is sample.</p>
</body>

코드2-8
@RequestMapping("/")
@ResponseBody
def home(ModelAndView mav) {
	mav.setViewName("home")
	mav.addObject("msg","Hello! this is sample page.")
	mav
}

코드2-9
mav.addObject("msg","안녕하세요!")

코드2-10
mav.addObject("msg","\uc548\ub155\ud558\uc138\uc694?")  

코드2-11
<body>
	<h1>Hello!</h1>
	<p th:text="${msg}">${msg}</p>
	<form method="post" action="/send">
		<input type="text" name="text1" th:value="${value}" />
		<input type="submit" value="Click" />
	</form>
</body>

코드2-12
@Grab("thymeleaf-spring4")

@Controller
class App {

	@RequestMapping(value="/", method=RequestMethod.GET)
	@ResponseBody
	def home(ModelAndView mav) {
		mav.setViewName("home")
		mav.addObject("msg","please write your name...")
		mav
	}

	@RequestMapping(value="/send", method=RequestMethod.POST)
	@ResponseBody
	def send(@RequestParam("text1")String str, ModelAndView mav) {
		mav.setViewName("home")
		mav.addObject("msg","Hello, " + str + "!!")
		mav.addObject("value",str)
		mav
	}
}

코드3-1
package com.tuyano.springboot;

public class App 
{
    public static void main( String[] args )
    {
        System.out.println( "Hello World!" );
    }
}

코드3-2
<project xmlns="http://maven.apache.org/POM/4.0.0" 
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
    http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.tuyano.springboot</groupId>
  <artifactId>MyBootApp</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>jar</packaging>

  <name>MyBootApp</name>
  <url>http://maven.apache.org</url>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>

  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>3.8.1</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>

코드3-3
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" 
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
	http://maven.apache.org/xsd/maven-4.0.0.xsd">

	<modelVersion>4.0.0</modelVersion>

	<groupId>com.tuyano.springboot</groupId>
	<artifactId>MyBootApp</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>MyBootApp</name>
	<description>sample project for Spring Boot</description>

	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>1.3.0.RELEASE</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<java.version>1.8</java.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
		
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>
	
	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>
	
</project>

코드3-4
package com.tuyano.springboot;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MyBootAppApplication {

	public static void main(String[] args) {
		SpringApplication.run(MyBootAppApplication.class, args);
	}
}

코드3-5
package com.tuyano.springboot;

public class HeloController {

}

코드3-6
package com.tuyano.springboot;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HeloController {

	@RequestMapping("/")
	public String index() {
		return "Hello Spring-Boot World!!";
	}
}

코드3-7
package com.tuyano.springboot;

import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HeloController {

	@RequestMapping("/{num}")
	public String index(@PathVariable int num) {
		int res = 0;
		for(int i = 1;i <= num;i++)
			res += i;
		return "total: " + res;
	}
}

코드3-8
package com.tuyano.springboot;

import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HeloController {
	String[] names = {"kim",
			"lee","park",
			"choi","jo"};
	String[] mails = {"kim@tuuyano.com",
			"lee@flower","park@yamda",
			"choi@happy","jo@baseball"};

	@RequestMapping("/{id}")
	public DataObject index(@PathVariable int id) {
		return new DataObject(id,names[id],mails[id]);
	}
	
}

class DataObject {
	private int id;
	private String name;
	private String value;
	
	public DataObject(int id, String name, String value) {
		super();
		this.id = id;
		this.name = name;
		this.value = value;
	}

	public int getId() { return id; }

	public void setId(int id) { this.id = id; }

	public String getName() { return name; }

	public void setName(String name) {
		this.name = name;
	}

	public String getValue() {
		return value;
	}

	public void setValue(String value) {
		this.value = value;
	}
	
}

코드3-9
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>

코드3-10
package com.tuyano.springboot;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
public class HeloController {
	
	@RequestMapping("/")
	public String index() {
		return "index";
	}
	
}

코드3-11
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	</style>
</head>
<body>
	<h1>Helo page</h1>
	<p class="msg">this is Thymeleaf sample page.</p>
</body>
</html>

코드3-12
<body>
	<h1>Helo page</h1>
	<p class="msg" th:text="${msg}"></p>
</body>

코드3-13
package com.tuyano.springboot;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
public class HeloController {
	
	@RequestMapping("/{num}")
	public String index(@PathVariable int num, Model model) {
		int res = 0;
		for(int i = 1;i <= num;i++)
			res += i;
		model.addAttribute("msg", "total: " + res);
		return "index";
	}
	
}

코드3-14
package com.tuyano.springboot;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.servlet.ModelAndView;

@Controller
public class HeloController {
	
	@RequestMapping("/{num}")
	public ModelAndView index(@PathVariable int num, 
			ModelAndView mav) {
		int res = 0;
		for(int i = 1;i <= num;i++)
			res += i;
		mav.addObject("msg", "total: " + res);
		mav.setViewName("index");
		return mav;
	}
	
}

코드3-15
<body>
	<h1>Helo page</h1>
	<p th:text="${msg}">please wait...</p>
	<form method="post" action="/">
		<input type="text" name="text1" th:value="${value}" />
		<input type="submit" value="Click" />
	</form>
</body>

코드3-16
package com.tuyano.springboot;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.servlet.ModelAndView;

@Controller
public class HeloController {
	
	@RequestMapping(value="/", method=RequestMethod.GET)
	public ModelAndView index(ModelAndView mav) {
		mav.setViewName("index");
		mav.addObject("msg","お이름を書いて送信してください。");
		return mav;
	}
	
	@RequestMapping(value="/", method=RequestMethod.POST)
	public ModelAndView send(@RequestParam("text1")String str, 
			ModelAndView mav) {
		mav.addObject("msg","こんにちは、" + str + "さん！");
		mav.addObject("value",str);
		mav.setViewName("index");
		return mav;
	}
}

코드3-17
<!-- pre { font-size:13pt; color:gray; padding:5px 10px; 
		border:1px solid gray; } を<style>に追加 -->
<body>
	<h1>Helo page</h1>
	<pre th:text="${msg}">please wait...</pre>
	<form method="post" action="/">
		<div>
		<input type="checkbox" id="check1" name="check1" />
		<label for="check1">チェック</label>
		</div>
		<div>
		<input type="radio" id="radioA" name="radio1" value="male" />
		<label for="radioA">남성</label>
		</div>
		<div>
		<input type="radio" id="radioB" name="radio1" value="female" />
		<label for="radioB">여성</label>
		</div>
		<div>
		<select id="select1" name="select1" size="4">
			<option value="Windows">Windows</option>
			<option value="Mac">Mac</option>
			<option value="Linux">Linux</option>
		</select>
		<select id="select2" name="select2" size="4" multiple="multiple">
			<option value="Android">Android</option>
			<option value="iphone">iPhone</option>
			<option value="Winfone">Windows Phone</option>
		</select>
		</div>
		<input type="submit" value="Click" />
	</form>
</body>

코드3-18
package com.tuyano.springboot;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.servlet.ModelAndView;

@Controller
public class HeloController {
	
	@RequestMapping(value="/", method=RequestMethod.GET)
	public ModelAndView index(ModelAndView mav) {
		mav.setViewName("index");
		mav.addObject("msg","フォームを送信下さい。");
		return mav;
	}
	
	@RequestMapping(value="/", method=RequestMethod.POST)
	public ModelAndView send(
		@RequestParam(value="check1",required=false)boolean check1,
		@RequestParam(value="radio1",required=false)String radio1,
		@RequestParam(value="select1",required=false)String select1,
		@RequestParam(value="select2",required=false)String[] select2,
		ModelAndView mav) {
		
		String res = "";
		try {
			res = "check:" + check1 +
				" radio:" + radio1 +
				" select:" + select1 + 
				"\nselect2:";
		} catch (NullPointerException e) {}
		try {
			res += select2[0];
			for(int i = 1;i < select2.length;i++)
				res += ", " + select2[i];
		} catch (NullPointerException e) {
			res += "null";
		}
		mav.addObject("msg",res);
		mav.setViewName("index");
		return mav;
	}
	
}

코드3-19
<body>
	<h1>Helo page</h1>
</body>

코드3-20
package com.tuyano.springboot;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.servlet.ModelAndView;

@Controller
public class HeloController {
	
	@RequestMapping("/")
	public ModelAndView index(ModelAndView mav) {
		mav.setViewName("index");
		return mav;
	}
	@RequestMapping("/other")
	public String other() {
		 return "redirect:/";
	}
	
	@RequestMapping("/home")
	public String home() {
		return "forward:/";
	}

}

코드4-1
<body>
	<h1>Helo page</h1>
	<p th:text="${new java.util.Date().toString()}"></p>
</body>

코드4-2
<body>
	<h1>Helo page</h1>
	<p th:text="${#dates.format(new java.util.Date(),'dd/MMM/yyyy HH:mm')}"></p>
	<p th:text="${#numbers.formatInteger(1234,7)}"></p>
	<p th:text="${#strings.toUpperCase('Welcome to Spring.')}"></p>
</body>

코드4-3
<body>
	<h1>Helo page</h1>
	<p th:text="'from parameter... id=' + ${param.id[0] + ',name=' + param.name[0]}"></p>
</body>
코드 4-4
content.title=message sample page.
content.message=this is sample message from properties.

코드4-5
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:text="#{content.message}"></p>
</body>

코드4-6
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p><a th:href="@{'/home/' + ${param.id[0]}}">link</a></p>
</body>

코드4-7
@RequestMapping("/")
public ModelAndView index(ModelAndView mav) {
	mav.setViewName("index");
	mav.addObject("msg","current data.");
	DataObject obj = new DataObject(123, "lee","lee@flower");
	mav.addObject("object",obj);
	return mav;
}

코드4-8
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	tr { margin:5px; }
	th { padding:5px; color:white; background:darkgray; }
	td { padding:5px; color:black; background:#e0e0ff; }
	</style>
</head>
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:text="${msg}">message.</p>
	<table th:object="${object}">
		<tr><th>ID</th><td th:text="*{id}"></td></tr>
		<tr><th>NAME</th><td th:text="*{name}"></td></tr>
		<tr><th>MAIL</th><td th:text="*{value}"></td></tr>
	</table>
</body>
</html>

코드4-9
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<div th:object="${object}">
		<p th:text="|my name is *{name}. mail address is *{value}.|">message.</p>
	</div>
</body>

코드4-10
@RequestMapping("/")
public ModelAndView index(ModelAndView mav) {
	mav.setViewName("index");
	mav.addObject("msg","message 1<hr/>message 2<br/>message 3");
	return mav;
}

코드4-11
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:text="${msg}">message.</p>
</body>

코드4-12
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:utext="${msg}">message.</p>
</body>

코드4-13
@RequestMapping("/{id}")
public ModelAndView index(@PathVariable int id,
		ModelAndView mav) {
	mav.setViewName("index");
	mav.addObject("id",id);
	mav.addObject("check",id % 2 == 0);
	mav.addObject("trueVal","Even number!");
	mav.addObject("falseVal","Odd number...");
	return mav;
}

코드4-14
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:text="${id} + ' is ' + (${check} ? ${trueVal} : ${falseVal})"></p>
</body>

코드4-15
@RequestMapping("/{id}")
public ModelAndView index(@PathVariable int id,
		ModelAndView mav) {
	mav.setViewName("index");
	mav.addObject("id",id);
	mav.addObject("check",id >= 0);
	mav.addObject("trueVal","POSITIVE!");
	mav.addObject("falseVal","negative...");
	return mav;
}

코드4-16
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:if="${check}" th:text="${id} + ' is ' + ${trueVal}">message.</p>
	<p th:unless="${check}" th:text="${id} + ' is ' + ${falseVal}">message.</p>
</body>

코드4-17
@RequestMapping("/{month}")
public ModelAndView index(@PathVariable int month,
		ModelAndView mav) {
	mav.setViewName("index");
	int m = Math.abs(month) % 12;
	m = m == 0 ? 12 : m;
	mav.addObject("month",m);
	mav.addObject("check",Math.floor(m / 3));
	return mav;
}

코드4-18
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<div th:switch="${check}">
		<p th:case="0" th:text="|${month} - Winter|"></p>
		<p th:case="1" th:text="|${month} - Spring|"></p>
		<p th:case="2" th:text="|${month} - Summer|"></p>
		<p th:case="3" th:text="|${month} - Autumn|"></p>
		<p th:case="4" th:text="|${month} - Winter|"></p>
		<p th:case="*">...?</p>
	</div>
</body>

코드4-19
@RequestMapping("/")
public ModelAndView index(ModelAndView mav) {
	mav.setViewName("index");
	ArrayList<String[]> data = new ArrayList<String[]>();
	data.add(new String[]{"park","park@yamada","090-999-999"});
	data.add(new String[]{"lee","lee@flower","080-888-888"});
	data.add(new String[]{"choi","choi@happy","080-888-888"});
	mav.addObject("data",data);
	return mav;
}

코드4-20
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<table>
		<tr>
			<th>NAME</th>
			<th>MAIL</th>
			<th>TEL</th>
		</tr>
		<tr th:each="obj:${data}">
			<td th:text="${obj[0]}"></td>
			<td th:text="${obj[1]}"></td>
			<td th:text="${obj[2]}"></td>
		</tr>
	</table>
</body>

코드4-21
@RequestMapping("/{num}")
public ModelAndView index(@PathVariable int num,
		ModelAndView mav) {
	mav.setViewName("index");
	mav.addObject("num",num);
	if (num >= 0){
		mav.addObject("check","num >= data.size() ? 0 : num");
	} else {
		mav.addObject("check","num <= data.size() * -1 ? 0 : num * -1");
	}
	ArrayList<DataObject> data = new ArrayList<DataObject>();
	data.add(new DataObject(0,"park","park@yamada"));
	data.add(new DataObject(1,"lee","lee@flower"));
	data.add(new DataObject(2,"choi","choi@happy"));
	mav.addObject("data",data);
	return mav;
}

코드4-22
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:text="|expression[ ${check} ]|"></p>
	<table th:object="${data.get(__${check}__)}">
		<tr><th>ID</th><td th:text="*{id}"></td></tr>
		<tr><th>NAME</th><td th:text="*{name}"></td></tr>
		<tr><th>MAIL</th><td th:text="*{value}"></td></tr>
	</table>
</body>

코드4-23
@RequestMapping("/")
public ModelAndView index(ModelAndView mav) {
	mav.setViewName("index");
	ArrayList<DataObject> data = new ArrayList<DataObject>();
	data.add(new DataObject(0,"park","park@yamada"));
	data.add(new DataObject(1,"lee","lee@flower"));
	data.add(new DataObject(2,"choi","choi@happy"));
	mav.addObject("data",data);
	return mav;
}

코드4-24
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<table th:inline="text">
		<tr>
		<th>ID</th>
		<th>NAME</th>
		<th>MAIL</th>
		</tr>
		<tr th:each="obj : ${data}">
		<td>[[${obj.id}]]</td>
		<td>[[${obj.name}]]</td>
		<td>[[${obj.value}]]</td>
		</tr>
	</table>
</body>

코드4-25
@RequestMapping("/{tax}")
public ModelAndView index(@PathVariable int tax,
		ModelAndView mav) {
	mav.setViewName("index");
	mav.addObject("tax",tax);
	return mav;
}

코드4-26
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	</style>
	<script th:inline="javascript">
	function action(){
		var val = document.getElementById("text1").value;
		var res = parseInt(val * ((100 + /*[[${tax}]]*/) / 100));
		document.getElementById("msg").innerHTML = 
			"include tax: " + res;
	}
	</script>
</head>
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p id="msg"></p>
	<input type="text" id="text1" />
	<button onclick="action()">click</button>
</body>
</html>

코드4-27
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>part page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	</style>
	<style th:fragment="frag_style">
	div.fragment {
		border:solid 3px lightgray;
		padding:0px 20px;
	}
	</style>
</head>
<body>
	<h1>Part page</h1>
	<div th:fragment="frag_body">
		<h2>fragment</h2>
		<div class="fragment">
			<p>this is fragment content.</p>
			<p>sample message...</p>
		</div>
	</div>
</body>
</html>

코드4-28
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	</style>
	<style th:include="part :: frag_style"></style>
</head>
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<div th:include="part :: frag_body">
		<p>this is orginal content.</p>
	</div>
</body>
</html>

코드4-29
@RequestMapping("/")
public ModelAndView index(ModelAndView mav) {
	mav.setViewName("index");
	return mav;
}

코드4-30
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>

코드4-31
<dependency>
	<groupId>org.apache.tomcat.embed</groupId>
	<artifactId>tomcat-embed-jasper</artifactId>
</dependency>

코드4-32
spring.mvc.view.prefix: /WEB-INF/jsp/
spring.mvc.view.suffix: .jsp

코드4-33
<%@page import="java.util.Date"%>
<%@page import="java.text.SimpleDateFormat"%>
<%@ page language="java" 
	contentType="text/html; charset=utf-8"
    pageEncoding="utf-8"%>
<!DOCTYPE html PUBLIC 
	"-//W3C//DTD HTML 4.01 Transitional//EN" 
	"http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" 
	content="text/html; charset=utf-8">
<title>JSP Index Page</title>
</head>
<body>
	<h1>Index page</h1>
	<p>this is JSP sample page.</p>
	<%=new SimpleDateFormat("yyyy년 MM월 dd일").format(new Date()) %>
</body>
</html>

코드4-34
@RequestMapping("/")
public String index() {
	return "index";
}

코드4-35
<body>
	<h1>Index page</h1>
	<p>${val}</p>
	<form method="post" action="/">
		<input type="text" name="text1">
		<input type="submit">
	</form>
</body>

코드4-36
@RequestMapping(value="/", method=RequestMethod.GET)
public ModelAndView index(ModelAndView mav) {
	mav.setViewName("index");
	mav.addObject("val", "please type...");
	return mav;
}

@RequestMapping(value="/", method=RequestMethod.POST)
public ModelAndView send(@RequestParam String text1,
		ModelAndView mav) {
	mav.setViewName("index");
	mav.addObject("val", "you typed: '" + text1 + "'.");
	return mav;
}

코드4-37
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-groovy-templates</artifactId>
</dependency>

코드4-38
html {
	head {
		title('Groovy Page')
		style('''
			h1 { font-size:18pt; font-weight:bold; color:gray; }
			body { font-size:13pt; color:gray; margin:5px 25px; }			
		''')
	}
	body {
		h1('Index Page')
		p('This is Groovy sample page.')
	}
}

코드4-39
@RequestMapping("/")
public ModelAndView index(ModelAndView mav) {
	mav.setViewName("index");
	return mav;
}

코드4-40
body {
	h1('Index Page')
	p(msg)
	form(method:'post',action:'/'){
		input(type:'text',name:'num')
		input(type:'submit')
	}
}

코드4-41
@RequestMapping(value="/", method=RequestMethod.GET)
public ModelAndView index(ModelAndView mav) {
	mav.setViewName("index");
	mav.addObject("msg", "type a number...");
	return mav;
}

@RequestMapping(value="/", method=RequestMethod.POST)
public ModelAndView send(@RequestParam int num,
		ModelAndView mav) {
	mav.setViewName("index");
	int total = 0;
	for(int i = 1;i <=num;i++)
		total += i;
	mav.addObject("msg", "total: " + total + " !!");
	return mav;
}

코드4-42
@RequestMapping("/")
public ModelAndView index(ModelAndView mav) {
	mav.setViewName("index");
	mav.addObject("msg","data table.");
	ArrayList<DataObject> data = new ArrayList<DataObject>();
	data.add(new DataObject(0,"park","park@yamada"));
	data.add(new DataObject(1,"lee","lee@flower"));
	data.add(new DataObject(2,"choi","choi@happy"));
	mav.addObject("data",data);
	return mav;
}

코드4-43
html {
	head {
		title('Groovy Page')
		style('''
			h1 { font-size:18pt; font-weight:bold; color:gray; }
			body { font-size:13pt; color:gray; margin:5px 25px; }			
			tr { margin:5px; }
			th { padding:5px; color:white; background:darkgray; }
			td { padding:5px; color:black; background:#e0e0ff; }
			''')
	}
	body {
		h1('Index Page')
		p(msg)
		table {
			tr {
				th('ID')
				th('NAME')
				th('MAIL')
			}
			data.each{obj ->
				tr {
					td(obj.id)
					td(obj.name)
					td(obj.value)
				}
			}
		}
	}
}

코드5-1
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
	<groupId>org.hsqldb</groupId>
	<artifactId>hsqldb</artifactId>
	<scope>runtime</scope>
</dependency>

코드5-2
package com.tuyano.springboot;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.Table;

@Entity
@Table(name="mydata")
public class MyData {

	@Id
	@GeneratedValue(strategy = GenerationType.AUTO)
	@Column
	private long id;
	
	@Column(length = 50, nullable = false)
	private String name;

	@Column(length = 200, nullable = true)
	private String mail;

	@Column(nullable = true)
	private Integer age;
	
	@Column(nullable = true)
	private String memo;

	public long getId() {
		return id;
	}
	public void setId(long id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}

	public String getMail() {
		return mail;
	}
	public void setMail(String mail) {
		this.mail = mail;
	}

	public Integer getAge() {
		return age;
	}
	public void setAge(Integer age) {
		this.age = age;
	}

	public String getMemo() {
		return memo;
	}
	public void setMemo(String memo) {
		this.memo = memo;
	}
}

코드5-3
package com.tuyano.springboot.repositories;

public interface MyDataRepository {

}


코드5-4
package com.tuyano.springboot.repositories;

import com.tuyano.springboot.MyData;

import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface MyDataRepository  extends JpaRepository<MyData, Long> {
	
}

코드5-5
package com.tuyano.springboot;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.servlet.ModelAndView;

import com.tuyano.springboot.repositories.MyDataRepository;

@Controller
public class HeloController {
	
	@Autowired
	MyDataRepository repository;

	@RequestMapping("/")
	public ModelAndView index(ModelAndView mav) {
		mav.setViewName("index");
		mav.addObject("msg","this is sample content.");
		Iterable<MyData> list = repository.findAll();
		mav.addObject("data",list);
		return mav;
	}

}

　코드5-6
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	pre { border: solid 3px #ddd; padding: 10px; }
	</style>
</head>
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<pre th:text="${data}"></pre>
</body>
</html>

코드5-7
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	tr { margin:5px; }
	th { padding:5px; color:white; background:darkgray; }
	td { padding:5px; color:black; background:#e0e0ff; }
	</style>
</head>
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<table>
	<form method="post" action="/" th:object="${formModel}">
	<tr><td><label for="name">이름</label></td>
		<td><input type="text" name="name" th:value="*{name}" /></td></tr>
	<tr><td><label for="age">연령</label></td>
		<td><input type="text" name="age"  th:value="*{age}" /></td></tr>
	<tr><td><label for="mail">메일</label></td>
		<td><input type="text" name="mail"  th:value="*{mail}" /></td></tr>
	<tr><td><label for="memo">메모</label></td>
	<td><textarea name="memo"  th:text="*{memo}" 
				cols="20" rows="5"></textarea></td></tr>
	<tr><td></td><td><input type="submit" /></td></tr>
	</form>
	</table>
	<hr/>
	<table>
	<tr><th>ID</th><th>이름</th></tr>
	<tr th:each="obj : ${datalist}">
		<td th:text="${obj.id}"></td>
		<td th:text="${obj.name}"></td>
	</tr>
	</table>
</body>
</html>

코드5-8
package com.tuyano.springboot;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.transaction.annotation.Transactional;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.servlet.ModelAndView;

import com.tuyano.springboot.repositories.MyDataRepository;

@Controller
public class HeloController {
	
	@Autowired
	MyDataRepository repository;
	
	@RequestMapping(value = "/", method = RequestMethod.GET)
	public ModelAndView index(
			@ModelAttribute("formModel") MyData mydata, 
			ModelAndView mav) {
		mav.setViewName("index");
		mav.addObject("msg","this is sample content.");
		Iterable<MyData> list = repository.findAll();
		mav.addObject("datalist",list);
		return mav;
	}

	@RequestMapping(value = "/", method = RequestMethod.POST)
	@Transactional(readOnly=false)
	public ModelAndView form(
			@ModelAttribute("formModel") MyData mydata, 
			ModelAndView mav) {
		repository.saveAndFlush(mydata);
		return new ModelAndView("redirect:/");
	}

}

코드5-9
// import javax.annotation.PostConstruct; 코드 상단에 추가

@PostConstruct
public void init(){
	MyData d1 = new MyData();
	d1.setName("kim");
	d1.setAge(123);
	d1.setMail("kim@gilbut.co.kr");
	d1.setMemo("this is my data!");
	repository.saveAndFlush(d1);
	MyData d2 = new MyData();
	d2.setName("lee");
	d2.setAge(15);
	d2.setMail("lee@flower");
	d2.setMemo("my girl friend.");
	repository.saveAndFlush(d2);
	MyData d3 = new MyData();
	d3.setName("choi");
	d3.setAge(37);
	d3.setMail("choi@happy");
	d3.setMemo("my work friend...");
	repository.saveAndFlush(d3);
}

코드5-10
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>edit page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	tr { margin:5px; }
	th { padding:5px; color:white; background:darkgray; }
	td { padding:5px; color:black; background:#e0e0ff; }
	</style>
</head>
<body>
	<h1 th:text="${title}">Edit page</h1>
	<table>
	<form method="post" action="/edit" th:object="${formModel}">
		<input type="hidden" name="id" th:value="*{id}" />
		<tr><td><label for="name">이름</label></td>
			<td><input type="text" name="name" th:value="*{name}" /></td></tr>
		<tr><td><label for="age">연령</label></td>
			<td><input type="text" name="age"  th:value="*{age}" /></td></tr>
		<tr><td><label for="mail">메일</label></td>
			<td><input type="text" name="mail"  th:value="*{mail}" /></td></tr>
		<tr><td><label for="memo">메모</label></td>
			<td><textarea name="memo"  th:text="*{memo}" 
			cols="20" rows="5"></textarea></td></tr>
		<tr><td></td><td><input type="submit" /></td></tr>
	</form>
	</table>
</body>
</html>

코드5-11
@Repository
public interface MyDataRepository  extends JpaRepository<MyData, Long> {
	
	public MyData findById(Long name);
}

코드5-12
@RequestMapping(value = "/edit/{id}", method = RequestMethod.GET)
public ModelAndView edit(@ModelAttribute MyData mydata, 
		@PathVariable int id,ModelAndView mav) {
	mav.setViewName("edit");
	mav.addObject("title","edit mydata.");
	MyData data = repository.findById((long)id);
	mav.addObject("formModel",data);
	return mav;
}

@RequestMapping(value = "/edit", method = RequestMethod.POST)
@Transactional(readOnly=false)
public ModelAndView update(@ModelAttribute MyData mydata, 
		ModelAndView mav) {
	repository.saveAndFlush(mydata);
	return new ModelAndView("redirect:/");
}

코드5-13
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>edit page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	td { padding:0px 20px; background:#eee;}
	</style>
</head>
<body>
	<h1 th:text="${title}">Edit page</h1>
	<table>
	<form method="post" action="/delete" 
		th:object="${formModel}">
		<input type="hidden" name="id" th:value="*{id}" />
		<tr><td><p th:text="|이름：　*{name}|"></p></td></tr>
		<tr><td><p th:text="|연령：　*{age}|" ></p></td></tr>
		<tr><td><p th:text="*{mail}"></p></td></tr>
		<tr><td><p th:text="*{memo}"></p></td></tr>
		<tr><td><input type="submit" value="delete"/></td></tr>
	</form>
	</table>
</body>
</html>

코드5-14
@RequestMapping(value = "/delete/{id}", method = RequestMethod.GET)
public ModelAndView delete(@PathVariable int id,
		ModelAndView mav) {
	mav.setViewName("delete");
	mav.addObject("title","delete mydata.");
	MyData data = repository.findById((long)id);
	mav.addObject("formModel",data);
	return mav;
}

@RequestMapping(value = "/delete", method = RequestMethod.POST)
@Transactional(readOnly=false)
public ModelAndView remove(@RequestParam long id, 
		ModelAndView mav) {
	repository.delete(id);
	return new ModelAndView("redirect:/");
}

코드5-15
package com.tuyano.springboot.repositories;

import java.util.List;

import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

import com.tuyano.springboot.MyData;

@Repository
public interface MyDataRepository  extends JpaRepository<MyData, Long> {
	
	public MyData findById(Long name);
	public List<MyData> findByNameLike(String name);
	public List<MyData> findByIdIsNotNullOrderByIdDesc();
	public List<MyData> findByAgeGreaterThan(Integer age);
	public List<MyData> findByAgeBetween(Integer age1, Integer age2);

}

코드5-16
package com.tuyano.springboot;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.Table;
import javax.validation.constraints.Min;
import javax.validation.constraints.Max;
import javax.validation.constraints.NotNull;

import org.hibernate.validator.constraints.Email;
import org.hibernate.validator.constraints.NotEmpty;

@Entity
@Table(name = "mydata")
public class MyData {

	@Id
	@GeneratedValue(strategy = GenerationType.AUTO)
	@Column
	@NotNull	// ●
	private long id;

	@Column(length = 50, nullable = false)
	@NotEmpty	// ●
	private String name;

	@Column(length = 200, nullable = true)
	@Email	// ●
	private String mail;

	@Column(nullable = true)
	@Min(0)	// ●
	@Max(200) // ●
	private Integer age;

	@Column(nullable = true)
	private String memo;

	……접근자는 생략……
}

코드5-17


@RequestMapping(value = "/", method = RequestMethod.GET)
public ModelAndView index(
	@ModelAttribute("formModel") MyData mydata, 
		ModelAndView mav) {
	mav.setViewName("index");
	mav.addObject("msg","this is sample content.");
	mav.addObject("formModel",mydata);
	Iterable<MyData> list = repository.findAll();
	mav.addObject("datalist",list);
	return mav;
}

@RequestMapping(value = "/", method = RequestMethod.POST)
@Transactional(readOnly=false)
public ModelAndView form(
		@ModelAttribute("formModel") 
		@Validated MyData mydata,
		BindingResult result,
		ModelAndView mov) {
	ModelAndView res = null;
	if (!result.hasErrors()){
		repository.saveAndFlush(mydata);
		res = new ModelAndView("redirect:/");
	} else {
		mov.setViewName("index");
		mov.addObject("msg","sorry, error is occured...");
		Iterable<MyData> list = repository.findAll();
		mov.addObject("datalist",list);
		res = mov;
	}
	return res;
}

코드5-18
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	tr { margin:5px; }
	th { padding:5px; color:white; background:darkgray; }
	td { padding:5px; color:black; background:#e0e0ff; }
	.err { color:red; }
	</style>
</head>
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:text="${msg}"></p>
	<table>
	<form method="post" action="/" th:object="${formModel}">
		<ul>
			<li th:each="error : ${#fields.detailedErrors()}"
				class="err" th:text="${error.message}" />
		</ul>
		<tr><td><label for="name">이름</label></td>
			<td><input type="text" name="name" 
				th:field="*{name}" /></td></tr>
		<tr><td><label for="age">연령</label></td>
			<td><input type="text" name="age"
				th:field="*{age}" /></td></tr>
		<tr><td><label for="mail">메일</label></td>
			<td><input type="text" name="mail" 
					th:field="*{mail}" /></td></tr>
		<tr><td><label for="memo">메모</label></td>
			<td><textarea name="memo" th:field="*{memo}" 
				cols="20" rows="5" ></textarea></td></tr>
		<tr><td></td><td><input type="submit" /></td></tr>
	</form>
	</table>
	<hr/>
	<table>
	<tr><th>ID</th><th>이름</th></tr>
	<tr th:each="obj : ${datalist}">
		<td th:text="${obj.id}"></td>
		<td th:text="${obj.name}"></td>
	</tr>
	</table>
</body>
</html>

코드5-19
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:text="${msg}"></p>
	<table>
	<form method="post" action="/" th:object="${formModel}">
		<tr><td><label for="name">이름</label></td>
			<td><input type="text" name="name"
				th:value="*{name}" th:errorclass="err" />
			<div th:if="${#fields.hasErrors('name')}" 
				th:errors="*{name}" th:errorclass="err">
				</div></td></tr>
		<tr><td><label for="age">연령</label></td>
			<td><input type="text" name="age"
				th:value="*{age}" th:errorclass="err" />
			<div th:if="${#fields.hasErrors('age')}" 
				th:errors="*{age}" th:errorclass="err">
				</div></td></tr>
		<tr><td><label for="mail">메일</label></td>
			<td><input type="text" name="mail" 
				th:value="*{mail}" th:errorclass="err" />
			<div th:if="${#fields.hasErrors('mail')}" 
				th:errors="*{mail}" th:errorclass="err">
				</div></td></tr>
		<tr><td><label for="memo">메모</label></td>
			<td><textarea name="memo" th:text="*{memo}" 
				cols="20" rows="5" ></textarea></td></tr>
		<tr><td></td><td><input type="submit" /></td></tr>
	</form>
	</table>
	<hr/>
	<table>
	<tr><th>ID</th><th>이름</th></tr>
	<tr th:each="obj : ${datalist}">
		<td th:text="${obj.id}"></td>
		<td th:text="${obj.name}"></td>
	</tr>
	</table>
</body>

코드5-20
@Entity
@Table(name="mydata")
public class MyData {

	@Id
	@GeneratedValue(strategy = GenerationType.AUTO)
	@Column
	@NotNull	// ●
	private long id;

	@Column(length = 50, nullable = false)
	@NotEmpty(message="공백 불가")	// ●
	private String name;

	@Column(length = 200, nullable = true)
	@Email(message="메일 주소만")	// ●
	private String mail;

	@Column(nullable = true)
	@Min(value=0,message="0이상")	// ●
	@Max(value=200,message="200이하") // ●
	private Integer age;

	@Column(nullable = true)
	private String memo;

	……이하 생략……
}

코드5-21
org.hibernate.validator.constraints.NotBlank.message = 공백은 허용되지 않습니다.
org.hibernate.validator.constraints.NotEmpty.message = 공백은 허용되지 않습니다.
javax.validation.constraints.Max.message = {value} 보다 작은 값을 입력해주세요.
javax.validation.constraints.Min.message = {value} 보다 큰 값을 입력해주세요.
org.hibernate.validator.constraints.Email.message = 메일 주소가 아닙니다.

코드5-22
org.hibernate.validator.constraints.NotBlank.message = \u7A7A\u767D\u306F\u4E0D\u53EF\u3067\u3059\u3002
org.hibernate.validator.constraints.NotEmpty.message = \u7A7A\u767D\u306F\u4E0D\u53EF\u3067\u3059\u3002
javax.validation.constraints.Max.message = {value} \u3088\u308A\u5C0F\u3055\u304F\u3057\u3066\u4E0B\u3055\u3044\u3002
javax.validation.constraints.Min.message = {value} \u3088\u308A\u5927\u304D\u304F\u3057\u3066\u4E0B\u3055\u3044\u3002
org.hibernate.validator.constraints.Email.message = \u30E1\u30FC\u30EB\u30A2\u30C9\u30EC\u30B9\u3067\u306F\u3042\u308A\u307E\u305B\u3093\u3002

코드5-23
package com.tuyano.springboot;

import javax.validation.ConstraintValidator;
import javax.validation.ConstraintValidatorContext;

public class PhoneValidator implements ConstraintValidator<Phone, String> {

	@Override
	public void initialize(Phone phone) {
	}

	@Override
	public boolean isValid(String input, ConstraintValidatorContext cxt) {
		if (input == null) {
			return false;
		}
		return input.matches("[0-9()-]*");
	}

}

코드5-24
package com.tuyano.springboot;

import java.lang.annotation.Documented;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

import javax.validation.Constraint;
import javax.validation.Payload;
import javax.validation.ReportAsSingleViolation;

@Documented
@Constraint(validatedBy = PhoneValidator.class)
@Target({ ElementType.METHOD, ElementType.FIELD })
@Retention(RetentionPolicy.RUNTIME)
@ReportAsSingleViolation
public @interface Phone {

	String message() default "please input a phone number.";

	Class<?>[] groups() default {};

	Class<? extends Payload>[] payload() default {};

}

코드5-25
@Column(nullable = true)
@Phone
private String memo;

코드5-26
<tr><td><label for="memo">메모</label></td>
	<td><textarea name="memo" th:text="*{memo}" 
		th:errorclass="err" cols="20" rows="5" ></textarea>
	<div th:if="${#fields.hasErrors('memo')}" 
		th:errors="*{memo}" th:errorclass="err"></div></td></tr>

코드5-27
public void init(){
	MyData d1 = new MyData();
	d1.setName("tuyano");
	d1.setAge(123);
	d1.setMail("kim@gilbut.co.kr");
	d1.setMemo("090-999-999"); // ●
	repository.saveAndFlush(d1);
	MyData d2 = new MyData();
	d2.setName("lee");
	d2.setAge(15);
	d2.setMail("lee@flower");
	d2.setMemo("080-888-888"); // ●
	repository.saveAndFlush(d2);
	MyData d3 = new MyData();
	d3.setName("choi");
	d3.setAge(37);
	d3.setMail("choi@happy");
	d3.setMemo("070-777-777"); // ●
	repository.saveAndFlush(d3);
}

코드5-28
public @interface Phone {

	String message() default "please input a phone number.";

	Class<?>[] groups() default {};

	Class<? extends Payload>[] payload() default {};

	boolean onlyNumber() default false;	// ●
	
}

코드5-29
public class PhoneValidator implements ConstraintValidator<Phone, String> {
	private boolean onlyNumber = false;

	@Override
	public void initialize(Phone phone) {
		onlyNumber = phone.onlyNumber();
	}

	@Override
	public boolean isValid(String input, ConstraintValidatorContext cxt) {
		if (input == null) {
			return false;
		}
		if (onlyNumber) {
			return input.matches("[0-9]*");
		} else {
			return input.matches("[0-9()-]*");
		}
	}

}

코드5-30
@Column(nullable = true)
@Phone(onlyNumber=true)
private String memo;

코드5-pom.xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.tuyano.springboot</groupId>
	<artifactId>MyBootApp</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>MyBootApp</name>
	<description>sample project for Spring Boot</description>

	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>1.4.2.RELEASE</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
		<java.version>1.8</java.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
<groupId>org.hsqldb</groupId>
	<artifactId>hsqldb</artifactId>
	<scope>runtime</scope>
</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-thymeleaf</artifactId>
			</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>


</project>

코드5-heloController.java
package com.tuyano.springboot;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.transaction.annotation.Transactional;
import org.springframework.validation.BindingResult;
import org.springframework.validation.annotation.Validated;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.servlet.ModelAndView;

import com.tuyano.springboot.repositories.MyDataRepository;
import javax.annotation.PostConstruct; 

@Controller
public class HeloController {
	
	@Autowired
	MyDataRepository repository;
	
	@RequestMapping(value = "/", method = RequestMethod.GET)
	public ModelAndView index(
		@ModelAttribute("formModel") MyData mydata, 
			ModelAndView mav) {
		mav.setViewName("index");
		mav.addObject("msg","this is sample content.");
		mav.addObject("formModel",mydata);
		Iterable<MyData> list = repository.findAll();
		mav.addObject("datalist",list);
		return mav;
	}

	@RequestMapping(value = "/", method = RequestMethod.POST)
	@Transactional(readOnly=false)
	public ModelAndView form(
			@ModelAttribute("formModel") 
			@Validated MyData mydata,
			BindingResult result,
			ModelAndView mov) {
		ModelAndView res = null;
		if (!result.hasErrors()){
			repository.saveAndFlush(mydata);
			res = new ModelAndView("redirect:/");
		} else {
			mov.setViewName("index");
			mov.addObject("msg","sorry, error is occured...");
			Iterable<MyData> list = repository.findAll();
			mov.addObject("datalist",list);
			res = mov;
		}
		return res;
	}
	

	@PostConstruct
	public void init(){
		MyData d1 = new MyData();
		d1.setName("tuyano");
		d1.setAge(123);
		d1.setMail("kim@gilbut.co.kr");
		d1.setMemo("090999999"); // ●
		repository.saveAndFlush(d1);
		MyData d2 = new MyData();
		d2.setName("lee");
		d2.setAge(15);
		d2.setMail("lee@flower");
		d2.setMemo("080888888"); // ●
		repository.saveAndFlush(d2);
		MyData d3 = new MyData();
		d3.setName("choi");
		d3.setAge(37);
		d3.setMail("choi@happy");
		d3.setMemo("070777777"); // ●
		repository.saveAndFlush(d3);
	}

	
	@RequestMapping(value = "/edit/{id}", method = RequestMethod.GET)
	public ModelAndView edit(@ModelAttribute MyData mydata, 
			@PathVariable int id,ModelAndView mav) {
		mav.setViewName("edit");
		mav.addObject("title","edit mydata.");
		MyData data = repository.findById((long)id);
		mav.addObject("formModel",data);
		return mav;
	}

	@RequestMapping(value = "/edit", method = RequestMethod.POST)
	@Transactional(readOnly=false)
	public ModelAndView update(@ModelAttribute MyData mydata, 
			ModelAndView mav) {
		repository.saveAndFlush(mydata);
		return new ModelAndView("redirect:/");
	}
	
	@RequestMapping(value = "/delete/{id}", method = RequestMethod.GET)
	public ModelAndView delete(@PathVariable int id,
			ModelAndView mav) {
		mav.setViewName("delete");
		mav.addObject("title","delete mydata.");
		MyData data = repository.findById((long)id);
		mav.addObject("formModel",data);
		return mav;
	}

	@RequestMapping(value = "/delete", method = RequestMethod.POST)
	@Transactional(readOnly=false)
	public ModelAndView remove(@RequestParam long id, 
			ModelAndView mav) {
		repository.delete(id);
		return new ModelAndView("redirect:/");
	}


}

코드5-MyData.java
package com.tuyano.springboot;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.Table;
import javax.validation.constraints.Max;
import javax.validation.constraints.Min;
import javax.validation.constraints.NotNull;

import org.hibernate.validator.constraints.Email;
import org.hibernate.validator.constraints.NotEmpty;

@Entity
@Table(name = "mydata")
public class MyData {

	@Id
	@GeneratedValue(strategy = GenerationType.AUTO)
	@Column
	@NotNull	
	private long id;

	@Column(length = 50, nullable = false)
	@NotEmpty
	private String name;

	@Column(length = 200, nullable = true)
	@Email
	private String mail;

	@Column(nullable = true)
	@Min(value=0)	
	@Max(value=200) 
	private Integer age;


	@Column(nullable = true)
	@Phone(onlyNumber=true)
	private String memo;


	public long getId() {
		return id;
	}
	public void setId(long id) {
		this.id = id;
	}

	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}

	public String getMail() {
		return mail;
	}
	public void setMail(String mail) {
		this.mail = mail;
	}

	public Integer getAge() {
		return age;
	}
	public void setAge(Integer age) {
		this.age = age;
	}

	public String getMemo() {
		return memo;
	}
	public void setMemo(String memo) {
		this.memo = memo;
	}
}

코드5-Phone.java
package com.tuyano.springboot;

import java.lang.annotation.Documented;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

import javax.validation.Constraint;
import javax.validation.Payload;
import javax.validation.ReportAsSingleViolation;

@Documented
@Constraint(validatedBy = PhoneValidator.class)
@Target({ ElementType.METHOD, ElementType.FIELD })
@Retention(RetentionPolicy.RUNTIME)
@ReportAsSingleViolation
public @interface Phone {

	String message() default "please input a phone number.";

	Class<?>[] groups() default {};

	Class<? extends Payload>[] payload() default {};

	boolean onlyNumber() default false;	// ●
	
}

코드5-PhoneValidator.java
package com.tuyano.springboot;

import javax.validation.ConstraintValidator;
import javax.validation.ConstraintValidatorContext;
public class PhoneValidator implements ConstraintValidator<Phone, String> {
	private boolean onlyNumber = false;

	@Override
	public void initialize(Phone phone) {
		onlyNumber = phone.onlyNumber();
	}

	@Override
	public boolean isValid(String input, ConstraintValidatorContext cxt) {
		if (input == null) {
			return false;
		}
		if (onlyNumber) {
			return input.matches("[0-9]*");
		} else {
			return input.matches("[0-9()-]*");
		}
	}

}

코드5-MyDataRepository.java
package com.tuyano.springboot.repositories;

import java.util.List;

import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

import com.tuyano.springboot.MyData;

@Repository
public interface MyDataRepository  extends JpaRepository<MyData, Long> {
	
	public MyData findById(Long name);
	public List<MyData> findByNameLike(String name);
	public List<MyData> findByIdIsNotNullOrderByIdDesc();
	public List<MyData> findByAgeGreaterThan(Integer age);
	public List<MyData> findByAgeBetween(Integer age1, Integer age2);

}


코드5-index.html
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	tr { margin:5px; }
	th { padding:5px; color:white; background:darkgray; }
	td { padding:5px; color:black; background:#e0e0ff; }
	.err { color:red; }
	</style>
</head>
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:text="${msg}"></p>
	<table>
	<form method="post" action="/" th:object="${formModel}">
		<tr><td><label for="name">이름</label></td>
			<td><input type="text" name="name"
				th:value="*{name}" th:errorclass="err" />
			<div th:if="${#fields.hasErrors('name')}" 
				th:errors="*{name}" th:errorclass="err">
				</div></td></tr>
		<tr><td><label for="age">연령</label></td>
			<td><input type="text" name="age"
				th:value="*{age}" th:errorclass="err" />
			<div th:if="${#fields.hasErrors('age')}" 
				th:errors="*{age}" th:errorclass="err">
				</div></td></tr>
		<tr><td><label for="mail">메일</label></td>
			<td><input type="text" name="mail" 
				th:value="*{mail}" th:errorclass="err" />
			<div th:if="${#fields.hasErrors('mail')}" 
				th:errors="*{mail}" th:errorclass="err">
				</div></td></tr>
		<tr><td><label for="memo">메모</label></td>
	<td><textarea name="memo" th:text="*{memo}" 
		th:errorclass="err" cols="20" rows="5" ></textarea>
	<div th:if="${#fields.hasErrors('memo')}" 
		th:errors="*{memo}" th:errorclass="err"></div></td></tr>
		<tr><td></td><td><input type="submit" /></td></tr>
	</form>
	</table>
	<hr/>
	<table>
	<tr><th>ID</th><th>이름</th></tr>
	<tr th:each="obj : ${datalist}">
		<td th:text="${obj.id}"></td>
		<td th:text="${obj.name}"></td>
	</tr>
	</table>
</body>
</html>
코드5-edit.html
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>edit page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	tr { margin:5px; }
	th { padding:5px; color:white; background:darkgray; }
	td { padding:5px; color:black; background:#e0e0ff; }
	</style>
</head>
<body>
	<h1 th:text="${title}">Edit page</h1>
	<table>
	<form method="post" action="/edit" th:object="${formModel}">
		<input type="hidden" name="id" th:value="*{id}" />
		<tr><td><label for="name">이름</label></td>
			<td><input type="text" name="name" th:value="*{name}" /></td></tr>
		<tr><td><label for="age">연령</label></td>
			<td><input type="text" name="age"  th:value="*{age}" /></td></tr>
		<tr><td><label for="mail">메일</label></td>
			<td><input type="text" name="mail"  th:value="*{mail}" /></td></tr>
		<tr><td><label for="memo">메모</label></td>
			<td><textarea name="memo"  th:text="*{memo}" 
			cols="20" rows="5"></textarea></td></tr>
		<tr><td></td><td><input type="submit" /></td></tr>
	</form>
	</table>
</body>
</html>


코드5-delete.html
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>edit page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	td { padding:0px 20px; background:#eee;}
	</style>
</head>
<body>
	<h1 th:text="${title}">Edit page</h1>
	<table>
	<form method="post" action="/delete" 
		th:object="${formModel}">
		<input type="hidden" name="id" th:value="*{id}" />
		<tr><td><p th:text="|이름：　*{name}|"></p></td></tr>
		<tr><td><p th:text="|연령：　*{age}|" ></p></td></tr>
		<tr><td><p th:text="*{mail}"></p></td></tr>
		<tr><td><p th:text="*{memo}"></p></td></tr>
		<tr><td><input type="submit" value="delete"/></td></tr>
	</form>
	</table>
</body>
</html>

코드6-1
package com.tuyano.springboot;

import java.io.Serializable;
import java.util.List;

public interface MyDataDao <T> extends Serializable {
	
	public List<T> getAll();
	
}

코드6-2
package com.tuyano.springboot;

import java.util.List;

import javax.persistence.EntityManager;
import javax.persistence.Query;

import org.springframework.stereotype.Repository;

@Repository
public class MyDataDaoImpl implements MyDataDao<MyData> {
	private static final long serialVersionUID = 1L;
	
	private EntityManager entityManager;
	
	public MyDataDaoImpl(){
		super();
	}
	public MyDataDaoImpl(EntityManager manager){
		entityManager = manager;
	}
	
	@Override
	public List<MyData> getAll() {
		Query query = entityManager.createQuery("from MyData");
		List<MyData> list = query.getResultList();
		entityManager.close();
		return list;
	}
	
}

코드6-3
package com.tuyano.springboot;

import javax.annotation.PostConstruct;
import javax.persistence.EntityManager;
import javax.persistence.PersistenceContext;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.transaction.annotation.Transactional;
import org.springframework.validation.BindingResult;
import org.springframework.validation.annotation.Validated;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.servlet.ModelAndView;

import com.tuyano.springboot.repositories.MyDataRepository;

@Controller
public class HeloController {
	
	@Autowired
	MyDataRepository repository;
	
	@PersistenceContext
	EntityManager entityManager; //●
	
	MyDataDaoImpl dao; //●
	
	@RequestMapping(value = "/", method = RequestMethod.GET)
	public ModelAndView index(ModelAndView mav) {
		mav.setViewName("index");
		mav.addObject("msg","MyData의 예제입니다.");
		Iterable<MyData> list = dao.getAll(); //●
		mav.addObject("datalist", list);
		return mav;
	}

	@PostConstruct
	public void init(){
		dao = new MyDataDaoImpl(entityManager); //●
		MyData d1 = new MyData();
		d1.setName("tuyano");
		d1.setAge(123);
		d1.setMail("kim@gilbut.co.kr");
		d1.setMemo("090999999");
		repository.save(d1);
		MyData d2 = new MyData();
		d2.setName("lee");
		d2.setAge(15);
		d2.setMail("lee@flower");
		d2.setMemo("080888888");
		repository.save(d2);
		MyData d3 = new MyData();
		d3.setName("choi");
		d3.setAge(37);
		d3.setMail("choi@happy");
		d3.setMemo("070777777");
		repository.save(d3);
	}

}

코드6-4
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	tr { margin:5px; }
	th { padding:5px; color:white; background:darkgray; }
	td { padding:5px; color:black; background:#e0e0ff; }
	.err { color:red; }
	</style>
</head>
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:text="${msg}"></p>
	<table>
	<tr><th>ID</th><th>이름</th><th>메일</th><th>연령</th><th>메모(tel)</th></tr>
	<tr th:each="obj : ${datalist}">
		<td th:text="${obj.id}"></td>
		<td th:text="${obj.name}"></td>
		<td th:text="${obj.mail}"></td>
		<td th:text="${obj.age}"></td>
		<td th:text="${obj.memo}"></td>
	</tr>
	</table>
</body>
</html>

코드6-5
package com.tuyano.springboot;

import java.io.Serializable;
import java.util.List;

public interface MyDataDao<T> extends Serializable {
	
	public List<T> getAll();
	public T findById(long id);
	public List<T> findByName(String name);
}

코드6-6
@Override
public MyData findById(long id) {
	return (MyData)entityManager.createQuery("from MyData where id = " 
		+ id).getSingleResult();
}

@Override
public List<MyData> findByName(String name) {
	return (List<MyData>)entityManager.createQuery("from MyData where name = " 
		+ name).getResultList();
}

코드6-7
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>find page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	tr { margin:5px; }
	th { padding:5px; color:white; background:darkgray; }
	td { padding:5px; color:black; background:#e0e0ff; }
	</style>
</head>
<body>
	<h1 th:text="${title}">find page</h1>
	<p th:text="${msg}"></p>
	<table>
	<form action="/find" method="post">
		<tr><td>FIND:</td>
		<td><input type="text" name="fstr" size="20" 
			th:value="${value}"/></td></tr>
		<tr><td></td><td><input type="submit" /></td></tr>
	</form>
	</table>
	<hr/>
	<table>
	<tr><th>ID</th><th>이름</th>
		<th>메일</th><th>연령</th></tr>
	<tr th:each="obj : ${datalist}">
		<td th:text="${obj.id}"></td>
		<td th:text="${obj.name}"></td>
		<td th:text="${obj.mail}"></td>
		<td th:text="${obj.age}"></td>
	</tr>
	</table>
</body>
</html>

코드6-8
// import javax.servlet.http.HttpServletRequest; を追加

@RequestMapping(value = "/find", method = RequestMethod.GET)
public ModelAndView find(ModelAndView mav) {
	mav.setViewName("find");
	mav.addObject("title","Find Page");
	mav.addObject("msg","MyData의 예제입니다.");
	mav.addObject("value","");
	Iterable<MyData> list = dao.getAll(); //●
	mav.addObject("datalist", list);
	return mav;
}

@RequestMapping(value = "/find", method = RequestMethod.POST)
public ModelAndView search(HttpServletRequest request,
		ModelAndView mav) {
	mav.setViewName("find");
	String param = request.getParameter("fstr");
	if (param == ""){
		mav = new ModelAndView("redirect:/find");
	} else {
		mav.addObject("title","Find result");
		mav.addObject("msg","「" + param + "」의 검색 결과");
		mav.addObject("value",param);
		List<MyData> list = dao.find(param);
		mav.addObject("datalist", list);
	}
	return mav;
}

코드6-9
public List<T> find(String fstr);

코드6-10
@Override
public List<MyData> find(String fstr){
	List<MyData> list = null;
	String qstr = "from MyData where id = :fstr";
	Query query = entityManager.createQuery(qstr)
		.setParameter("fstr", Long.parseLong(fstr));
	list = query.getResultList();
	return list;
}

코드6-11
@Override
public List<MyData> find(String fstr){
	List<MyData> list = null;
	String qstr = "from MyData where id = :fid or name like :fname or mail like :fmail";
	Long fid = 0L;
	try {
		fid = Long.parseLong(fstr);
	} catch (NumberFormatException e) {
		//e.printStackTrace();
	}
	Query query = entityManager.createQuery(qstr).setParameter("fid", fid)
			.setParameter("fname", "%" + fstr + "%")
			.setParameter("fmail", fstr + "@%");
	list = query.getResultList();
	return list;
}

코드6-12
@Override
public List<MyData> find(String fstr){
	List<MyData> list = null;
	String qstr = "from MyData where id = ?1 or name like ?2 or mail like ?3";
	Long fid = 0L;
	try {
		fid = Long.parseLong(fstr);
	} catch (NumberFormatException e) {
		//e.printStackTrace();
	}
	Query query = entityManager.createQuery(qstr).setParameter(1, fid)
		.setParameter(2, "%" + fstr + "%")
		.setParameter(3, fstr + "@%");
	list = query.getResultList();
	return list;
}

코드6-13
// import javax.persistence.NamedQuery; 추가

@NamedQuery(
	name="findWithName",
	query="from MyData where name like :fname"
)

코드6-14
@NamedQueries (
	@NamedQuery(
		name="findWithName",
		query="from MyData where name like :fname"
	)
)

코드6-15
@Override
public List<MyData> find(String fstr){
	List<MyData> list = null;
	Long fid = 0L;
	try {
		fid = Long.parseLong(fstr);
	} catch (NumberFormatException e) {
		//e.printStackTrace();
	}
	Query query = entityManager
			.createNamedQuery("findWithName")
			.setParameter("fname", "%" + fstr + "%");
	list = query.getResultList();
	return list;
}

코드6-16
package com.tuyano.springboot.repositories;

import java.util.List;

import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import org.springframework.stereotype.Repository;

import com.tuyano.springboot.MyData;

@Repository
public interface MyDataRepository  extends JpaRepository<MyData, Long> {
	
	@Query("SELECT d FROM MyData d ORDER BY d.name")
	List<MyData> findAllOrderByName();
}

코드6-17
@RequestMapping(value = "/", method = RequestMethod.GET)
public ModelAndView index(ModelAndView mav) {
	mav.setViewName("index");
	mav.addObject("title","Find Page");
	mav.addObject("msg","MyData의 예제입니다.");
	Iterable<MyData> list = repository.findAllOrderByName(); //dao.getAll(); //●
	mav.addObject("datalist", list);
	return mav;
}

코드6-18
@NamedQuery(
	name="findByAge",
	query="from MyData where age > :min and age < :max"
)

코드6-19	MyDataDao에 추가
public List<MyData> findByAge(int min, int max);

코드6-20	MyDataDaoImpl에 추가
@Override
public List<MyData> findByAge(int min, int max) {
	return (List<MyData>)entityManager
		.createNamedQuery("findByAge")
		.setParameter("min", min)
		.setParameter("max", max)
		.getResultList();
}

코드6-21
@Query("from MyData where age > :min and age < :max")
public List<MyData> findByAge(@Param("min") int min, @Param("max") int max);

코드6-22
import javax.persistence.criteria.CriteriaBuilder;
import javax.persistence.criteria.CriteriaQuery;
import javax.persistence.criteria.Root;

코드6-23
@Override
public List<MyData> getAll() {
	List<MyData> list = null;		
	CriteriaBuilder builder = 
			entityManager.getCriteriaBuilder();
	CriteriaQuery<MyData> query = 
			builder.createQuery(MyData.class);
	Root<MyData> root = query.from(MyData.class);
	query.select(root);
	list = (List<MyData>)entityManager
			.createQuery(query)
			.getResultList();
	return list;
}

코드6-24
@Override
public List<MyData> find(String fstr){
	CriteriaBuilder builder = 
			entityManager.getCriteriaBuilder();
	CriteriaQuery<MyData> query = 
		builder.createQuery(MyData.class);
	Root<MyData> root = 
		query.from(MyData.class);
	query.select(root)
		.where(builder.equal(root.get("name"), fstr));
	List<MyData> list = null;
	list = (List<MyData>) entityManager
			.createQuery(query)
			.getResultList();
	return list;
}

코드6-25
@Override
public List<MyData> getAll() {
	List<MyData> list = null;		
	CriteriaBuilder builder = 
			entityManager.getCriteriaBuilder();
	CriteriaQuery<MyData> query = 
			builder.createQuery(MyData.class);
	Root<MyData> root = query.from(MyData.class);
	query.select(root)
			.orderBy(builder.asc(root.get("name")));
	list = (List<MyData>)entityManager
			.createQuery(query)
			.getResultList();
	return list;
}

코드6-26
@Override
public List<MyData> getAll() {
	int offset = 1; // ●추출 위치 지정
	int limit = 2; // ●추출 개수 지정
	List<MyData> list = null;
	CriteriaBuilder builder = 
			entityManager.getCriteriaBuilder();
	CriteriaQuery<MyData> query = 
			builder.createQuery(MyData.class);
	Root<MyData> root = 
			query.from(MyData.class);
	query.select(root);
	list = (List<MyData>)entityManager
			.createQuery(query)
			.setFirstResult(offset)
			.setMaxResults(limit)
			.getResultList();
	return list;
}

코드6-27――MsgData.java
package com.tuyano.springboot;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.ManyToOne;
import javax.persistence.Table;
import javax.validation.constraints.NotNull;

import org.hibernate.validator.constraints.NotEmpty;

@Entity
@Table(name = "msgdata")
public class MsgData {

	@Id
	@GeneratedValue(strategy = GenerationType.AUTO)
	@Column
	@NotNull
	private long id;

	@Column
	private String title;

	@Column(nullable = false)
	@NotEmpty
	private String message;

	@ManyToOne
	private MyData mydata;

	public MsgData() {
		super();
		mydata = new MyData();
	}

	public long getId() {
		return id;
	}

	public void setId(long id) {
		this.id = id;
	}

	public String getTitle() {
		return title;
	}

	public void setTitle(String title) {
		this.title = title;
	}

	public String getMessage() {
		return message;
	}

	public void setMessage(String message) {
		this.message = message;
	}

	public MyData getMydata() {
		return mydata;
	}

	public void setMydata(MyData mydata) {
		this.mydata = mydata;
	}
}

코드6-28
// 다음 import를 추가. 다른 package/import는 생략하고 있다
// import javax.persistence.CascadeType;
// import javax.persistence.OneToMany;
// import java.util.List;

@Entity
@Table(name = "mydata")
public class MyData {
	
	@OneToMany(cascade=CascadeType.ALL)
	@Column(nullable = true)
	private List<MsgData> msgdatas;
	
	public List<MsgData> getMsgdatas() {
		return msgdatas;
	}

	public void setMsgdatas(List<MsgData> msgdatas) {
		this.msgdatas = msgdatas;
	}
	
	……이하 생략……	
}

코드6-29――MsgDataRepository.java
package com.tuyano.springboot.repositories;

import org.springframework.data.jpa.repository.JpaRepository;

import com.tuyano.springboot.MsgData;

public interface MsgDataRepository 
	extends JpaRepository<MsgData, Long> {
	
}

코드6-30――MsgDataDao.java
package com.tuyano.springboot;

import java.io.Serializable;
import java.util.List;

public interface MsgDataDao<T> {
	
	public List<MsgData> getAll();
	public MsgData findById(long id);

}

코드6-31――MsgDataDaoImpl.java
package com.tuyano.springboot;

import java.util.List;

import javax.persistence.EntityManager;

public class MsgDataDaoImpl implements MsgDataDao<MsgDataDao> {

	private EntityManager entityManager;
	
	public MsgDataDaoImpl(){
		super();
	}
	public MsgDataDaoImpl(EntityManager manager){
		entityManager = manager;
	}

	@Override
	public List<MsgData> getAll() {
		return entityManager
				.createQuery("from MsgData")
				.getResultList();
	}

	@Override
	public MsgData findById(long id) {
		return (MsgData)entityManager
				.createQuery("from MsgData where id = " 
				+ id).getSingleResult();
	}
}

코드6-32――showMsgData.html
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title th:text="${title}">top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	tr { margin:5px; }
	th { padding:5px; color:white; background:darkgray; }
	td { padding:5px; color:black; background:#e0e0ff; }
	</style>
</head>
<body>
	<h1 th:text="${title}">MyMsg page</h1>
	<p th:text="${msg}"></p>
	<table>
	<form method="post" action="/msg" 
			th:object="${formModel}">
		<input type="hidden" name="id" th:value="*{id}" />
		<tr><td><label for="title">제목</label></td>
			<td><input type="text" name="title" 
				th:value="*{title}" /></td></tr>
		<tr><td><label for="message">메시지</label></td>
			<td><textarea name="message"  
				th:text="*{message}"></textarea></td></tr>
		<tr><td><label for="mydata">MYDATA_ID</label></td>
			<td><input type="text" name="mydata" /></td></tr>
		<tr><td></td><td><input type="submit" /></td></tr>
	</form>
	</table>
	<hr/>
	<table>
	<tr><th>ID</th><th>이름</th><th>제목</th></tr>
	<tr th:each="obj : ${datalist}">
		<td th:text="${obj.id}"></td>
		<td th:text="${obj.mydata.name}"></td>
		<td th:text="${obj.title}"></td>
	</tr>
	</table>
</body>
</html>

코드6-33
package com.tuyano.springboot;

import java.util.List;

import javax.annotation.PostConstruct;
import javax.persistence.EntityManager;
import javax.persistence.PersistenceContext;
import javax.validation.Valid;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.validation.Errors;
import org.springframework.web.bind.annotation.ModelAttribute;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.servlet.ModelAndView;

import com.tuyano.springboot.repositories.MsgDataRepository;

@Controller
public class MsgDataController {
	
	@Autowired
	MsgDataRepository repository;
	
	@PersistenceContext
	EntityManager entityManager;
	
	MsgDataDaoImpl dao;

	@RequestMapping(value = "/msg", method = RequestMethod.GET)
	public ModelAndView msg(ModelAndView mav) {
		mav.setViewName("showMsgData");
		mav.addObject("title","Sample");
		mav.addObject("msg","MsgData의 예제입니다.");
		MsgData msgdata = new MsgData();
		mav.addObject("formModel", msgdata);
		List<MsgData> list = (List<MsgData>)dao.getAll();
		mav.addObject("datalist", list);
		return mav;
	}

	@RequestMapping(value = "/msg", method = RequestMethod.POST)
	public ModelAndView msgform(
			@Valid @ModelAttribute MsgData msgdata, 
			Errors result, 
			ModelAndView mav) {
		if (result.hasErrors()) {
			mav.setViewName("showMsgData");
			mav.addObject("title", "Sample [ERROR]");
			mav.addObject("msg", "값을 다시 확인해주세요!");
			return mav;
		} else {
			repository.save(msgdata);
			return new ModelAndView("redirect:/msg");
		}
	}

	@PostConstruct
	public void init(){
		System.out.println("ok");
		dao = new MsgDataDaoImpl(entityManager);
	}

}

코드7-1
package com.tuyano.springboot;

import java.util.List;

import javax.persistence.EntityManager;
import javax.persistence.PersistenceContext;
import javax.persistence.criteria.CriteriaBuilder;
import javax.persistence.criteria.CriteriaQuery;
import javax.persistence.criteria.Root;

import org.springframework.stereotype.Service;

@Service
public class MyDataService {

	@PersistenceContext
	private EntityManager entityManager;

	public List<MyData> getAll() {
		return (List<MyData>) entityManager.createQuery("from MyData").getResultList();
	}

	public MyData get(int num) {
		return (MyData)entityManager
				.createQuery("from MyData where id = " + num)
				.getSingleResult();
	}

	public List<MyData> find(String fstr) {
		CriteriaBuilder builder = entityManager.getCriteriaBuilder();
		CriteriaQuery<MyData> query = builder.createQuery(MyData.class);
		Root<MyData> root = query.from(MyData.class);
		query.select(root).where(builder.equal(root.get("name"), fstr));
		List<MyData> list = null;
		list = (List<MyData>) entityManager.createQuery(query).getResultList();
		return list;
	}

}

코드7-2
package com.tuyano.springboot;

import java.util.List;

import javax.annotation.PostConstruct;
import javax.servlet.http.HttpServletRequest;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.servlet.ModelAndView;

import com.tuyano.springboot.repositories.MyDataRepository;

@Controller
public class HeloController {
	
	@Autowired
	MyDataRepository repository;
	
	@Autowired
	private MyDataService service;
	
	@RequestMapping(value = "/", method = RequestMethod.GET)
	public ModelAndView index(ModelAndView mav) {
		mav.setViewName("index");
		mav.addObject("title","Find Page");
		mav.addObject("msg","MyData의 예제입니다.");
		List<MyData> list = service.getAll(); //●
		mav.addObject("datalist", list);
		return mav;
	}
	
	@RequestMapping(value = "/find", method = RequestMethod.GET)
	public ModelAndView find(ModelAndView mav) {
		mav.setViewName("find");
		mav.addObject("title","Find Page");
		mav.addObject("msg","MyData의 예제입니다.");
		mav.addObject("value","");
		List<MyData> list = service.getAll(); //●
		mav.addObject("datalist", list);
		return mav;
	}
	
	@RequestMapping(value = "/find", method = RequestMethod.POST)
	public ModelAndView search(HttpServletRequest request,
			ModelAndView mav) {
		mav.setViewName("find");
		String param = request.getParameter("fstr");
		if (param == ""){
			mav = new ModelAndView("redirect:/find");
		} else {
			mav.addObject("title","Find result");
			mav.addObject("msg","「" + param + "」의 검색 결과");
			mav.addObject("value",param);
			List<MyData> list = service.find(param); //●
			mav.addObject("datalist", list);
		}
		return mav;
	}

	@PostConstruct
	public void init(){
		MyData d1 = new MyData();
		d1.setName("tuyano");
		d1.setAge(123);
		d1.setMail("kim@gilbut.co.kr");
		d1.setMemo("090999999");
		repository.save(d1);
		MyData d2 = new MyData();
		d2.setName("lee");
		d2.setAge(15);
		d2.setMail("lee@flower");
		d2.setMemo("080888888");
		repository.save(d2);
		MyData d3 = new MyData();
		d3.setName("choi");
		d3.setAge(37);
		d3.setMail("choi@happy");
		d3.setMemo("070777777");
		repository.save(d3);
		……필요한 만큼 테스트용 데이터 준비……
	}

}

코드7-3
package com.tuyano.springboot;

import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class MyDataRestController {

	@Autowired
	private MyDataService service;

	@RequestMapping("/rest")
	public List<MyData> restAll() {
		return service.getAll();
	}

	@RequestMapping("/rest/{num}")
	public MyData restBy(@PathVariable int num) {
		return service.get(num);
	}
}

코드7-4
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<script src="http://code.jquery.com/jquery.min.js"></script>
	<script th:inline="javascript">
	$(document).ready(function(){
		var num = [[${param.id[0]}]];
		$.get("/rest/" + num, null, callback);
	});
	function callback(result){
		$('#obj').append('<li>id: ' + result.id + '</li>');
		$('#obj').append('<li>name: ' + result.name + '</li>');
		$('#obj').append('<li>mail: ' + result.mail + '</li>');
		$('#obj').append('<li>age: ' + result.age + '</li>');
		$('#obj').append('<li>memo: ' + result.memo + '</li>');
	}
	</script>
	<style>
	……생략……
	</style>
</head>
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p  th:text="${msg}"></p>
	<ol id="obj"></ol>
	<table>
	……생략……
	</table>
</body>
</html>

코드7-5
<dependency>
	<groupId>com.fasterxml.jackson.dataformat</groupId>
	<artifactId>jackson-dataformat-xml</artifactId>
</dependency>

코드7-6
package com.tuyano.springboot;

import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.ApplicationArguments;
import org.springframework.stereotype.Component;

@Component
public class MySampleBean {
	private int counter = 0;
	private int max = 10;

	@Autowired
	public MySampleBean(ApplicationArguments args) {
		List<String> files = args.getNonOptionArgs();
		try {
			max = Integer.parseInt(files.get(0));
		} catch (NumberFormatException e) {
			e.printStackTrace();
		}
	}

	public int count() {
		counter++;
		counter = counter > max ? 0 : counter;
		return counter;
	}
}

코드7-7
public static void main(String[] args) {
	SpringApplication.run(
			MyBootAppApplication.class, 
			new String[]{"100"});
}

코드7-8
@Autowired
MySampleBean bean;

@RequestMapping("/count")
public int count() {
	return bean.count();
}

코드7-9
package com.tuyano.springboot;

import org.springframework.context.annotation.Configuration;

@Configuration
public class MyBootAppConfig {
}

코드7-10
package com.tuyano.springboot;

import org.springframework.beans.factory.annotation.Autowired;

import com.tuyano.springboot.repositories.MyDataRepository;

public class MyDataBean {
	
	@Autowired
	MyDataRepository repository;
	
	public String getTableTagById(Long id){
		MyData data = repository.findOne(id);
		String result = "<tr><td>" + data.getName()
				+ "</td><td>" + data.getMail() + 
				"</td><td>" + data.getAge() + 
				"</td><td>" + data.getMemo() + 
				"</td></tr>";
		return result;
	}

}

코드7-11
package com.tuyano.springboot;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class MyBootAppConfig {

	@Bean
	MyDataBean myDataBean(){
		return new MyDataBean();
	}
}

코드7-12
@Autowired
MyDataBean myDataBean;

@RequestMapping(value = "/{id}", method = RequestMethod.GET)
public ModelAndView indexById(@PathVariable long id,
		ModelAndView mav) {
	mav.setViewName("pickup");
	mav.addObject("title","Pickup Page");
	String table = "<table>"
			+ myDataBean.getTableTagById(id)
			+ "</table>";
	mav.addObject("msg","pickup data id = " + id);
	mav.addObject("data",table);
	return mav;
}

코드7-13
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	tr { margin:5px; }
	th { padding:5px; color:white; background:darkgray; }
	td { padding:5px; color:black; background:#e0e0ff; }
	</style>
</head>
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:text="${msg}"></p>
	<p th:utext="${data}"></p>
</body>
</html>

코드7-14
// import org.springframework.data.domain.Page;
// import org.springframework.data.domain.PageRequest;
@Autowired
MyDataRepository repository;

private static final int PAGE_SIZE = 3; // 한 페이지당 엔터티 수

public Page<MyData> getMyDataInPage(Integer pageNumber) {
	PageRequest pageRequest = new PageRequest(pageNumber - 1, PAGE_SIZE);
	return repository.findAll(pageRequest);
}

코드7-15
@RequestMapping(value = "/page/{num}", 
		method = RequestMethod.GET)
public ModelAndView page(@PathVariable Integer num, 
		ModelAndView mav) {
	Page<MyData> page = service.getMyDataInPage(num);
	mav.setViewName("index");
    mav.addObject("title","Find Page");
	mav.addObject("msg","MyData의 예제입니다.");
	mav.addObject("pagenumber", num);
	mav.addObject("datalist", page);
    return mav;
}

코드7-16
<table>
<tr><th>ID</th><th>이름</th><th>메일</th><th>연령</th><th>메모(tel)</th></tr>
<tr th:each="obj : ${datalist}">
	<td th:text="${obj.id}"></td>
	<td th:text="${obj.name}"></td>
	<td th:text="${obj.mail}"></td>
	<td th:text="${obj.age}"></td>
	<td th:text="${obj.memo}"></td>
</tr>
</table>

코드7-17
package com.tuyano.springboot;

public class MyTLUtility {
	
	public String hello(String name) {
		return "Hello, <b>" + name + "!</b>";
	}
	
	public String prevUrl(int num) {
		return "/page/" + (num > 1 ? num - 1 : 1);
	}
	
	public String nextUrl(int num) {
		return "/page/" + (num + 1);
	}
}

코드7-18
package com.tuyano.springboot;

import java.util.Collections;
import java.util.HashMap;
import java.util.Map;

import org.thymeleaf.context.IProcessingContext;
import org.thymeleaf.dialect.AbstractDialect;
import org.thymeleaf.dialect.IExpressionEnhancingDialect;

public class MyTLDialect extends AbstractDialect 
		implements IExpressionEnhancingDialect {
	
	private static final Map<String, Object> EXPRESSION_OBJECTS;

	static {
		Map<String, Object> objects = new HashMap<>();
		objects.put("myTLHelper", new MyTLUtility());
		EXPRESSION_OBJECTS = Collections.unmodifiableMap(objects);
	}

	public MyTLDialect() {
		super();
	}
	
	@Override
	public Map<String, Object> getAdditionalExpressionObjects
			(IProcessingContext processingContext) {
		return EXPRESSION_OBJECTS;
	}

	@Override
	public String getPrefix() {
		return null;
	}
}

코드 7-19
  @Bean
   MyTLDialect myTLDialect(){
     return new MyTLDialect();
  }


코드7-20
<table>
  <tr><th>ID</th><th>이름</th><th>메일</th><th>연령</th><th>메모(tel)</th></tr>
  <tr th:each="obj : ${datalist}">
    <td th:text="${obj.id}"></td>
    <td th:text="${obj.name}"></td>
    <td th:text="${obj.mail}"></td>
    <td th:text="${obj.age}"></td>
    <td th:text="${obj.memo}"></td>
  </tr>
  <tr>
    <td colspan="5">
      <table class="navi">
        <tr>
          <td><div style="text-align: left;">
              <a th:href="${#myTLHelper.prevUrl(pagenumber)}">← Prev</a>
            </div></td>
          <td><div style="text-align: center;">page</div></td>
          <td><div style="text-align: right;">
              <a th:href="${#myTLHelper.nextUrl(pagenumber)}">Next→</a>
            </div></td>
        </tr>
      </table>
    </td>
  </tr>
</table>



코드7-21
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-data-mongodb</artifactId>
</dependency>

코드7-22
package com.tuyano.springboot;

import java.util.Date;

import org.springframework.data.annotation.Id;

public class MyDataMongo {
	@Id
    private String id;
     
    private String name;
    private String memo;
    private Date date;
    
    public MyDataMongo(String name, String memo) {
    	super();
    	this.name = name;
    	this.memo = memo;
    	this.date = new Date();
    }
    
	public String getId() {
		return id;
	}
	public String getName() {
		return name;
	}
	public String getMemo() {
		return memo;
	}
	public Date getDate() {
		return date;
	}
}

코드7-23
package com.tuyano.springboot.repositories;

import org.springframework.data.mongodb.repository.MongoRepository;

import com.tuyano.springboot.MyDataMongo;

public interface MyDataMongoRepository 
		extends MongoRepository<MyDataMongo, Long> {

}

코드7-24
package com.tuyano.springboot;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.transaction.annotation.Transactional;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.servlet.ModelAndView;

import com.tuyano.springboot.repositories.MyDataMongoRepository;

@Controller
public class HeloController {
	
	@Autowired
	MyDataMongoRepository repository;

	@RequestMapping(value = "/", method = RequestMethod.GET)
	public ModelAndView index(ModelAndView mav) {
		mav.setViewName("index");
		mav.addObject("title","Find Page");
		mav.addObject("msg","MyDataMongo의 예제입니다.");
		Iterable<MyDataMongo> list = repository.findAll();
		mav.addObject("datalist", list);
		return mav;
	}
	
	@RequestMapping(value = "/", method = RequestMethod.POST)
	@Transactional(readOnly=false)
	public ModelAndView form(
			@RequestParam("name") String name,
			@RequestParam("memo") String memo,
			ModelAndView mov) {
		MyDataMongo mydata = new MyDataMongo(name,memo);
		repository.save(mydata);
		return new ModelAndView("redirect:/");
	}
	
}

코드7-25
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>top page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	tr { margin:5px; }
	th { padding:5px; color:white; background:darkgray; }
	td { padding:5px; color:black; background:#e0e0ff; }
	table.navi {width:100%; background:white; }
	table.navi tr { background:white; }
	table.navi tr td { background:white; }
	.err { color:red; }
	</style>
</head>
<body>
	<h1 th:text="#{content.title}">Helo page</h1>
	<p th:text="${msg}"></p>
	<table>
	<form method="post" action="/">
	<tr><td><label for="name">이름</label></td>
		<td><input type="text" name="name" /></td></tr>
	<tr><td><label for="memo">메모</label></td>
	<td><textarea name="memo" 
				cols="20" rows="5"></textarea></td></tr>
	<tr><td></td><td><input type="submit" /></td></tr>
	</form>
	</table>
	<hr/>
	<table>
	<tr><th>이름</th><th>메모</th><th>일시</th></tr>
	<tr th:each="obj : ${datalist}">
		<td th:text="${obj.name}"></td>
		<td th:text="${obj.memo}"></td>
		<td th:text="${obj.date}"></td>
	</tr>
	</table>
</body>
</html>

코드7-26
import java.util.List; // 상단 import 부분에 추가

public List<MyDataMongo> findByName(String s);

코드7-27
import java.util.List;  // 상단에 추가

@RequestMapping(value = "/find", method = RequestMethod.GET)
public ModelAndView find(ModelAndView mav) {
	mav.setViewName("find");
	mav.addObject("title","Find Page");
	mav.addObject("msg","MyData의 예제입니다.");
	mav.addObject("value","");
	List<MyDataMongo> list = repository.findAll();
	mav.addObject("datalist", list);
	return mav;
}

@RequestMapping(value = "/find", method = RequestMethod.POST)
public ModelAndView search(
		@RequestParam("find") String param,
		ModelAndView mav) {
	mav.setViewName("find");
	if (param == ""){
		mav = new ModelAndView("redirect:/find");
	} else {
		mav.addObject("title","Find result");
		mav.addObject("msg","「" + param + "」의 검색 결과");
		mav.addObject("value",param);
		List<MyDataMongo> list = repository.findByName(param);
		mav.addObject("datalist", list);
	}
	return mav;
}

코드7-28
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
	<title>find page</title>
	<meta http-equiv="Content-Type" 
		content="text/html; charset=UTF-8" />
	<style>
	h1 { font-size:18pt; font-weight:bold; color:gray; }
	body { font-size:13pt; color:gray; margin:5px 25px; }
	tr { margin:5px; }
	th { padding:5px; color:white; background:darkgray; }
	td { padding:5px; color:black; background:#e0e0ff; }
	</style>
</head>
<body>
	<h1 th:text="${title}">find page</h1>
	<p th:text="${msg}"></p>
	<table>
	<form action="/find" method="post">
		<tr><td>검색:</td>
		<td><input type="text" name="find" size="20" 
			th:value="${value}"/></td></tr>
		<tr><td></td><td><input type="submit" /></td></tr>
	</form>
	</table>
	<hr/>
	<table>
	<tr><th>이름</th><th>메모</th><th>일시</th></tr>
	<tr th:each="obj : ${datalist}">
		<td th:text="${obj.name}"></td>
		<td th:text="${obj.memo}"></td>
		<td th:text="${obj.date}"></td>
	</tr>
	</table>
</body>
</html>

#tpl.js

##���
    tpl.js��һ���Ƚϼ���(��С�����죬����)��jsģ�����棬�����ڸ���js������ʹ�á�
##����
    1. ʹ��js��Ϊģ�����ԣ�������ѧϰ�ɱ�
    2. С�ɣ��ٶȿ쵽����
    3. ������﷨��ģ����д�ǳ�����
    4. mit��Դ��������

##�﷨˵��

###����
tpl.js��ģ���﷨������Ϊ��һ����Ϊjs����䣬���������䡣����˼�壬js������Ǳ���ʱ��ᵱ��jsִ�е���䣬
���������䣬���ǻ����Ϊhtml��

###�����﷨
    1. ����Ϊ��λ��ÿһ����Ϊ���飬��ȥ����ǰ��հ��ַ�
    2. ����в�����<��������ţ���ͷ������Ϊjs,������ǣ�����Ϊ����Ϊ�����
    3. �������!(̾��)��ͷ��Ҳ�Ӹ���Ϊ����С��� !aa
    4. ���������ͨ��@{exp}�����ı���ʽ��Ϊjs���������@{item.name}
    5. ���exp��.(��)��ͷ�����Զ�����Ϊ�ϸ�exp����ʽ�����һ�����ǰ�沿�֡���@{.name}�����Զ�����Ϊ@{item.name}
    6. ���4��exp�������ַ�����"��'��'<�� >�ȡ������ʡ��{}�����š���@.item.name @.name @func(item) @list[i]
    7. �������!!2��̾�ſ�ͷ�����Ӹ���Ϊ������У�������@����ʽ��ԭ���������!!abc@def
    8. ������г���@�ֲ���Ҫtpl.js��������ͨ��\ת�塣��\@abc
    
#ʾ��
```html
<html>
<head>
<meta charset="utf8"/>
<script type="text/javascript" src="tpl.js"></script>
</head>
<body>
�����ڱ��ļ���
<div class="users">
	<script type="tpl">
			<table>
				for(var i=0;i<users.length;i++){
					var user = users[i];
						<tr>
    						<td>@user.name</td>
    						<td>@{.age}year</td>
							<td>@.sex</td>
							<td>@.email\@126.com
						</tr>
				}
			<table>
	</script>
</div>

<p></p>
ͨ��ajax��ȡ����<br>
<script type="tpl" data='./users.js'>
	!!@tplData.lengthԭ�����<br/>
	!@tplData.length�������<br/>
	 <select>
			for(var i=0;i<tplData.length;i++){
					var user = tplData[i];
						<option value="@user.age" age="@.age">
							@.name
						</option>
			}
	 </select>
</script>
 
<div id="result">

</div>

<script type="text/javascript">
	var beg = new Date().getTime();
    var users=[
        {
            name:'name',
            age:12,
            sex:'boy',
            email:'nimei'
        }, {
            name:'name1',
            age:12,
            sex:'boy',
            email:'nimei'
        }
    ];
		
    tpl.render(); //�Զ���Ⱦ������ҳ�е�<script type="tpl">ģ��
    
    var tplText= "<ul>\n"
                +"for(var i=0;i<tplData;i++){\n"
                + "<li>@i</li>\n"
                +"}\n"
                + "<ul>\n";
	/*
    var func = tpl.func(tplText); //��ģ������һ��������ģ������ͨ��tplData��ȡ����
    var html = func(12);//����ģ�庯���������ݲ���12����ģ������tplData����12
    document.getElementById('result').innerHTML=html; //�����ɵ�html����Ϊ��ҳ
    */
	
	var html = tpl.html(tplText,12);//ֱ�Ӵ���ģ�壬�������ȡhtml
	document.getElementById('result').innerHTML=html;
    document.write("ʱ�䣺"+ (new Date().getTime()-beg).toString() +"����");
</script>
</body>
</html>
```

##API
* tpl.html(tplText,daata)
    
    ͨ������tplTextģ�壬������dataֱ�ӻ�ȡģ�����ɵ�html���롣

* tpl.func(tplText)
    
    ��tplText����Ϊһ���������ú���������ģ����ͨ��tplData���á� ���ú󷵻�ģ�������html���롣

* tpl.render()

    �Զ���Ⱦ������ҳ�е�&lt;script type="tpl"&gt;��ǩ�е�ģ�塣���ܱ�֤html dom��ԭ�еĽṹ���൱���滻����ԭ����&lt;script type="tpl"&gt;��ǩ

###���
������ĵ�������tpl.js���е��﷨�ˣ���ӭ��Ҳ����뷴����
Դ���ַ:https://git.oschina.net/tianqiq/tpl.js

    
 

见某网站的输入框支持截屏粘贴的功能，觉得有点意思，于是将代码扒出来分享下。

可惜，目前仅有高版本的 Chrome 浏览器支持这样直接粘贴，其他浏览器目前为止还无法粘贴( IE11没测试过 )，当然这种增强型的用户体验功能有总比没有好。

输入框的结构代码：


++复制代码++代码如下:
<input type="text" id="testInput" />


为输入框绑定粘贴事件：

++复制代码++代码如下:
var input = document.getElementById( 'testInput' );

input.addEventListener( 'paste', function( event ){
    // dosomething...
});


粘贴事件的 Event 接口对象提供了一个 clipboardData 接口，该接口就保存了系统剪贴板中的数据，如上面所说，目前只有高版本的 Chrome 浏览器能直接访问系统剪贴板的数据。这就给截屏后保存到剪贴板中的图片于网页直接进行交互提供了一个入口。

这里所说的截屏，就是 QQ 提供的截屏或者系统自带的 PrtScn 键的截屏功能，或者其他第三方软件提供的截屏功能。


++复制代码++代码如下:
input.addEventListener( 'paste', function( event ){
    // 添加到事件对象中的访问系统剪贴板的接口
    var clipboardData = event.clipboardData,
        i = 0,
        items, item, types;


    if( clipboardData ){
        items = clipboardData.items;


        if( !items ){
            return;
        }


        item = items[0];
        // 保存在剪贴板中的数据类型
        types = clipboardData.types || [];


        for( ; i < types.length; i++ ){
            if( types[i] === 'Files' ){
                item = items[i];
                break;
            }
        }


        // 判断是否为图片数据
        if( item && item.kind === 'file' && item.type.match(/^image\//i) ){
            // 读取该图片            
            imgReader( item );
        }
    }
});


从剪贴板中取到了图片数据，就可以用 FileReader 对其进行读取了。

++复制代码++代码如下:
var imgReader = function( item ){
    var file = item.getAsFile(),
        reader = new FileReader();


    // 读取文件后将其显示在网页中
    reader.onload = function( e ){
        var img = new Image();


        img.src = e.target.result;
        document.body.appendChild( img );
    };

    // 读取文件
    reader.readAsDataURL( file );
};


很短的代码就实现了，可以使用以下源码看看演示。

++复制代码++代码如下:

<!DOCTYPE HTML>
<html lang="en-US">
<head>
<meta charset="UTF-8">
<title>利用 clipboardData 在网页中实现截屏粘贴的功能</title>
<style type="text/css">
#box{ width:200px; height:200px; border:1px solid #ddd; }
</style>
</head>
<body>


<h1>利用 clipboardData 在网页中实现截屏粘贴的功能</h1>   
<hr />
<div><input type="text" id="testInput" placeholder="截屏后粘贴到输入框中" size="30" /></div>

<script type="text/javascript">
(function(){
    var imgReader = function( item ){
        var blob = item.getAsFile(),
            reader = new FileReader();


        reader.onload = function( e ){
            var img = new Image();


            img.src = e.target.result;
            document.body.appendChild( img );
        };


        reader.readAsDataURL( blob );
    };

    document.getElementById( 'testInput' ).addEventListener( 'paste', function( e ){
    var clipboardData = e.clipboardData,
        i = 0,
        items, item, types;


    if( clipboardData ){
        items = clipboardData.items;


        if( !items ){
            return;
        }


        item = items[0];
        types = clipboardData.types || [];


        for( ; i < types.length; i++ ){
            if( types[i] === 'Files' ){
                item = items[i];
                break;
            }
        }


        if( item && item.kind === 'file' && item.type.match(/^image\//i) ){
            imgReader( item );
        }
    }
    });
})();  
</script>


</body>
</html>

<span style="color: rgb(0,0,0);font-size: 14px;">如果开发的应用用户较多，那么必须保证应用在多个版本不同的设备上能够正确的运行。这就要求对各个版本比较熟悉，知道在什么版本中加入了什么新的功能或特性。但是Android的版本太多了，是个令人头疼的问题。如果想了解Android的版本差异，建议读一下Android开发者文档上相关的章节。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">为了让你的应用程序指定可以运行的版本，Android的manifest文件中提供了<uses-</span><span style="color: black;background-color: rgb(160,255,255);font-size: 14px;">sdk</span><span style="color: rgb(0,0,0);font-size: 14px;">>标签。该标签中有三个属性，分别是minSdkVersion，targetSdkVersion，maxSdkVersion。这三个属性比较容易让人迷惑，我也是仔细读了谷歌的官方文档，才弄清楚这三个属性的意义。此外，在项目构建时，还有个概念叫build</span> <span style="color: black;background-color: rgb(255,255,102);font-size: 14px;">target</span><span style="color: rgb(0,0,0);font-size: 14px;">，在本文中也会进行分析。</span>

# <span style="color: rgb(0,0,0);font-size: 14px;">什么是API level</span>

<span style="color: rgb(0,0,0);font-size: 14px;">其实标签<uses-</span><span style="color: black;background-color: rgb(160,255,255);font-size: 14px;">sdk</span><span style="color: rgb(0,0,0);font-size: 14px;">>中指定的并不是我们使用的</span><span style="color: black;background-color: rgb(160,255,255);font-size: 14px;">sdk</span><span style="color: rgb(0,0,0);font-size: 14px;">的版本，也不是Android系统的版本，而是我们使用的Android平台的版本，即API level。API level是一个整数，它指的是我们使用的框架（Framework）的版本，也就是我们使用的</span><span style="color: black;background-color: rgb(160,255,255);font-size: 14px;">sdk</span><span style="color: rgb(0,0,0);font-size: 14px;">中的各个平台下的android.jar。但是这个API level又和Android系统的版本有着对应关系，并且每个系统都会在内部记录它所使用的API level。举例来说，我使用的手机系统是Android 2.3.3， 那么它就会在内部记录使用的API level为10。这个内部的API level可以让系统判定能不能安装一款app，这个问题会在下文中提及。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">下面给出android系统版本，API level和版本代号之间的对应关系表。（该表来自谷歌官方文档：</span>[<span style="color: rgb(0,0,0);font-size: 14px;">http://developer.android.com/guide/topics/manifest/uses-</span>](http://developer.android.com/guide/topics/manifest/uses-)<span style="color: black;background-color: rgb(160,255,255);font-size: 14px;">sdk</span><span style="color: rgb(0,0,0);font-size: 14px;">-element.html#provisional）</span>

![](http://img.blog.csdn.net/20140122171730890?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemhhbmdqZ19ibG9n/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

<span style="color: rgb(0,0,0);font-size: 14px;">由上表可以看出，android的系统版本和API level之间并不是一一对应的，比如Android 2.3， Android 2.3.1， Android 2.3.2对应API level 9， 而Android 2.3.3， Android 2.3.4对应API level 10。API level是Android向开发者提供的一套Framework（android.jar）的代号，可能发布了新的系统版本，但是这一套接口并没有变化，所以就不必提供新的Framework开发包，所以API level也不必改变。由此可知Android系统版本和API level是多对一的关系。由于API level就是发布的android.jar（一套接口）的代号，所以API level和</span><span style="color: black;background-color: rgb(160,255,255);font-size: 14px;">sdk</span><span style="color: rgb(0,0,0);font-size: 14px;">中platforms目录中的各个android.jar是一一对应的。说白了，Android系统版本是给Android用户看的，而API level是给应用程序开发者看的。</span>

# <span style="color: rgb(0,0,0);font-size: 14px;">什么是build</span> <span style="color: black;background-color: rgb(255,255,102);font-size: 14px;">target</span>

<span style="color: rgb(0,0,0);font-size: 14px;">build</span> <span style="color: black;background-color: rgb(255,255,102);font-size: 14px;">target</span><span style="color: rgb(0,0,0);font-size: 14px;">并不存在于manifest文件中，而是存在于项目根目录中的project.properties文件中。如果使用Eclipse构建项目的话，那么每个项目的根目录下都会有一个project.properties文件，这个文件中的内容用于告诉构建系统，怎样构建这个项目。打开这个文件，除了注释之外，还有以下一行：</span>

<span style="color: black;background-color: rgb(255,255,102);font-size: 14px;">target</span><span style="color: rgb(0,0,0);font-size: 14px;">=android-18</span>

<span style="color: rgb(0,0,0);font-size: 14px;">这句话就是指明build</span> <span style="color: black;background-color: rgb(255,255,102);font-size: 14px;">target</span><span style="color: rgb(0,0,0);font-size: 14px;">，也就是根据哪个android平台构架这个项目。指明build</span> <span style="color: black;background-color: rgb(255,255,102);font-size: 14px;">target</span><span style="color: rgb(0,0,0);font-size: 14px;">为android-18，就是使用</span><span style="color: black;background-color: rgb(160,255,255);font-size: 14px;">sdk</span><span style="color: rgb(0,0,0);font-size: 14px;">中platforms目录下android-18目录中的android.jar这个jar包编译项目。同样，这个android.jar会被加入到本项目的build path中。如下图：</span>

![](http://img.blog.csdn.net/20140122174131609?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemhhbmdqZ19ibG9n/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

<span style="color: rgb(0,0,0);font-size: 14px;">每当修改了build</span> <span style="color: black;background-color: rgb(255,255,102);font-size: 14px;">target</span><span style="color: rgb(0,0,0);font-size: 14px;">，就会将另一个android.jar加入到build path中替换原来的jar。将build</span> <span style="color: black;background-color: rgb(255,255,102);font-size: 14px;">target</span><span style="color: rgb(0,0,0);font-size: 14px;">改成android-17后的效果如下图：</span>

![](http://img.blog.csdn.net/20140122174424468?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemhhbmdqZ19ibG9n/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

<span style="color: rgb(0,0,0);font-size: 14px;">如果将build</span> <span style="color: black;background-color: rgb(255,255,102);font-size: 14px;">target</span> <span style="color: rgb(0,0,0);font-size: 14px;">改成android-8，那么就会使用</span><span style="color: black;background-color: rgb(160,255,255);font-size: 14px;">sdk</span><span style="color: rgb(0,0,0);font-size: 14px;">中android-8下的android.jar编译项目，如果在Activity中调用ActionBar相关的Api，那么就会报错，因为ActionBar相关的Api是在API level 11中才加进来的。</span>

![](http://img.blog.csdn.net/20140122175623328?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemhhbmdqZ19ibG9n/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

<span style="color: rgb(0,0,0);font-size: 14px;">一般情况下，应该使用最新的API level作为build</span> <span style="color: black;background-color: rgb(255,255,102);font-size: 14px;">target</span><span style="color: rgb(0,0,0);font-size: 14px;">。这也是eclipse生成项目时的默认行为。</span>

# <span style="color: rgb(0,0,0);font-size: 14px;">android:minSdkVersion</span>

<span style="color: rgb(0,0,0);font-size: 14px;">指明应用程序运行所需的最小API level。如果不指明的话，默认是1。也就是说该应用兼容所有的android版本。我们应该总是声明这个属性。</span>

<span style="color: rgb(255,0,0);font-size: 14px;">如果系统的API level低于android:minSdkVersion设定的值，那么android系统会阻止用户安装这个应用</span><span style="color: rgb(0,0,0);font-size: 14px;">。下载将android:minSdkVersion设置为11， 并且将该应用安装在android 2.3的手机上（对应API level 9），在安装时会有如下提示：</span>

![](http://img.blog.csdn.net/20140122182135031?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemhhbmdqZ19ibG9n/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

<span style="color: rgb(255,0,0);font-size: 14px;">如果指明了这个属性，并且在项目中使用了高于这个API level的API， 那么会在编译时报错</span><span style="color: rgb(0,0,0);font-size: 14px;">。将build</span> <span style="color: black;background-color: rgb(255,255,102);font-size: 14px;">target</span><span style="color: rgb(0,0,0);font-size: 14px;">设为最新的android-19，那么就会使用最新的android-19下的android.jar来编译项目。将minSdkVersion设置为8。在使用的android.jar中，肯定会有和ActionBar相关的API， 但是在项目中调用ActionBar API， 项目会报错。因为minSdkVersion指明的API level 8中不存在ActionBar相关的API。</span>

![](http://img.blog.csdn.net/20140122183244906?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemhhbmdqZ19ibG9n/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

<span style="color: rgb(0,0,0);font-size: 14px;">调用Activity.getActionBar()和ActionBar.getHeight()方法需要API level 11， 但是指定的minSdkVersion为8，所以报错。由此可见，</span><span style="color: rgb(255,0,0);font-size: 14px;">minSdkVersion不仅在程序安装时起作用，也会在项目构建时起作用</span><span style="color: rgb(0,0,0);font-size: 14px;">。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">如果没有设置minSdkVersion这个属性，那么默认是1。表明程序兼容所有的Android系统，能够在所有Android系统上运行。如果使用了高于API level 1 的API， 如ActionBar。那么在构建项目时，会提示和上面相同的错误，项目构建失败。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">android:targetSdkVersion</span>

<span style="color: rgb(0,0,0);font-size: 14px;">标明应用程序目标API Level的一个整数。如果不设置，默认值和minSdkVersion相同。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">这个属性通知系统，你已经针对这个指定的目标版本测试过你的程序，系统不必再使用兼容模式来让你的应用程序向前兼容这个目标版本。应用程序仍然能在低于targetSdkVersion的系统上运行。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">由于Android不断向着更新的版本进化，一些行为甚至是外观可能会改变。然而，</span><span style="color: rgb(255,0,0);font-size: 14px;">如果平台的API Level高于你的应用程序中的targetSdkVersion属性指定的值，系统会开启兼容行为来确保你的应用程序继续以期望的形式来运行</span><span style="color: rgb(0,0,0);font-size: 14px;">。你可以通过指定targetSdkVersion来匹配运行程序的平台的 API level来禁用这种兼容性行为。举例来说，设置这个值为11或更高，当你的应用运行在Android3.0或更高的系统上时，系统会为你的应用使用新的默认主题（Holo主题），并且当运行在大屏幕的设备上时会禁用屏幕兼容模式（screen compatibility mode），因为支持了 API level 11就暗示了支持大屏幕。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">根据你设置的targetSdkVersion 的值，系统会执行很多兼容行为。一些行为在对应平台版本的Build.</span><span style="color: black;background-color: rgb(153,255,153);font-size: 14px;">VERSION</span><span style="color: rgb(0,0,0);font-size: 14px;">_CODES中有讨论。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">为了让你的应用程序支持每个Android版本，你应当提高targetSdkVersion的值到最新的API level，然后在对应的平台上彻底的测试你的应用。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">从上面的论述可知，</span><span style="color: rgb(255,0,0);font-size: 14px;">targetSdkVersion这个属性是在程序运行时期起作用的，系统根据这个属性决定要不要以兼容模式运行这个程序</span><span style="color: rgb(0,0,0);font-size: 14px;">。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">一般情况下，应该将这个属性的值设置为最新的API level 值，这样的话可以利用新版本系统上的新特性。eclipse在生成项目时，默认将该值设置为最高，如果设置一个较低的值，会给出一个警告，如下图所示。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">这个警告的意思是没有将targetSdkVersion的值设置为最高值，较新的系统会以兼容模式运行该程序。请考虑在新版本系统上测试程序并将targetSdkVersion设置为最新。更详细的信息请参考android.os.Build.</span><span style="color: black;background-color: rgb(153,255,153);font-size: 14px;">VERSION</span><span style="color: rgb(0,0,0);font-size: 14px;">_CODES 。</span>

# <span style="color: rgb(0,0,0);font-size: 14px;">android:maxSdkVersion</span>

<span style="color: rgb(0,0,0);font-size: 14px;">标明可以运行你的应用的最高API Level版本。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">在Android1.5， 1.6， 2.0 和2.0.1，在安装应用或系统升级时，系统会检查这个值。在这两种情况下，如果应用设置的maxSdkVersion 值低于系统本身使用的API Level，系统将不会允许安装该应用。在系统升级后，新系统会重新校验这个值，如果新系统的API Level高于这个值，新系统会删除你的应用。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">在高于2.0.1的系统上，安装应用时不会再检验应用中设置的maxSdkVersion值，在系统升级后也不会重新校验这个值。但是在向用户展示可用的应用时，Google Play会继续使用这个属性进行过滤。</span>

<span style="color: rgb(255,0,0);font-size: 14px;">maxSdkVersion这个属性本来是在程序安装时和系统升级后起作用的</span><span style="color: rgb(0,0,0);font-size: 14px;">。但是根据官方文档中的说明， 已经不再推荐使用这个属性。</span>

<span style="color: rgb(0,0,0);font-size: 14px;">经过测试，将maxSdkVersion的值设置成9，程序是可以安装在4.2的手机上的。说明这个值已经不再起作用。</span>

<pre style="text-align:start;"> <span style="color: black;background-color: rgb(160,255,255);">sdk</span> <span style="color: rgb(0,0,0);">android:minSdkVersion="8"</span> <span style="color: rgb(0,0,0);">android:targetSdkVersion="19"</span> <span style="color: rgb(0,0,0);">android:maxSdkVersion="9"/></span> </pre>
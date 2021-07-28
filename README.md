1.复制packUpload.gradle文件到项目根目录

2.项目根目录的build.gradle添加这些
```

ext {
    jiagubaoPath = 'C:\\jiagubao\\jiagu' //  加固保安装的路径，不要用中文路径
    title="youbao"          //APPtitle，这个可不写，我自己项目写了方便区分不同的app
    storeFile = file('./app/youbao.jks')               // 签名文件位置，根据实际情况写
    storePassword = ''                 //  密码
    keyAlias = ''                           // app别名
    keyPassword = ''                  //  key密码
    jiaGu_UserName = ''          //  360加固保用户名
    jiaGu_Pwd = ''                    //  360加固保登录密码
}
```


3.可选:app的build.gradle里添加这些，修改打包时候的文件名，不写这个的话需要修改packUpload.gradle里的apk文件名构成，比如44行的代码
```
android {
    ...
    //修改打包文件名
    applicationVariants.all {
        variant ->
            variant.outputs.all {
                //在这里修改apk文件名
                outputFileName = "${variant.name}-${rootProject.ext.title}-v${variant.versionName}.apk"
            }
    }
}
```

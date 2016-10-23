###初遇java若干的问题

- - -
- Error:(5, 7) Gradle: 错误: 类HelloWorld是公共的, 应在名为 HelloWorld.java 的文件中声明

公共类名应与文件名同名
      我们一般写的类都是公共的（public），JAVA要求保存公共类的文件的文件名必须与类同名，而且要注意大小写。否则会报错：类XX是公共的，应在名为XX.java的文件中声明。这里的“XX”指代某个类名，以下亦然


- - -
Android输出乱码
解决办法
解决办法，在Java工程目录下的build.gradle添加如下代码，然后重新运行一遍。 
1.新版gradle

tasks.withType(JavaCompile) {
    options.encoding = "UTF-8"
}
2.旧版gradle

tasks.withType(Compile) {
    options.encoding = "UTF-8"
}

- - -

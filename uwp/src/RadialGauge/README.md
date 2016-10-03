#win10 uwp 车表盘 径向规

车表盘就是有刻度的圆盘加上针，这个控件可以直观让用户知道当前的速度或其他

看名字不知道是什么，我就放一张图

![这里写图片描述](http://img.blog.csdn.net/20160903165703064) 

![这里写图片描述](http://img.blog.csdn.net/20160903173217169) 

使用很简单，在Nuget，Radial Gauge

![这里写图片描述](http://img.blog.csdn.net/20160903165948549) 

要使用大神做的，简单，在使用我们需要在Nuget下载，然后在引用` xmlns:controls="using:WinRTXamlToolkit.Controls"`

我们需要知道每个值是什么

![这里写图片描述](http://img.blog.csdn.net/20160903173511567) 

tick:最上面表盘，我们可以修改颜色TickBrush，我们颜色可以用SolidColorBrush、ImageBrush、LinearGradientBrush

我们对每个值都可以修改，可以是颜色，图片。

trail:我们可以修改颜色，如果需要修改大小，我们修改下面的scaleTick

scaleTick:可以修改颜色，大小，ScaleWidth就是大小，ScaleTickBrush颜色

scale:还没有使用的，可以设置颜色,设置大小ScaleWidth可以让中心有没空白

Minimum：我们可以修改和进度条那最大值，最小值

Unit：下面写的字，我写了博客

needle：指针，英文我就不翻译

```

            <controls:Gauge

                x:Name="Gauge"

                Value="10"

                Unit="http://blog.csdn.net/lindexi_gd"

                ScaleTickBrush="Gainsboro"

                TickBrush="Black"

                ScaleWidth="50"

                Margin="1,50,1,100" Width="600">

                <controls:Gauge.TrailBrush>

                    <SolidColorBrush Color="Red"></SolidColorBrush>

                </controls:Gauge.TrailBrush>

                <controls:Gauge.ScaleBrush>

                    <SolidColorBrush Color="Cornsilk"></SolidColorBrush>

                </controls:Gauge.ScaleBrush>

                <controls:Gauge.NeedleBrush>

                    <LinearGradientBrush EndPoint="1,0">

                        <GradientStop Color="Transparent" />

                        <GradientStop Color="Goldenrod"

                          Offset="0.5" />

                        <GradientStop Color="Transparent"

                          Offset="1" />

                    </LinearGradientBrush>

                </controls:Gauge.NeedleBrush>

            </controls:Gauge>

```

如果感兴趣可以去https://github.com/xyzzer/WinRTXamlToolkit

如果大小觉得不是我们要的，可以用ViewBox，直接设置大小

说到这我用xaml画Windows10，应该大家看到上面gif，我用了它图片，其实我用path

```

 <Grid Margin="10,10,10,10">

 <Path Stroke="Blue" StrokeThickness="1" Fill="#0078d6" Data="M0 12.49l35.7-4.9v34.5H0M40 6.91L87.3 0V41.8H40M0 45.74h35.7v34.6L0 75.34M40 46.2H87.3v41.4L40 80.9 "></Path>

 <Path Fill="#0078d6" Data="M113.95 16.99c2.25.01 4.5.01 6.76.04 3.51 12.68 6.97 25.38 10.49 38.07.75 2.66 1.31 5.38 1.64 8.14 3.66-15.57 8.66-30.81 12.86-46.25 1.95.01 3.9.01 5.85.02 3.09 10.99 5.98 22.03 9.04 33.03 1.13 4.38 2.59 8.7 3.05 13.23 3.31-15.55 8.03-30.79 11.78-46.24 2.22-.03 4.44-.03 6.66-.03-4.84 17.69-9.88 35.33-14.78 53h-7.21c-3.55-12.69-7.07-25.39-10.66-38.06-.6-2.05-.85-4.17-1.04-6.29-.28 1.83-.54 3.68-1.01 5.47-3.63 12.92-7.31 25.82-10.84 38.76-2.4.13-4.8.14-7.2.12-5.15-17.66-10.26-35.34-15.39-53.01"></Path>

 <Path Fill="#0078d6" Data="m186.2 17.42a4 4 0 1 1 0 1M187.1 32h6v38h-6"></Path>

 <Path Fill="#0078d6" Data="M209.06 38.12c3.43-6.11 11.43-8.92 17.88-6.09 5.13 2 7.04 7.94 7.2 13 .28 8.32.05 16.65.12 24.97-2 0-4 0-6-.01-.09-7.99.21-16-.14-23.99-.16-3.96-1.84-8.72-6.15-9.73-6.29-1.9-12.57 3.77-12.77 9.99-.18 7.91-.01 15.83-.07 23.74h-6c.01-12.67.01-25.33 0-38h6.01c-.01 2.04-.02 4.08-.08 6.12"></Path>

 <Path Fill="#0078d6" Data="M270.13 14.01c2-.01 4-.01 6-.01v56h-5.98c.01-2.03-.03-4.06-.17-6.09-4.33 7.78-15.91 9.5-22.53 3.73-4.73-4.07-6.17-10.69-5.92-16.68.05-6.08 2.05-12.54 6.89-16.51 6.29-5.18 17.44-4.88 21.75 2.73-.08-7.73-.01-15.45-.04-23.17m-12.92 22.14c-4.8.76-8.05 5.14-8.95 9.67-1.18 5.46-.97 11.78 2.47 16.42 3.72 4.94 11.93 5.05 15.91.38 2.71-2.82 3.48-6.86 3.5-10.64.03-3.99.37-8.49-2.28-11.82-2.34-3.33-6.71-4.83-10.65-4.01"></Path>

 <Path Fill="#0078d6" Data="M299.47 31.06c5.35-.47 11.28.37 15.3 4.24 4.54 4.19 5.89 10.7 5.64 16.65-.07 5.35-2.05 10.78-5.97 14.51-8.18 7.44-23.37 5.81-28.56-4.42-4.08-8.57-3.26-20.43 4.19-26.94 2.67-2.26 6.05-3.29 9.4-4.04m-1.08 5.44c-8.81 2.71-10.3 14.22-7.55 21.79 2.19 6.72 10.73 9.7 16.86 6.56 4.15-1.91 6.04-6.59 6.44-10.88.45-5.01.05-10.69-3.49-14.6-3-3.38-8.08-4.11-12.26-2.87"></Path>

 <Path Fill="#0078d6" Data="M322.91 32h6.26c2.48 9.05 4.88 18.12 7.41 27.16.51 1.7.7 3.46.88 5.22 2.83-10.9 6.41-21.6 9.62-32.39l5.47.03c2.75 10.8 6.17 21.44 8.45 32.35 2.35-10.85 5.69-21.46 8.3-32.25 2.01-.1 4.02-.13 6.04-.15-3.81 12.67-7.46 25.38-11.29 38.03h-6.22c-2.7-10.3-6.2-20.4-8.39-30.81-2.61 10.4-6.23 20.52-9.21 30.81h-6.01c-3.76-12.67-7.6-25.31-11.31-38"></Path>

 <Path Fill="#0078d6" Data="M390.46 31.04c3.75-.26 7.57.1 11.1 1.48.98 1.86.22 4.3.45 6.39-4.21-2.63-10.01-4.31-14.58-1.63-3.13 1.7-3.28 6.73-.23 8.6 4.37 2.83 9.92 3.57 13.8 7.21 4.28 4.12 3.24 12.04-1.77 15.13-6.09 3.88-14.11 3.5-20.49.54 0-2.24-.01-4.48-.05-6.72 4.54 3.46 10.92 5.38 16.35 2.92 3.17-1.59 3.33-6.46.54-8.51-4.37-3.22-10.36-3.73-14.24-7.75-3.83-3.86-3.14-10.96 1.13-14.23 2.21-2.03 5.2-2.64 7.99-3.43"></Path>

 <Path Fill="#0078d6" Data="M432.27 16.15c.53-.07 1.59-.22 2.11-.29.03 18.04.01 36.09.01 54.14h-5.92c.04-15.02-.1-30.05.07-45.07-3.77 2.61-7.84 4.84-12.27 6.08.03-2 .05-4 .07-6 5.8-1.97 11.08-5.15 15.93-8.86"></Path>

 <Path Fill="#0078d6" Data="M456.26 16.13c5.2-.87 10.97 1.03 14.06 5.45 4.39 6.2 4.8 14.15 5.02 21.48-.15 7.74-1 16.13-5.94 22.44-4.55 5.97-13.87 7.37-19.97 2.98-4.95-3.57-6.89-9.8-7.77-15.57-1-8.57-.91-17.56 2.07-25.74 1.88-5.55 6.52-10.33 12.53-11.04m-.92 5.37c-5.33 2.16-6.86 8.46-7.6 13.58-.78 7.14-.96 14.5.74 21.53.85 3.46 2.64 7.13 6.07 8.65 3.89 1.96 9.09.27 11.14-3.57 3.27-5.65 3.35-12.43 3.39-18.78-.13-6.19-.38-12.85-3.8-18.23-2.03-3.28-6.4-4.6-9.94-3.18"></Path>

 </Grid>

```

如果大小觉得不是你要的，使用ViewBox，然后这个是放大多少都不会模糊。

修改Fill修改颜色，修改Stroke修改边框，第一个是田后面就是垃圾wr

[http://blogs.u2u.be/diederik/post/2015/12/14/The-Radial-Gauge-goes-UWP.aspx](http://blogs.u2u.be/diederik/post/2015/12/14/The-Radial-Gauge-goes-UWP.aspx)

使用代码：https://github.com/lindexi/UWP/tree/master/uwp/src/RadialGauge

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />本作品采用<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">知识共享署名-非商业性使用-相同方式共享 4.0 国际许可协议</a>进行许可。欢迎转载、使用、重新发布，但务必保留文章署名[林德熙](http://blog.csdn.net/lindexi_gd)(包含链接:http://blog.csdn.net/lindexi_gd )，不得用于商业目的，基于本文修改后的作品务必以相同的许可发布。如有任何疑问，请与我[联系](mailto:lindexi_gd@163.com)。

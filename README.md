# UnoApp
Uno Platform  测试app  https://platform.uno/docs/articles/getting-started-tutorial-1.html

# 要点

1. UWP要选择生成平台,例如X86,选AnyCPU不能正确调试

2. 编辑MainPage.xaml文件出现错误"空路径名是非法的",经查证是vs的bug,新建工程仍然不能解决就用vsc先编辑玩着吧. 参考链接 https://developercommunity.visualstudio.com/content/problem/889907/uwp-hot-reload-does-not-work-for-xaml-files-in-a-s.html

3. 各个平台要独立引用需要的库,不同平台库名称可能有所差异

4. [各平台条件编译](https://platform.uno/docs/articles/platform-specific-csharp.html)

| Platform | Symbol | 备注 |
| :----:| :----: | :----: |
| UWP | NETFX_CORE | 旧版为(WINDOWS_UWP) |
| iOS | \__IOS__ |  |
| Android | \__ANDROID__ |  |
| WebAssembly | \__WASM__ |  |
| MacOS | \__MACOS__ |  |
| Skia | \__SKIA__ |  |

5. [多平台实现的分部类,比一大堆#if更优美,例如 NativeWrapperControl.cs , NativeWrapperControl.Android.cs, 类似razor代码后置](https://platform.uno/docs/articles/platform-specific-csharp.html)

6. [多平台显示不同文本,类似xamarin form](https://platform.uno/docs/articles/platform-specific-xaml.html)
```
<TextBlock Text="This text will be large on Windows, and pink on WASM"
				   win:FontSize="24"
				   wasm:Foreground="DeepPink"
				   TextWrapping="Wrap"/>
		<TextBlock android:Text="This version will be used on Android"
				   not_android:Text="This version will be used on every other platform" />
		<ios:TextBlock Text="This TextBlock will only be created on iOS" />
```
    
    

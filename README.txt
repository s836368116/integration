2016-11-01版本修改内容如下：
1、getimage和getvoxel线程是并行的
2、getvoxel线程结束之后再进行pathplan线程，这里的A*算法依然是需要全局地图
3、每获取一帧点云文件（即depth.log）界面会显示一帧，这就导致图像显示较慢，卡顿现象比较明显
4、在主线程中又增加了一个用户定义消息WM_UPDATE_STATUS,用来接收子线程传回来的除显示图片以外的消息
5、对DialogDlg.cpp文件中的全局变量做了一次排版，更新Init函数为InitVariable函数，逻辑更加合理
6、没有对界面做美化

2016-11-02版本修改内容如下：
1、修改了getimage线程的内容，之前存在left不存在depth时，depth自动补零，压到vector中；现在只要depth不存在，就跳过这一帧，如果depth存在且left不存在，那么left=Mat（0）压到vector中
2、三平修改后的路径规划程序集成进去了，不过还没有测试；因为路径规划程序还有些问题；
3、如今是getvoxel处理完全部帧后，才进行pathplan，记住以后这样修改：getvoxel每处理完一帧，pathplan执行一次，然后getvoxel再处理下一帧，依次循环下去。
4、界面美化过了

2016-11-06版本修改内容
1、三平的路径规划程序已经集成进去
2、体素化程序和原来的版本完全一致（测试输入"桌面\4"）
3、注意：路径规划程序每次运行的结果drawPoint文件都会有个别值不同，集成后保证和源程序的drawPoint文件中的结果绝大多数一样
		allPoint文件是完全一样的（测试输入"桌面\4"）
What's the matter?

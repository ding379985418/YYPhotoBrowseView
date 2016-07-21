# YYPhotoBrowseView 从YYKitDemo中抽离出来的图片浏览器
---- 
## 效果图
![][image-1]
## 说明：
######研究YYKit时，发现Demo中图片浏览器效果不错，YYKit作者没有抽离出来，然后我就将其抽离出来作为一个单独部分，最终版权归YYKit作者ibireme所用，使用方法请参考下面或YYKitdemo。
## 使用方法：
1、将YYPhotoBrowseView文件夹拖入项目

2、添加libz、libsqlite3库 

_注意：如果你项目中引用过YYKit，请不要将Quartz和YYWebImage两个文件夹拖入项目中_

3、创建装有YYPhotoGroupItem对象的数组items

	NSMutableArray *items = [NSMutableArray array];
	    UIView *fromView = nil; //点击的imageview
	    for (int i =0; i < _dataSource.count; i++) {
	        YYPhotoGroupItem *item = [YYPhotoGroupItem new];
	        //设置item中原来的缩略图的imagView
	        item.thumbView = self.imageViews[i];
	        //每个缩略图的imagView的高清图的地址
	        NSURL *url = [NSURL URLWithString:_dataSource[i];
	        item.largeImageURL = url;
	        [items addObject:item];
	        if (i == selectIndex) {
	        //所点击的缩略图的imageView
	            fromView =  self.imageViews[i];
	        }
	    }
4、实例化 YYPhotoBrowseView ，并展示视图

	YYPhotoBrowseView *groupView = [[YYPhotoBrowseView alloc]initWithGroupItems:items];
	    [groupView presentFromImageView:fromView toContainer:self.navigationController.view animated:YES completion:nil];

[image-1]:	https://github.com/ding379985418/YYPhotoBrowseView/blob/master/YYPhotoBrowseView.gif "动画效果图"
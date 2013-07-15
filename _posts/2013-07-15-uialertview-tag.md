---
layout: post
title: "UIAlertViewやUIActionSheetを識別する"
description: ""
categories: [Objective-C, iOS]
tags: [tips, delegate]
---
{% include JB/setup %}

今更iPhoneアプリ開発などやっているわけですが、ARCがついていて昨今はお手軽なようです。  
さておき、お作法がいろいろあってWebのようにフリーダムには行きません。  
その代わり標準でいろいろついているので大体はそれを使えばなんとかなります。

さて本題に移ります。
同じViewControllerの中でアラートやアクションシートが複数ある場合も、デリゲートがselfであれば同じ

	- (void)alertView:(UIAlertView *)alertView clickedButtonAtIndex:(NSInteger)buttonIndex

とか

	- (void)actionSheet:(UIActionSheet *)actionSheet clickedButtonAtIndex:(NSInteger)buttonIndex

とかを通るわけです当たり前ですね。  
単にOKボタンがあるようなアラートならいいんですが、クリックしたボタンによって処理を変えたい場合はどうしましょうか。  
クラス分けて作った方がいいのでしょうがそれだけのためにわざわざ作るのも面倒臭いし、さらに増えると無惨です。

やり方は難しさの欠片もなく、単にtagをつけてやればそれで事足ります。  
これはUIViewにある識別用プロパティで、UIAlertViewもUIActionSheetもUIViewを継承しているので同様に使えるわけです。  

    UIActionSheet *actionSheet = [[UIActionSheet alloc]
                            initWithTitle:nil
                            delegate:self
                            cancelButtonTitle:@"Cancel"
                            destructiveButtonTitle:@"注意"
                            otherButtonTitles:@"処理1", @"処理2", nil];
    sheet.tag = 1;
    [sheet showInView:self.view];

とやっておけば、

	-(void)actionSheet:(UIActionSheet *)actionSheet clickedButtonAtIndex:(NSInteger)buttonIndex {
    	NSLog(@"clicked : %d", buttonIndex);
	    NSLog(@"actionSheet tag %d", actionSheet.tag);
	}

`actionSheet.tag`に1が入ってきます。連番でなくてもかまわないので100でも1000でも256でもいけるようです。

Cancelを押すと以下のようにログが出るはず。

> 2013-07-15 13:05:17.486 actionSheetTest[6093:c07] clicked : 3  
> 2013-07-15 13:05:17.486 actionSheetTest[6093:c07] actionSheet tag 1
# EasySearchBar
自定义SearchBar，由于系统的searchBar扩展性不强，所以打算自定义SearchBar，就有了此框架。


## Join Us 
为了更好的完善EasySwift框架，希望更多对此框架有兴趣的朋友一起加入进来打造最好用最全面扩展最好的swift框架。
[EasySwift](https://github.com/stubbornnessness/EasySwift)官方QQ群：<mark>**542916901**</mark>

## Mark
先更新Github上的项目，所以最新的项目一定在[Github](https://github.com/stubbornnessness)上。

## Features
* 自定义SearchBar

## System Requirements
iOS 8.0 or above

## Installation
### As a CocoaPods Dependency
Add the following to your Podfile:

	pod 'EasySearchBar'
	
## Version
**V0.0.1** ---- 2016-7-1

* 首次发版
	
## Example
	import UIKit
	import EasySwift

	class ClassifyVC: BaseVC {

    private var searchBar: YXJ_SearchBar?

    @IBOutlet weak var titleView1: UIView!

    override func viewDidLoad() {
        super.viewDidLoad()

    }

    override func loadUI() {

        titleView1.w = ScreenWidth

        // 搜索框
        self.searchBar = YXJ_SearchBar(frame: CGRectMake(0, (self.titleView1.h - 30) / 2, titleView1.w - 60, 30))
        self.searchBar?.YXJ_searchBarPlaceholder = "搜索课程"
        self.searchBar?.YXJ_backgroundColor = UIColor(hexString: "#F2F2F2")
        self.titleView1.addSubview(self.searchBar!)

        self.searchBar?.YXJ_cancelBTClickedBlock({ (search) in
            log.debug("点击了取消按钮")
            search.text = ""
        })
        self.searchBar?.YXJ_SearchBarTextDidBeginEditingBlock({ (search) in
            log.debug("开始编辑" + search.text!)
        })
        self.searchBar?.YXJ_SearchBarTextDidChangeBlock({ (search, searchText) in
            log.debug("内容改变" + searchText)
        })
        self.searchBar?.YXJ_SearchBarTextDidEndEditingBlock({ (search) in
            log.debug("结束输入")
        })
        self.searchBar?.YXJ_SearchBarSearchButtonClickedBlock({ (search) in
            log.debug("点击键盘搜索" + search.text!)
        })

        // 历史按钮
        let btn = UIButton(frame: CGRectMake(titleView1.w - 62, 0, 50, titleView1.h))
        btn.setImage(UIImage(named: "history"), forState: UIControlState.Normal)
        self.titleView1.addSubview(btn)
        btn.bnd_controlEvent.filter { (event) -> Bool in
            return event == UIControlEvents.TouchUpInside
        }.observe { [weak self](event) in
            self?.pushWithOtherStoryBoard_Swift("HistoryVC", storyBoardName: "Home")
        }
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
    }
}

    
## 极致框架
* EasySwift是从2014年开始打造的贯穿整个Swift开发的整套解决方案，只为最简单，最高效，最全面，高扩展性，囊括最前沿的架构，思想在其中[EasySwift](https://github.com/stubbornnessness/EasySwift)

## License
EasyEmoji is licensed under the Apache License, Version 2.0 License. For more information, please see the LICENSE file.

# 天天基金爬虫
爬取天天基金网，辅助对基金投资的选择

## 功能特性
- 爬取天天基金网上所有的基金，及相应基金经理，以往的收益率等

- 模仿tcp的拥塞控制的反爬控制，线程数量，慢开始，拥塞避免
- 爬取全部数据需要470s（不使用代理），瓶颈为网站的反爬策略
- 留有从文件中批量导入代理ip的代码，理论上可大大提升爬取效率（需简单修改代码）
    - 爬取免费代理的脚本在另一个profile，crawler_tools，爬取的对象为西刺所提供的免费代理ip
    - 由于免费代理ip非常不稳定，大概率会导致比原本更慢的情况
- 结果展示
![Image text](./image/result.png)
    2019/08/21 共有7182个基金，其中 007560,中融恒鑫纯债A、007561,中融恒鑫纯债C\爬取失败

## 食用方法
- 下载脚本文件 fundcrawler.py
- 在我的另一个仓库（Crawler-Tools）下载 FakeUA.py

      这一步非必须，若无，则会在爬取全程使用唯一的chrome ua，可能会影响到爬取的效率
      也可自己实现FakeUA类，在爬取脚本中会通过 FakeUA().random 获取 随机的ua(str)
- 设置爬取后的基金筛选条件
      
      在代码的末尾处对原数据进行修改，非必须
      choice_return = {'近1月收益': 6.41, '近3月收益': 24.55, '近6月收益': 10.91, '近1年收益': -3.64,
                     '近3年收益': 18.35, '成立来收益/保本期收益': 0, '本基金任职收益': 0}
      choice_time = {'本基金任职时间': [1, 0], '累计任职时间': [3, 0]}

- 运行fundcrawler.py并等待
      
## 以后的更新
- 重构
- 数据可视化

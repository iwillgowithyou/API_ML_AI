# Anti_violence

| 发布日期   | 2019-12-10     |
| ---------- | -------------- |
| 项目名称   | 净化视界 |
| 项目现状   | 进行中         |
| 项目所有者 | 罗嘉琪         |
| 项目设计师 | 罗嘉琪         |
| 项目开发者 | 罗嘉琪         |
| 项目测试者 | 罗嘉琪         |

# 净化视界
## 项目背景
 网络暴力是一种由网络衍生出的看似虚拟的暴力形式,在这个互联网蓬勃发展的时代,网络给人们提供了多元的发表意见的平台,为人们发表言论提供了便捷的途径,但随之而来的,是使得一部分人原本浮躁的心态更加浮躁,网络暴力的现象应运而生,不仅严重地影响了当事人的生活安宁和社会的正常秩序，甚者还有许多当事人因此丧命。
 
## 项目介绍
 净化视界是一个由用户自主审核并提交举报的软件，目前暂时只支持哔哩哔哩视频网站的弹幕内容下载和举报，随着弹幕文化的普及，将会陆续开放各大视频网站的举报途径。由于每个视频的弹幕数量不一，小批量的弹幕数量可以通过客户端举报，当视频的弹幕量达到1min/240及以上时，首先会影响一部分观感，其次从中抓取网暴言论也十分麻烦。本项目建议使用于弹幕量1min/240以上的视频中，通过客户端下载ass弹幕文件并由软件转码为txt，再由百度API提供的文本审核进行审核，最后筛选出各等级网暴言论由用户进行举报。
 
## 核心价值
  产品的核心价值为检测txt文件中的违禁文本，并将其罗列在用户面前。
 
## 项目理念
 - 减小网暴对视频作者的影响
 - 减轻风纪委员（视频网站审核员）的工作强度
 - 营造更清净的观看环境
 
## 项目操作流程
 1.用户在哔哩哔哩选择视频下载弹幕ass文件
 2.用户上传ass文件
 3.挑选经过软件审核的弹幕进行举报
 
## 用户痛点
- 观看视频过程中经常出现与视频不符的弹幕，但举报流程十分繁杂，面对大量网暴弹幕无法及时清除
- 大量的视频使得风纪委员（审核员）无法第一时间查看举报内容或删除举报内容

## 需求列表与人工智能API加值
| 功能   | 用户案例     | 重要程度     |
| ---------- | -------------- | -------------- |
| 自动转码   | 用户在视频网站下载的弹幕文件为ass，可以直接上传到软件中转码 |重要   |
| 筛选功能   | 太多的内容使用户想选取其中言语辱骂较为严重的区域进行查看         |很重要   |
| 举报功能 | 对于用户筛选出的言论进行最终的举报         |很重要   |
#### 使用的API：
- 百度智能云文本检测
- Bilibili开放平台举报API 
## 原型

## API 产品使用关键AI或机器学习之API的输出入展示
### API1.使用水平
- 文本审核
- 输入
```
def check_content():
    request_url = 'https://aip.baidubce.com/rest/2.0/antispam/v2/spam?access_token=【你自己的access token哦！！！】'
    items = {'1':'暴恐违禁', '2':'文本色情', '3':'政治敏感', '4':'恶意推广', '5':'低俗辱骂', '6':'低质灌水'}

    with open('./baidu_data/checked_data_1.txt', 'r', encoding='utf8') as fr:
        with open('./baidu_data/data_1_check_result.txt', 'a', encoding='utf8') as fw:
            for i, each in enumerate(fr.readlines()):
                print('正在检测样本：{}'.format(i))
                params = {'content': each.strip().split('\t')[-1]}
                result = requests.post(request_url, headers={'Content-Type': 'application/x-www-form-urlencoded'}, data=params).text
                predict_res = (json.loads(result).get('result')).get('reject')
                print(predict_res)

                if len(predict_res) == 0:
                    # 普通直接保存
                    fw.write('普通\t'+'0\t###\t'+each)
                else:
                    # 获取拒绝得分最高的那个
                    score = []
                    content = []
                    for each_hit in predict_res:
                        score.append(each_hit.get('score'))
                        temp = each_hit.get('hit')
                        content.append(str(each_hit.get('label'))+'\t'+','.join(each_hit.get('hit'))+'\t')
                    # 找到得分最大的那个索引
                    max_score_index = score.index(max(score))
                    tag_label = content[max_score_index]
                    # 写入
                    fw.write('{}\t'.format(items.get(tag_label.split('\t')[0]))+tag_label+each)
```


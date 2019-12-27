# Anti_violence

| 发布日期   | 2019-12-10     |
| ---------- | -------------- |
| 项目名称   | 净化视界 |
| 项目现状   | 进行中         |
| 项目所有者 | 罗嘉琪         |
| 项目设计师 | 罗嘉琪         |
| 项目开发者 | 罗嘉琪         |
| 项目测试者 | 罗嘉琪         |

# 目录
- [价值主张设计](#净化视界) 
    - [项目背景](#项目背景)
    - [项目介绍](#项目介绍)
    - [核心价值](#核心价值)
    - [项目理念](#项目理念)
    - [项目操作流程](#项目操作流程)
    - [用户痛点](#用户痛点)
    - [需求列表与人工智能API加值](#需求列表与人工智能API加值) 
- [原型](#原型)
    - [产品原型图](#产品原型图)
- [API](#API产品使用关键AI或机器学习之API的输出入展示)
    - [API1.使用水平](#API1.使用水平)
    - [API2.使用比较分析](#API2.使用比较分析)
    - [API3.使用后风险报告](#API3.使用后风险报告)
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
### 1.原型源文件[下载地址](https://gitee.com/NFUNM062/API_final_axure)
### 2.[Axure高保真原型](https://nfunm062.gitee.io/api_final_axure/#g=1&p=%E5%90%AF%E5%8A%A8%E9%A1%B5%E5%92%8C%E5%BC%95%E5%AF%BC%E9%A1%B5)
### 3.产品原型图
#### **3.1启动页和引导页**
- **启动页**
![启动页](http://chuantu.xyz/t6/709/1577453738x2890211847.png)
- **引导页**
![引导页](http://chuantu.xyz/t6/709/1577454304x989499252.jpg)




## API 产品使用关键AI或机器学习之API的输出入展示
### API1.使用水平
#### · 获取access_token代码示例
#### · 输入
```
import requests 
import urllib
def get_access_key():
    # client_id 为官网获取的AK， client_secret 为官网获取的SK
    host = 'https://aip.baidubce.com/oauth/2.0/token?grant_type=client_credentials&client_id=bQBglXgN7ZHh9CwzRKLsAp28&client_secret=MhRyj5DaiAGvOZr9cFQMzyls0kdmGjBU'
    request = urllib.request.Request(host)
    request.add_header('Content-Type', 'application/json; charset=UTF-8')
    response = urllib.request.urlopen(request)
    content = response.read()
    if (content):
        print(content)
```
#### · 输出
```
b'{"refresh_token":"25.fc46e230176f79544c50cdf981d80821.315360000.1892389261.282335-18084954","expires_in":2592000,"session_key":"9mzdXRcAGnjUR4kZrId\\/GmoSv0Ou634xIqbKIsrARQt13r6IkG42uQgpkQAApHRkpEnogCnnQMr9D1IA6+egTndTI+Elaw==","access_token":"24.fcb4e1efc8619b18f80c1060e4d53eea.2592000.1579621261.282335-18084954","scope":"audio_voice_assistant_get brain_enhanced_asr audio_tts_post public vis-ocr_ocr vis-antiporn_antiporn_v2 vis-classify_watermark brain_ocr_scope brain_gif_antiporn brain_ocr_general brain_ocr_general_basic vis-classify_terror vis-ocr_business_license brain_ocr_webimage brain_all_scope vis-starface_public_person solution_face brain_ocr_idcard brain_ocr_driving_license brain_ocr_vehicle_license brain_antiporn brain_antiterror vis-classify_\\u6076\\u5fc3\\u56fe\\u8bc6\\u522b\\u670d\\u52a1 vis-ocr_plate_number brain_politician brain_imgquality_general brain_solution brain_ocr_plate_number brain_watermark brain_ocr_accurate brain_ocr_accurate_basic brain_ocr_receipt brain_ocr_business_license brain_solution_iocr brain_public brain_disgust brain_qrcode brain_ocr_handwriting brain_antispam_spam brain_ocr_passport brain_ocr_vat_invoice brain_numbers picchain_test_picchain_api_scope brain_ocr_business_card brain_ocr_train_ticket brain_ocr_taxi_receipt vis-ocr_household_register vis-ocr_vis-classify_birth_certificate vis-ocr_\\u53f0\\u6e7e\\u901a\\u884c\\u8bc1 vis-ocr_\\u6e2f\\u6fb3\\u901a\\u884c\\u8bc1 vis-ocr_\\u673a\\u52a8\\u8f66\\u68c0\\u9a8c\\u5408\\u683c\\u8bc1\\u8bc6\\u522b vis-ocr_\\u8f66\\u8f86vin\\u7801\\u8bc6\\u522b vis-ocr_\\u5b9a\\u989d\\u53d1\\u7968\\u8bc6\\u522b vis-ocr_\\u4fdd\\u5355\\u8bc6\\u522b brain_ocr_vin brain_ocr_quota_invoice brain_ocr_birth_certificate brain_ocr_household_register brain_ocr_HK_Macau_pass brain_ocr_taiwan_pass brain_ocr_vehicle_certificate brain_ocr_insurance_doc wise_adapt lebo_resource_base lightservice_public hetu_basic lightcms_map_poi kaidian_kaidian ApsMisTest_Test\\u6743\\u9650 vis-classify_flower lpq_\\u5f00\\u653e cop_helloScope ApsMis_fangdi_permission smartapp_snsapi_base iop_autocar oauth_tp_app smartapp_smart_game_openapi oauth_sessionkey smartapp_swanid_verify smartapp_opensource_openapi smartapp_opensource_recapi fake_face_detect_\\u5f00\\u653eScope vis-ocr_\\u865a\\u62df\\u4eba\\u7269\\u52a9\\u7406 idl-video_\\u865a\\u62df\\u4eba\\u7269\\u52a9\\u7406","session_secret":"c714e044adb914211218983681008341"}\n'
```
#### · 文本审核代码示例
#### · 输入
```
def check_content():
    request_url = 'https://aip.baidubce.com/rest/2.0/antispam/v2/spam?access_token=【】'
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

#### · 输出
```
{
    "log_id": 123456789,
    "conclusion": "不合规",
    "conclusionType": 2,
    "data": [{
        "type": 11,
        "subType": 0,
        "conclusion": "不合规",
        "conclusionType": 2,
        "msg": "存在百度官方默认违禁词库不合规",
        "hits": [{
            "datasetName": "百度默认黑词库",
            "words": ["免费翻墙"]
        }]
    }, {
        "type": 12,
        "subType": 2,
        "conclusion": "不合规",
        "conclusionType": 2,
        "msg": "存在文本色情不合规",
        "hits": [{
            "datasetName": "百度默认文本反作弊库",
            "probability": 1.0,
            "words": ["电话 找小姐"]
        }]
    }, {
        "type": 12,
        "subType": 3,
        "conclusion": "不合规",
        "conclusionType": 2,
        "msg": "存在政治敏感不合规",
        "hits": [{
            "probability": 1.0,
            "datasetName": "百度默认文本反作弊库",
            "words": ["敏感人物A"]
        }]
    }, {
        "type": 12,
        "subType": 4,
        "conclusion": "不合规",
        "conclusionType": 2,
        "msg": "存在恶意推广不合规",
        "hits": [{
            "probability": 1.0,
            "datasetName": "百度默认文本反作弊库",
            "words": [""]
        }]
    }, {
        "type": 13,
        "subType": 0,
        "conclusion": "不合规",
        "conclusionType": 2,
        "msg": "存在自定义文本黑名单不合规",
        "hits": [{
            "datasetName": "SLK-测试-自定义黑名单",
            "words": ["我是你爹", "他妈的"]
        }]
    }]
}
```

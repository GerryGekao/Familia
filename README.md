# Familia

Familia 开源项目包含文档主题推断工具、语义匹配计算工具以及基于工业级语料训练的三种主题模型（LDA、SentenceLDA、Topical Word Embedding)。 支持用户以“拿来即用”的方式进行文本分类、文本聚类、个性化推荐等任务的调研和落地。考虑到主题模型训练成本较大的问题，我们会陆续开放基于工业级语料训练的多个领域的主题模型，助力主题模型技术在垂直领域的应用和学术界的科学研究。

# 代码编译
第三方依赖包括gflags-2.0，glogs-0.3.3，protobuf-2.5.0, 同时要求编译器支持C++11, g++ >= 4.8 
默认情况下执行以下脚本会自动获取依赖并安装。
    
    sh build.sh # 包含了获取并安装第三方依赖的过程

# 模型下载

    cd model
    sh download_model.sh

# 运行DEMO
## 文档主题推断
    
    sh run_inference_demo.sh # 运行文档主题推断的demo
    
执行程序后，通过标准流方式输入文档，每行为一个文档，程序会返回每个文档的主题分布。如下所示

    请输入需要推断主题分布的文档:
    百度又一次展示了自动驾驶领域领导者的大气风范，发布了一项名为“Apollo(阿波罗)”的新计划，向汽车行业及自动驾驶领域的合作伙伴提供一个开放、完整、安全的软件平台，帮助他们结合车辆和硬件系统，快速搭建一套属于自己的完整的自动驾驶系统。
    
    文档主题分布:
    9159:0.103704 4296:0.072840 7486:0.058025 1378:0.037037 1073:0.037037 2414:0.037037 3935:0.034568 5921:0.032099 7380:0.032099 8643:0.032099 4757:0.030864 6808:0.025926 7185:0.022222 4091:0.019753 1167:0.017284 8843:0.016049 5292:0.014815 2507:0.014815 9914:0.013580 2520:0.011111 7658:0.011111 249:0.011111 2017:0.009877 2995:0.008642 4021:0.008642 7163:0.008642 9336:0.007407 1438:0.007407 136:0.007407 7095:0.007407 2313:0.007407 4309:0.007407 1314:0.006173 3573:0.006173 9529:0.006173 477:0.004938 6446:0.004938 281:0.004938 4072:0.004938 9082:0.004938 847:0.004938 27:0.004938 5872:0.004938 2720:0.004938 1322:0.004938 8848:0.003704 7765:0.003704 7838:0.003704 7891:0.003704 7918:0.003704 1592:0.003704 7107:0.003704 1766:0.003704 1812:0.003704 6726:0.003704 6513:0.003704 5660:0.003704 8996:0.003704 1434:0.003704 3407:0.003704 2285:0.003704 500:0.003704 3615:0.003704 3766:0.003704 4704:0.002469 1449:0.002469 9599:0.002469 7779:0.002469 2565:0.002469 7425:0.002469 1665:0.002469 9473:0.002469 9395:0.002469 872:0.002469 8411:0.002469 8606:0.002469 4490:0.002469 8722:0.002469 386:0.002469 4817:0.002469 8826:0.002469 1219:0.002469 75:0.002469 8859:0.002469 7716:0.001235 9280:0.001235 1399:0.001235 9304:0.001235 1:0.001235 9536:0.001235 8099:0.001235 8266:0.001235 1175:0.001235 91:0.001235 5809:0.001235 3087:0.001235 3265:0.001235 3752:0.001235 3832:0.001235 3908:0.001235 2515:0.001235 1046:0.001235 804:0.001235 1953:0.001235 5263:0.001235 428:0.001235 5514:0.001235 5624:0.001235 7696:0.001235 5826:0.001235 5906:0.001235 6196:0.001235 6240:0.001235 6378:0.001235 1896:0.001235 6875:0.001235 6917:0.001235 244:0.001235 7469:0.001235 1516:0.001235 7488:0.001235


## 语义匹配计算

    sh run_semantic_matching_demo.sh # 运行语义匹配计算的demo

默认为计算短文本与长文本语义匹配模式，运行结果如下所示

    请输入短文本:
    百度宣布阿波罗计划 开放自动驾驶技术有望改变汽车产业
    请输入长文本:
    百度又一次展示了自动驾驶领域领导者的大气风范，发布了一项名为“Apollo(阿波罗)”的新计划，向汽车行业及自动驾驶领域的合作伙伴提供一个开放、完整、安全的软件平台，帮助他们结合车辆和硬件系统，快速搭建一套属于自己的完整的自动驾驶系统。
    LDA sim = 0.0133234    TWE sim = 0.128288

将脚本中的--mode参数修改为1，则为长文本语义相似度模式, 运行结果如下所示

    请输入文档1:
    在人工智能发展得最为系统化的硅谷，AI工程师们的薪水远高于其他领域的同行。随着人工智能概念的不断深入人心，人工智能的人才愈发的紧俏，时至今日，大学刚毕业的博士也能坐拥八九十万的年薪，与资深的硅谷工程师相媲美。
    请输入文档2:
    在国内，部分企业早已瞄准人才的短板，走在了业界的前面。百度是最早进行AI的人才培养布局的，他们同国内诸多高校开展合作，共建工程实验室，在数据开放和资源共享上进行各种合作。这种方式类似美国在人工智能教育领域推行的“硅谷-斯坦福”校企联动模式，一方面斯坦福大学为硅谷提供了人才和科研成果，另一方面硅谷为斯坦福大学提供资金支持和大数据，以助力他们的科研能有更大的突破。
    Jensen Shannon Divergence = 1.13397    
    Hellinger Distance = 0.889616

## 模型内容展现
### 邻近词查询

    sh run_word_distance_demo.sh # 运行邻近词查询的demo

执行程序后，通过标准流方式输入词，每行为一个词，程序会返回每个词的最邻近的K个词。如下所示

    请输入词语:      篮球
    Word           Cosine distance
    ------------------------------
    足球              0.903682
    网球              0.842661
    羽毛球            0.836915
    足球比赛          0.809366
    五人制足球        0.799211
    美式足球          0.791207
    中国足球          0.788995
    乒乓球            0.788278
    五人制            0.784913
    足球新闻          0.783203

其中，每一行为一个词，数字表示该词与输入词的cosine距离，按照从大到小的顺序排序。可通过更改脚本中--work_dir和--conf_file的配置选择其他模型，--top_k配置展现词的个数，如

    --work_dir="./model/news/" --conf_file="lda.conf" --top_k=10 # 选用新闻LDA主题模型,展现距离最近的前10个词
    --work_dir="./model/news/" --conf_file="slda.conf" --top_k=20 # 选用新闻SentenceLDA主题模型,展现距离最近的前20个词

### 主题词查询
在TWE模型中，通过计算主题向量与词向量的cosine相似度可以衡量主题与每个词的相关性，可以每个主题下最邻近的K个词。同理，在LDA模型中，也可以得到每个主题下每个词的产生概率。主题词查询demo展示这两个模型的主题词结果。

    sh run_topic_word_demo.sh # 运行主题词查询的demo

执行程序后，通过标准流方式输入主题id，每行为一个id，程序会返回每个主题在TWE跟主题模型下最邻近的K个词的结果。如下所示

    请输入主题编号(0-10000):    105
    TWE result            LDA result
    ----------------------------------
    卫生检疫              国家
    检验检疫              出入境
    上海口岸              外籍
    外经贸部              检验检疫
    正式批准              检验检疫局
    认监委                国外
    卫生注册证书          互认
    检验检疫局            要闻
    资格认可              奖励旅游
    许可制度              公布

其中，每一行为有两次词，第一个词为TWE召回结果，第二个词为主题模型召回结果，按照相关性从大到小的顺序排序。
可通过更改脚本中--work_dir和--emb_file的配置选择其他TWE模型，--topic_words_file配置主题模型的主题结果，如

    --work_dir="./model/news/" --emb_file="news_twe_lda.model" --topic_words_file="topic_words.lda.txt" # 选用新闻LDA主题模型训练得到TWE模型以及对应的主题展现结果

# 注意事项
*   若出现找不到libglog.so, libgflags.so等动态库错误，请添加third_party至环境变量的LD_LIBRARY_PATH中。

    export LD_LIBRARY_PATH=./third_party/lib:$LD_LIBRARY_PATH

* 代码中内置简易的FMM分词工具，只针对主题模型中出现的词表进行正向匹配。该工具仅用于Demo示例使用，若对分词和语义准确度有更高要求，建议使用其他开源或者商用分词工具, 并使用自定义词表的功能导入主题模型中的词表。


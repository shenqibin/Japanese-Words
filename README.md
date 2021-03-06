# 日语单词整理

## Motivation
在学习日语的过程中，背单词是一个绕不去的砍。

对于不同的语言，单词的特点也不相同。对日语而言，有以下几个特点：
- 汉字可以通过音读记忆
- 同一个汉字可能对应不同的音读
- 同一个音读可能对应不同的汉字

在我背单词的过程中，发现一个很有趣也很普遍的问题，在经过一段时间的
记忆后，看到汉字我可以回忆起假名，不用太费功夫。但是当我尝试看假名去回忆汉字时，却屡屡受挫。

>通过看假名回忆汉字，是为了训练听力，因为你在听听力时，只能听到假名

## Target
为了达到我们的目的，看到假名就能回忆起对应的日文和中文意思，首先需要进行分类。

我认为分类记忆会强化记忆，所以我会把不同的假名发音分类，在该类别下是该发音对应的假名和组词。
以下是一个例子：

| 假名 | 日语 |组词 |
|----- | ----- | ---- |
| こう | 高  | 高校 |
|      | 候 | 天候 |
|      | 効 | 効果 |
|      | 幸 | 幸運 |
|      | 講 | 講演 |
## RoadMap
### 1. Read Excel
使用`pandas`的表格处理功能，我们可以读取excel中的行列，并将读取所有的单词的
- 假名
- 日文
- 汉字意思

所以`get_words_list.py`的输出为一个`word_list`.

>技术细节：每个词条用`Dict`表示，分别为{'假名':, '日文':, '意思':}，所有词条装在一个`list`里

### 2. 分类
构建一个词汇表类，类的数据成员为希望得到的各个类别，初始化为空。  
例如：
`self.kou = {'こう': []} # こう} `  ，每个数据成员都是一个`Dict`，其中`key`为字段，`value`为包含该字段的词汇的列表。

该词条表类有一个`classify`函数，输入为一个`word_list`，该函数遍历所有词条，假如该词条包含某个字段，则对应的数据成员添加该词条。

### 3. 生成Dataframe
得到每个字段所包含的词条后，需要整合。  
创建一个`pandas dataframe`，如以下形式:

|假名|日文|意思|类型|
|---|---|---|---|
|こう|||
|こうそう|高層|高层|名词|
|...|||
||||
|せい|||
|せいぞう|製造|制造，生产|名词|
|...|||

>排除专有名词

### 4. 输出到excel
将`dataframe`输出到excel文件。

### 5. 样品
我已经处理了生成的excel的文件，进行了校对和字体调整，并生成了PDF文件，可以在example里找到。

如果您有好的修改意见，或者发现了一些bug，欢迎提issue！  
如果您有解决办法，也欢迎fork并pull!  

最後の最後に, 如果该项目对您有帮助，欢迎分享并star!  
ありがとうございます!


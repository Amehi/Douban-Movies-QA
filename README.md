# Douban-Movies-QA

This is the repo for CSC6052 Final Project

## Baseline
- 豆瓣爬虫获取电影列表
- 豆瓣爬虫获取每部电影的长短评
- 问题池的构建
- LLM数据清洗/评论重写
- 问题生成

## Motivation
- 当前LLM生成的回答都十分客观，显得冰冷且机械化，表达方式与真人相差甚远。我们希望构建起能让模型“说人话”的数据库，使其在表达上更加主观，更具有人的情感色彩。
  

## Data Cleaning
定义好prompt，输入到LLM中，对数据集的内容做评判以及重写

重写的标准：
- 带有歧视内容的评论
- 带有侮辱性词汇的评论
- 带有观影或者评分日期
- 包含个人隐私信息或其他敏感信息


## Datasets
- id: 电影评论的id号
- film: 电影的名字
- question: 在构建questions时，我们首先列出几种基本问题，以及对应电影种类的问题，再用LLM重写这几个问题，丰富问题的种类。这些LLM生成的问题和预先定义好的问题将共同组成问题池，作为数据集的question部分
- answer: 经过Data Cleaning的电影评论，包括长评短评
- rating: 指这一评论对当前电影(film)的打分. range：rating ∈{0,1,2,3,4,5}
- vote: 指这一电影评论（answer）的点赞数 range：vote≥0

## Highlight & Contribution
- 相较之前的数据库，包含了长评
- 我们在生成问题时，既有分类，又节约了成本，给未来的数据库生成方法提供了参考
- 我们使用LLM对不符合规范的影评做了refine，避免bias，negative expression

## Result
- 由于经费，算力等资源不足，我们仅提供大小为5000的demo dataset，该数据库经通过完整数据清洗，问题生成等流程构建。
- 你可以在 `\data\douban_dataset.jsonl` 找到该数据库
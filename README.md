tail-rec-optimization
=====================

Scheme实现的对Scheme代码的尾递归判断和尾递归优化

* I'm DOING! (目前有一个简单的尾递归识别的Scheme实现,而且还没有做充分测试,只对正常情况简单试过,尾递归优化部分还没写)

* 运行环境: Racket 6.0, # lang racket on Mac 10.9.2 x64

* 这是对我的博客文章[浅谈尾递归的定义和判定方法](http://zoowii.com/blog/view/e327f3d4-66b9-4945-bd9e-5a3b1038db70) 和 [通用尾递归优化算法（包括自我尾递归和A->B, B->C, C->A的复杂尾递归的优化）](http://zoowii.com/blog/view/546971ee-e95f-4dbb-9853-99c4ed20d4c2)的代码实现实例。
* 本项目是使用Scheme语言实现的对Scheme代码的尾递归判断和尾递归优化的实现，采用的Scheme实现是Racket。

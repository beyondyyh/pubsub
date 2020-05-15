# 发布订阅模型

发布订阅（publish-and-subscribe）模型通常被简写为pub/sub模型。在这个模型中，消息生产者成为发布者（publisher），而消息消费者则成为订阅者（subscriber），生产者和消费者是M:N的关系。在传统生产者和消费者模型中，是将消息发送到一个队列中，而发布订阅模型则是将消息发布给一个主题。

## 构建发布者对象

> `func NewPublisher(publishTimeout time.Duration, buffer int) *Publisher`

- publishTimeout: 发布超时时间
- buffer: 缓冲队列长度

## 添加订阅者，订阅全部主题

> `func (p *Publisher) Subscribe() chan interface{}`

## 添加订阅者，订阅过滤后的主题

> `func (p *Publisher) SubscribeTopic(topic topicFunc) chan interface{}`

- topic: 主题过滤规则

## 发布主题

> `func (p *Publisher) Publish(v interface{})`

## 退出订阅

> `func (p *Publisher) Evict(sub chan interface{})`

## 关闭发布者，同时所有的订阅管道

> `func (p *Publisher) Close()`

## 发送主题

> `func (p *Publisher) sendTopic(sub subscriber, topic topicFunc, v interface{}, wg *sync.WaitGroup)`

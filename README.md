# ip2region for hyperf

本库基于 [ip2region](https://github.com/lionsoul2014/ip2region) ，适配Hyperf，可通过注解来使用。

[ip2region](https://github.com/lionsoul2014/ip2region) - 最自由的ip地址查询库，ip到地区的映射库，提供Binary,B树和纯内存三种查询算法，妈妈再也不用担心我的ip地址定位。

## 99.9%准确率，定时更新

数据聚合了一些知名ip到地名查询提供商的数据，这些是他们官方的的准确率，经测试着实比纯真啥的准确多了。<br />
每次聚合一下数据需要1-2天，会不定时更新。

## 标准化的数据格式

每条ip数据段都固定了格式：_城市Id|国家|区域|省份|城市|ISP_

只有中国的数据精确到了城市，其他国家只能定位到国家，后前的选项全部是0，已经包含了全部你能查到的大大小小的国家。
（请忽略前面的城市Id，个人项目需求）

## 体积小

数据库文件是ip2region.db

## 安装组件
>composer require firstphp/ip2region

## 使用范例
```php
use Hyperf\Di\Annotation\Inject;

......

/**
 * @Inject()
 * @var \Firstphp\Ip2region\Ip2region
 */
protected $ip2region;

......

$res = $this->ip2region->binarySearch($ip);

var_dump($res);


// Array
// (
//     [city_id] => 1132
//     [region] => 中国|0|浙江省|杭州市|移动
// )

```


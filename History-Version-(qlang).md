We renamed all tags:

```
git tag v0.1.2 v1.2.0
git tag v0.2.0 v2.0.01
git tag v0.2.1 v2.1.00
git tag v0.2.20 v2.2.00
git tag v0.2.21 v2.2.01
git tag v0.2.3 v2.3.00
git tag v0.2.4 v2.4.00
git tag v0.2.5 v2.5.00
git tag v0.2.6 v2.6.00
git tag v0.2.70 v2.7.00
git tag v0.2.71 v2.7.10
git tag v0.2.72 v2.7.20
git tag v0.2.80 v2.8.00
git tag v0.2.81 v2.8.10
git tag v0.2.82 v2.8.20
git tag v0.2.90 v2.9.00
git tag v0.2.91 v2.9.10
git tag v0.2.92 v2.9.20
git tag v0.2.93 v2.9.30
git tag v0.2.95 v2.9.50
git tag v0.2.96 v2.9.60
git tag v0.3.0 v3.0.00
git tag v0.3.1 v3.1.00
git tag v0.3.2 v3.2.00
git tag v0.3.3 v3.3.00
git tag v0.3.5 v3.5.00
git tag v0.4.1 v4.1.0
git tag v0.5.00 v5.0.0
git tag v0.5.01 v5.0.1
git tag v0.5.1 v5.1.0
git tag v0.5.2 v1.5.0 (v5.1.1)
git tag v0.6.01 v6-alpha-0.1
git tag v0.6.02 v6-alpha-0.2
git tag v0.6.03 v6-alpha-0.3
git tag v0.6.10 v6-alpha-1.0
```

也就是说，对于 goplus 来说，历史的 qlang 的 release 信息仍然被保留，但是实际上已经是不能正常 work 了的。如果您的项目基于 qlang 老版本，可以移步到：

* https://github.com/xushiwei/qlang/releases

老版本的 qlang 少量维护工作，会在 https://github.com/xushiwei/qlang 进行。

迁移样例 (https://github.com/qiniu/bpl 基于 qlang v1.2.x 版本)：

* https://github.com/qiniu/bpl/tree/v1.1.4

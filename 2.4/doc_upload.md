#个人/企业上传申请材料

## 描述
[企贷产品配置](04_cp_fac_config.md)或[个贷产品配置](01_cs_fac_config.md)，需要按照接口的返回“doc”结果，组织上传申请材料需要的压缩包文件（见[申请材料压缩包结构](#申请材料压缩包结构)），然后上传申请材料。

## 示例代码
具体上传方法详见<a href="https://codeload.github.com/lianjintai/openapi-demo-java/zip/master" target="_blank">接口demo下载</a>申请材料上传demo,包路径[com.ljt.openapi.demo.demos.CreditMaterialUploadDemo.java]。

### 申请材料压缩包结构
文件名：文件名.zip

压缩包内容：
```
文件名.zip
├── {refId} \
│    ├── {mtDocCd} \
│    │      └── {文件1}
│    └── {mtDocCd} \
│           ├── {文件2}
│           └── {文件3}
└── {refId} \
     └── {mtDocCd} \
            └── {文件4}
```
## FAQ
1. refId有多少个<br>
同一个产品，最多有两个refId
2. 不同的mtDocTypeCd值的Json对象中的refId意义<br>
mtDocTypeCd=CIF，客户申请材料，<br>
mtDocTypeCd=FAC：业务申请材料

3. refId的作用<br>
对上传的文件进行归类处理，再创建申请的时候，需要传入你上传的申请材料使用的refId，服务端将根据refId关联已上传的申请材料文件
4. refId创建申请的时候使用方式
不同的申请材料门类，使用的refId不同。在授信申请的时候需要<br>将mtDocTypeCd=CIF的refId放入"doc.cifDocRefId"值中,<br>将mtDocTypeCd=FAC的refId放入"doc.facDocRefId"值中
5. 上传压缩包中mtDocCd值怎么取值<br>
使用mtDocTypeCd判断,<br>
mtDocTypeCd=CIF,将mtDocCd放入对应的refId中<br>
mtDocTypeCd=FAC,将mtDocCd放入对应的refId中
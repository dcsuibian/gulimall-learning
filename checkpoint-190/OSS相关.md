开通OSS功能，详见P61



设置bucket为能跨域访问的，详见P64



由于我不方便上传我的OSS相关配置内容，因此需要你在你的电脑上设置如下的环境变量：

![image-20231024055649069](./assets/image-20231024055649069.png)

| 环境变量名                   |
| ---------------------------- |
| ALIYUN_OSS_ACCESS_KEY_ID     |
| ALIYUN_OSS_ACCESS_KEY_SECRET |
| ALIYUN_OSS_BUCKET_NAME       |
| ALIYUN_OSS_ENDPOINT          |



另外，需要你在前端代码中用vscode检索并替换掉如下内容：

```
gulimall-dcsuibian.oss-cn-hangzhou.aliyuncs.com
```



数据库中的图片地址也要替换掉：

```sql
SET @url='你的OSS的bucket.endpoint';
SET @old_url='gulimall-dcsuibian.oss-cn-hangzhou.aliyuncs.com';
USE `gulimall_oms`;
UPDATE `oms_order` SET `note`=REPLACE(`note`,@old_url,@url);
UPDATE `oms_order_item` SET `spu_pic`=REPLACE(`spu_pic`,@old_url,@url);
UPDATE `oms_order_item` SET `sku_pic`=REPLACE(`sku_pic`,@old_url,@url);
UPDATE `oms_order_item` SET `sku_attrs_vals`=REPLACE(`sku_attrs_vals`,@old_url,@url);
UPDATE `oms_order_operate_history` SET `note`=REPLACE(`note`,@old_url,@url);
UPDATE `oms_order_return_apply` SET `sku_img`=REPLACE(`sku_img`,@old_url,@url);
UPDATE `oms_order_return_apply` SET `sku_attrs_vals`=REPLACE(`sku_attrs_vals`,@old_url,@url);
UPDATE `oms_order_return_apply` SET `description述`=REPLACE(`description述`,@old_url,@url);
UPDATE `oms_order_return_apply` SET `desc_pics`=REPLACE(`desc_pics`,@old_url,@url);
UPDATE `oms_order_return_apply` SET `handle_note`=REPLACE(`handle_note`,@old_url,@url);
UPDATE `oms_order_return_apply` SET `receive_note`=REPLACE(`receive_note`,@old_url,@url);
UPDATE `oms_order_return_apply` SET `company_address`=REPLACE(`company_address`,@old_url,@url);
UPDATE `oms_payment_info` SET `callback_content`=REPLACE(`callback_content`,@old_url,@url);
UPDATE `oms_refund_info` SET `refund_content`=REPLACE(`refund_content`,@old_url,@url);
USE `gulimall_pms`;
UPDATE `pms_brand` SET `logo`=REPLACE(`logo`,@old_url,@url);
UPDATE `pms_sku_info` SET `sku_desc`=REPLACE(`sku_desc`,@old_url,@url);
UPDATE `pms_sku_info` SET `sku_subtitle`=REPLACE(`sku_subtitle`,@old_url,@url);
UPDATE `pms_spu_comment` SET `resources`=REPLACE(`resources`,@old_url,@url);
UPDATE `pms_spu_info` SET `spu_description`=REPLACE(`spu_description`,@old_url,@url);
USE `gulimall_sms`;
UPDATE `sms_coupon` SET `coupon_img`=REPLACE(`coupon_img`,@old_url,@url);
UPDATE `sms_home_adv` SET `pic`=REPLACE(`pic`,@old_url,@url);
UPDATE `sms_home_adv` SET `url`=REPLACE(`url`,@old_url,@url);
UPDATE `sms_home_adv` SET `note`=REPLACE(`note`,@old_url,@url);
UPDATE `sms_home_subject` SET `url`=REPLACE(`url`,@old_url,@url);
UPDATE `sms_home_subject` SET `img`=REPLACE(`img`,@old_url,@url);
USE `gulimall_ums`;
UPDATE `ums_member` SET `header`=REPLACE(`header`,@old_url,@url);
UPDATE `ums_member` SET `city`=REPLACE(`city`,@old_url,@url);
UPDATE `ums_member_collect_spu` SET `spu_name`=REPLACE(`spu_name`,@old_url,@url);
UPDATE `ums_member_collect_spu` SET `spu_img`=REPLACE(`spu_img`,@old_url,@url);
UPDATE `ums_member_collect_subject` SET `subject_img`=REPLACE(`subject_img`,@old_url,@url);
UPDATE `ums_member_collect_subject` SET `subject_urll`=REPLACE(`subject_urll`,@old_url,@url);
USE `gulimall_wms`;
UPDATE `wms_ware_order_task` SET `delivery_address`=REPLACE(`delivery_address`,@old_url,@url);
UPDATE `wms_ware_order_task` SET `task_comment`=REPLACE(`task_comment`,@old_url,@url);
```


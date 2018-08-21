# 使用方法

在其他模块中，定义你要索引的数据.

 ```

 /**
  * Implements hook_xunsearch_index().
  */
 function MODULE_xunsearch_index() {
   $data = entity_load_many('page', array(), array('orderby' => array('created' => 'DESC')));
   $data = json_decode(json_encode( $data),true);
   return $data;
 }

```

在其他模块目录下的config/install/xunsearch.index.yml，定义你要索引的数据源字段.

 ```

 xunsearch:
   fields:
     pid:
       type: id
     title:
       type: title
     content:
       type: body
     type:
       type: string
     image:
       type: string
     status:
       type: string
     created:
       type: date

```

然后你就可以任意地方使用如下调用方法.

 ```
xunsearch_update_index();
xunsearch_clean_index();
xunsearch_search($keywords);

 ```

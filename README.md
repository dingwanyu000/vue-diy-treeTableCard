# vue-diy-treeTableCard
a diy treeTableCard of element-ui

基于Vue自定义树形tableCard

API
-----------------------
|Param          | Description   | Type  |
| ------------- |:-------------:| -----:|
| item          | 循环数据结构   | Array |
| noLine        | 是否有链接符   |Boolean|

|event          | Description   | param |
| ------------- |:-------------:| -----:|
|listenToChildPlus | 组件展开回掉事件   | |
|listenToChildMinus| 组件收缩回掉事件   | data |

Data
------------------------
data: [
        {
          id: 1,
          name: "综合采集",
          span: 24,
          array: [
            {
              fileNum: 1,
              recordNum: "123",
              goTo: "123",
              outFileNum: 2,
              outRecordNum: 3
            }
          ],
          children: [
            {
              id: 2,
              name: "预处理",
              array: [
                {
                  fileNum: 1,
                  recordNum: "123",
                  goTo: "123",
                  outFileNum: 2,
                  outRecordNum: 3
                }
              ],
              children: [
                {
                  id: 3,
                  name: "云合并拆分",
                  array: [
                    {
                      fileNum: 1,
                      recordNum: "123",
                      goTo: "123",
                      outFileNum: 2,
                      outRecordNum: 3
                    }
                  ],
                  children: [
                    {
                      id: 4,
                      name: "批价入库",
                      array: [
                        {
                          fileNum: 1,
                          recordNum: "123",
                          goTo: "123",
                          outFileNum: 2,
                          outRecordNum: 3
                        }
                      ],
                      children: [
                        {
                          id: 5,
                          name: "累账合并",
                          array: [
                            {
                              fileNum: 1,
                              recordNum: "123",
                              goTo: "123",
                              outFileNum: 2,
                              outRecordNum: 3
                            }
                          ],
                          children: [
                            {
                              id: 6,
                              name: "累账",
                              array: [
                                {
                                  fileNum: 1,
                                  recordNum: "123",
                                  goTo: "123",
                                  outFileNum: 2,
                                  outRecordNum: 3
                                }
                              ],
                              children: []
                            }
                          ]
                        },
                        {
                          id: 7,
                          name: "累账",
                          array: [
                            {
                              fileNum: 1,
                              recordNum: "123",
                              goTo: "123",
                              outFileNum: 2,
                              outRecordNum: 3
                            }
                          ],
                          children: []
                        }
                      ]
                    }
                  ]
                }
              ]
            }
          ]
        }
      ]

Usage
------------------------
![image](https://github.com/dingwanyu000/vue-diy-treeTableCard/blob/master/usage.png)

Demo Screenshot
------------------------
![image](https://github.com/dingwanyu000/vue-diy-treeTableCard/blob/master/diyCard.png)

License
------------------------
DWY

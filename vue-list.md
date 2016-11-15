### vue遍历列表的几种方式：

##### 最好的方式：
1. 特点：(v, k) in 的方式；保证schema和values里的属性必须一致；
2. 优点：适合很多数据的列表；标题栏亿控制，只要删除schema的一个属性，那么values里相对应的也不复存在；但是如果是单独删除values里属性或者即便有一条数据为空排版也不受任何影响；

    ```
    <template>
      <table id="demo" class="table">
        <thead>
          <tr>
            <th v-for="v in orderList.schema">     /*v随便定义*/
              {{v}}
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="order in orderList.values">
            <td v-for="(v, k) in orderList.schema">{{order[k]}}</td>
          </tr>
        </tbody>
      </table>
    </template>
    ```

    ```
    <script type='text/babel'>
     export default {
        data(){
         return {
             orderList: {
                 schema: {
                     id: '#',
                     firstName: '名字',
                     lastName: '姓',
                     nickname: '用户名',
                     role: '角色'
                 },

                 values: [
                   {
                     id: '1',
                     firstName: '德希穆克',
                     lastName: 'PROHASKA',
                     nickname: '@Genelia',
                     role: '管理员'
                   },

                   {
                     id: '1',
                     firstName: '德希穆克',
                     lastName: 'PROHASKA',
                     nickname: '@Genelia',
                     role: '管理员'
                   }
                 ]
             }
         }
        }
      }
    </script>
    ```

##### 常用的的方式：
1. 特点：tbody里的数据分条展示；
2. 有点：对于数据字段清晰明了易理解；

    ```
    <template>
      <table id="demo" class="table">
        <thead>
          <tr>
            <th v-for="v in orderList.schema">
              {{v}}
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="order in orderList.values">
            <td>{{order.id}}</td>
            <td>{{order.firstName}}</td>
            <td>{{order.lastName}}</td>
            <td>{{order.nickname}}</td>
            <td>{{order.role}}</td>
          </tr>
        </tbody>
      </table>
    </template>
    ```

    ```
    <script></script>内容，同上，不变
    ```

##### 最易理解的方式：
1. 遍历一层套一层，哪里需要遍历，就给哪里加上v-for

    ```
    <template>
      <table id="demo" class="table">
        <thead>
          <tr>
            <th v-for="v in orderList.schema">
              {{v}}
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="order in orderList.values">
            <td v-for="v in order">
              {{v}}
            </td>
          </tr>
        </tbody>
      </table>
    </template>
    ```

```
<script></script>内容同第一个，不变
```

##### 可实现但不建议使用的的方式：
1. 弊端：数组结构通常是有key，有value，相对应

    ```
    <thead>
      <tr>
        <th v-for="v in orderList.schema">
          {{v}}
        </th>
      </tr>
    </thead>
    ```

    ```
    <script type='text/babel'>
     export default {
        data(){
         return {
             orderList: {
                 schema: ['#', '名字', '姓', '用户名', '角色'],
             }
         }
        }

      }
    ```

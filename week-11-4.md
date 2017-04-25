### 周报 16-11-4
##### Vue.js实践操作案例总结
1. 需求：点击“查看详情”后跳转到地图页

    ```
	//第一步：新建一个rodemap文件夹，包括index.vue和index.js，然后在route.js页仿照其他格式配置路由
    const RouterConfig = {
      "/basic": {
        title: "填写基本信息",
        name: "view:service.basic",
        component(resolve){
          require(["./../pages/RequirementBasic"], resolve)
        }
      },
      "/roadmap":{
        title:"小型会务办公流程",
        name:"view:roadmap",
        component(resolve){
          require(["../pages/Roadmap"],resolve)
        }
      },
      "/copy/:id": {
        title: "填写基本信息",
        name: "view:copy.service.basic",
        component(resolve){
          require(["./../pages/RequirementBasic"], resolve)
        }
      }
    };
    ```

    ```
	//第二步：加v-link跳转链接,引入路径
    <div v-link="{path:'/rodemap'}">查看详情</div>
    ```

    ```
	//第三步：在rodemap文件夹下的index页面输入地图页面内容
    ```
2. 想要弹出数字键盘，则在类型加上number

	` label="人均预算" name="budget" type="number"`

3. 入住时间默认填写开始时间

	`:start-time.sync="data.start_time"`

	```
    //定义在ready（）{}里
    dataFormat.start_time = this.requirement.start_time;
    ```

4. 默认设施是投影仪，3000-5000流明 

	```
	export default [
      { value: "320", text: "其他" },
      { value: "313", text: "投影仪" },
      { value: "327", text: "电子指示屏" },
      { value: "322", text: "背景板" },
      { value: "326", text: "横幅" }
    ]

    export const projector = [
      "酒店内投影仪3000流明以下",
      "酒店内投影仪3000-5000流明",
      "酒店内投影5000流明以上",
      "外带投影仪3000流明以下",
      "外带投影仪3000-5000流明",
      "外带投影仪5000流明以上"
    ];
	```

	`dataFormat.item_id = "313";     //313是投影仪的值`

    ```
    //写在methods里：
	onTypeChange(data, index){
        try {
          if (data.item_id !== this.requirement.utility_detail[index].item_id) data.note = data.item_id.value == 313 ? this.projector[1] : ''
        } catch (e) {
          data.note = data.item_id.value == 313 ? this.projector[1] : ''
        }
      }
    ```

5. 值不等于1或者不等于2时，用&&，而不是||，且（）代表有运算顺序

	`v-if="data.type && (data.type.value != 1 && data.type.value != 2)"`

6. 给当前页面的body加背景色

    ```
	<script>
      export default {
        created() {
          document.body.classList.add('bg--body')
        },

        destroyed() {
          document.body.classList.remove('bg--body');
        }
      }
    </script>
	```


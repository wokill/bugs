#### 1、Html代码
```
<script src="//unpkg.com/vue/dist/vue.js"></script>
<script src="//unpkg.com/iview/dist/iview.min.js"></script>
<div id="app">
    <row>
        <i-col span="12">
        <i-select
            v-model="model14"
            multiple
            filterable
            remote
            :remote-method="remoteMethod2"
            :loading="loading2">
            <i-option v-for="(option, index) in options2" :value="option.value" :key="index">{{option.label}}</i-option>
        </i-select>
       <button type="button" @click="delTest">测试代码删除多选值</button>
        </i-col>
    </row>
</div>
```
### 2、JS 代码
```

    var Main = {
        data () {
            return {
                model13: '',
                loading1: false,
                options1: [],
                model14: [],
                loading2: false,
                options2: [],
                list: ['Alabama', 'Alaska', 'Arizona', 'Arkansas', 'California', 'Colorado', 'Connecticut', 'Delaware', 'Florida', 'Georgia', 'Hawaii', 'Idaho', 'Illinois', 'Indiana', 'Iowa', 'Kansas', 'Kentucky', 'Louisiana', 'Maine', 'Maryland', 'Massachusetts', 'Michigan', 'Minnesota', 'Mississippi', 'Missouri', 'Montana', 'Nebraska', 'Nevada', 'New hampshire', 'New jersey', 'New mexico', 'New york', 'North carolina', 'North dakota', 'Ohio', 'Oklahoma', 'Oregon', 'Pennsylvania', 'Rhode island', 'South carolina', 'South dakota', 'Tennessee', 'Texas', 'Utah', 'Vermont', 'Virginia', 'Washington', 'West virginia', 'Wisconsin', 'Wyoming']
            }
        },
        methods: {
        	delTest(){
          	this.model14.splice(1,1)
          },
            remoteMethod1 (query) {
                if (query !== '') {
                    this.loading1 = true;
                    setTimeout(() => {
                        this.loading1 = false;
                        const list = this.list.map(item => {
                            return {
                                value: item,
                                label: item
                            };
                        });
                        this.options1 = list.filter(item => item.label.toLowerCase().indexOf(query.toLowerCase()) > -1);
                    }, 200);
                } else {
                    this.options1 = [];
                }
            },
            remoteMethod2 (query) {
                if (query !== '') {
                    this.loading2 = true;
                    setTimeout(() => {
                        this.loading2 = false;
                        const list = this.list.map(item => {
                            return {
                                value: item,
                                label: item
                            };
                        });
                        this.options2 = list.filter(item => item.label.toLowerCase().indexOf(query.toLowerCase()) > -1);
                    }, 200);
                } else {
                    this.options2 = [];
                }
            }
        }
    }

var Component = Vue.extend(Main)
new Component().$mount('#app')
```


### 测试步骤

** 1、首选在多选中选中两个以上的值

** 2、点击删除按钮

** 3、此时，下拉框中option当中的选择已经取消，但选中框的显示并未去除，而且此时手动删除该显示无效

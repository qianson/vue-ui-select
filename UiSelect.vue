<template>
  <div id="sel-wrapper">
      <div class="ui-wrapper">
        <input type="text" class="sel_input" :placeholder="defaultHolder" v-model="inputText">
        <div class="triangle-wrapper" @click="showSelDown">
           <span class="triangle"></span>
        </div>
         <ul class="sel-down-wrapper" v-if="listShow">
            <li v-for='(item,index) in selData' :key='index' @click='handleListClick(item,index)' :class="{active:index===activeItem}">{{item}}</li>
         </ul>
      </div>
  </div>
</template>
<script>
export default {
    name: 'UiSelect',
    data () {
        return {
            listShow: false, // select 下拉显示控制
            inputText: '', // 绑定输入值
            activeItem: null // 控制当前显示的下拉选项
        };
    },
    props: {
        defaultHolder: { // placeholder设置
            type: String,
            default: ''
        },
        selData: { // 下拉框数据
            type: Array,
            default () {
                return ['xiaohw', 'xiaoling'];
            }
        }
    },
    created () {
        console.log(this.defaultHolder);
    },
    methods: {
        showSelDown () {
            this.listShow = !this.listShow;
        },
        handleListClick (item, index) {
            this.inputText = item;
            this.listShow = !this.listShow;
            this.activeItem = index;
        }
    }
};
</script>
<style>
#sel-wrapper{
    display:inline-block;
}
    .ui-wrapper{
        width:200px;
        height:34px;
        border:1px solid #E7EAEC;
        position: relative;

    }
    .ui-wrapper .sel_input{
        padding-left:12px;
        height:100%;
        width:85%;
        box-sizing: border-box;
    }
    .ui-wrapper .triangle-wrapper{
        width:15%;
        position:relative;
        float:right;
        height:100%;
    }
    .triangle{
        border: 4px solid transparent;
        border-top: 6px solid #666;
        width: 0;
        height: 0px;
        position: absolute;
        right:50%;
        top:50%;
        margin-right:-3px;
        margin-top:-3px;
        }
    .sel-down-wrapper{
        width:100%;
        border:1px solid #E7EAEC;
        position: absolute;
        left:-1px;
        top:100%;
        margin-top:5px;
        background:#fff;
        z-index: 999;
    }
    .sel-down-wrapper li{
        padding:10px 0 10px 10px;
    }
   .sel-down-wrapper .active{
       background:#1AB394;
       color:#fff;
    }
</style>

<template>
    <div class="">
        <section>
            <input type="file" accept="application/json" @change="readLocalFile1($event)" value="读取钱包文件"/>
            <el-button type="primary" @click="saveStorage">保存到storage</el-button>
            <el-button type="primary" @click="save">备份到本地</el-button>
            <pre>{{json}}</pre>
            <a :href="href" download="json" id="a">链接</a>
        </section>
    </div>
</template>

<script>
    //import  from ''

    export default {
        //组件名
        name: 'index',
        //实例的数据对象
        data() {
            return {
                textarea:"",
                json:'',
                href:''
            }
        },
        //数组或对象，用于接收来自父组件的数据
        props: {

        },
        //计算
        computed: {

        },
        //方法
        methods: {
            readLocalFile1(e){
                console.log("e",e);
                var localFile = e.target.files[0];
                console.log(localFile);
                var content,
                    reader = new FileReader();;
                reader.onload = (event)=> {
                    content = event.target.result;
                    console.log(content)
                    this.json=content;
                }
                reader.onerror = function(event) {
                alert('error')

                }

                content = reader.readAsText(localFile,"UTF-8");
                console.log('read',content)
            },
            saveStorage(){
                console.log(this.json)
                localStorage.json=this.json;
                console.log("storage",localStorage.json)
            },
            save(){
                this.href=localStorage.json;
                console.log("href",this.href);

                var bb = new Blob([this.href],{type : 'application/json'});
                console.log('bb',bb);
                var jsonURL=window.URL.createObjectURL(bb);
                console.log(jsonURL)
                this.href=jsonURL;
                let a=document.getElementById('a');
                console.log(a)
                setTimeout(function() {
                    a.click()
                }, 50);
            }
        },
        //生命周期函数
        created() {

        },
        beforeMount() {

        },
        mounted() {

        },
        //监视
        watch: {

        },
        //组件
        components: {

        },
        //过滤器
        filters:{

        },
        //自定义指令
        directive:{

        }
    }
</script>

<!--
	作者：liangyanxiangde@163.com
	时间：2017-03-27
	描述：统一使用less,局部样式
-->
<style lang="less" scoped>

</style>
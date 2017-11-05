<template>
    <div class="">
        <section>
            <input type="file" id="uploadFile" @onchange="readLocalFile($event)"/>
            <div><img src="" id="img"/></div>

            <div><textarea id="fileContent" rows="30" cols="60"></textarea></div>
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
            readLocalFile(e){
                console.log(e);
                var localFile = document.getElementById("uploadFile").files[0];

                var reader = new FileReader();
                //Uncaught SyntaxError:Unexpected identifier
                var content;
                reader.onload = function(event) {
                    content = event.target.result;
                    //alert(content);

                    document.getElementById("img").src = content;
                    document.getElementById("fileContent").value = content;
                }
                reader.onerror = function(event) {
                alert('error')
                    //alert("File could not be read! Code " + event.target.error.code);
                }
                //reader.readAsText(localFile,"UTF-8");

        content = reader.readAsDataURL(localFile,"UTF-8");
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
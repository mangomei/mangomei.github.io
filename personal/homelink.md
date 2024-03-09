<!-- 引入 layui.css -->
<link href="//unpkg.com/layui@2.7.6/dist/css/layui.css" rel="stylesheet">


<div class="layui-row">
    <div class="layui-col-md12">
        <div id="container">
            <fieldset class="layui-elem-field">
                <legend>就算没有什么事，也要常和家人聊聊天</legend>
                <div class="layui-field-box">
                    <ul class="layui-timeline">
                        <li class="layui-timeline-item" v-for="(node,index) in nodes" :key="index">
                            <i class="layui-icon layui-timeline-axis">&#xe63f;</i>
                            <div class="layui-timeline-content layui-text">
                            <div class="layui-timeline-title">{{node.year}}</div>
                            <p v-for="remark in node.remarks">
                                {{remark}}
                            </p>
                            </div>
                        </li>
                    </ul>
                </div>
            </fieldset>
        </div>
    </div>
</div>


<script>
    (function(){
         new Vue({
            el:'#container',
            data() {
                return {
                    nodes: [
                        {
                            year: '2023年3月12',
                            remarks: [
                                "这次23年第二次家庭聊天",
                                "先是和爸爸翠姐聊了很多关于二月花朝节的事情，爸爸说没什么意思不好玩。",
                                "再和翠姐，聊了我可以去香港帮她们代购东西，说是让带动我们的朋友圈"
                            ]
                        },
                        {
                            year: '2023年2月18',
                            remarks: [
                                "过年回来深圳后，和翠姐爸爸聊天",
                                "聊了很多家常，关于爸爸的工作身体，还有翠姐的工作等"
                            ]
                        }
                    ]
                };
            }
        });
    })();
</script>
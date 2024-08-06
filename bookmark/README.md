<!-- 引入 layui.css -->
<link href="https://cdn.jsdelivr.net/npm/layui@2.7.6/dist/css/layui.css" rel="stylesheet">

<style type="text/css">
.layui-row{
    display: flex;
    flex-flow: row wrap;
    align-content: space-between;
}
.layui-row a:hover{
    text-decoration:underline;
}
.layui-row div{
    border:1px solid #ddd;
    height:40px;
    display: flex;
    flex-flow: row wrap;
    align-content: center;
    justify-content: center;
    margin-bottom: 5px;
    margin-right: 5px;
    border-radius: 2px;
    font-size: 12px;
}

.layui-row .no {
    background-color: white;
    color: black;
}
.nav{
    position: fixed;
    top: 20%;
    width: 140px;
    right: 20px;
    z-index: 999;
    background: #eee;
    padding: 10px;
}
.nav a{
    display: block;
    padding: 2px;
}
.stat{
    height:30px;
    line-height:30px;
    color: gray;
    text-align: right;
}
</style>

<div id="container" >
    <div class="stat">共{{nodes.length}}个分区，{{linkCount}}条链接！</div>
    <div class="nav">
        <a v-for="(item,index) in nodes" :href="aHref(item)">{{index+1}}.{{item.moduleName}}</a>
    </div>
    <fieldset class="layui-elem-field" style="padding: 8px;" v-for="(item,index) in nodes">
        <a :id="item.moduleId" style="position: relative;top:-50px;"></a>
        <legend>{{index+1}}.{{item.moduleName}}</legend>
        <div class="layui-row">
            <div class="layui-col-xs12 layui-col-sm12 layui-col-md2 no" v-for="(part,index) in item.parts">
                <a :href="theHref(part)" target="_blank">{{theName(part)}}</a>
            </div>
    </fieldset>
</div>

<script>
    (function(){
         new Vue({
            el:'#container',
            data() {
                return {
                    nodes: [
                        {
                            moduleId: 'my-project',
                            moduleName: '我的项目',
                            parts:[
                                    '项目资源分布@https://mg.meiflower.top/personal/project',
                                    '我的项目@https://gitee.com/mgang/my-project',
                                    '猫大刚主页@https://mg.meiflower.top/',
                                    '我的计划@https://mg.meiflower.top/plan/',
                                    '我的B站空间@https://space.bilibili.com/1174515315',
                                    '我的博客@https://mg.meiflower.top/mb/',
                                    'marp分享@http://marp.meiflower.top/',
                                    '待办列表@http://todo.meiflower.top/',
                                    'mango-kit@https://github.com/mg0324/mango-kit',
                                    '妙娃miaowa@https://mmtdd.gitee.io/miaowa/#/',
                                    'B站工具bup@https://gitee.com/mgang/my-project/tree/master/bup',
                                    'jmedis@https://gitee.com/mangoorg/jmedis',
                                    'idea启动插件@https://gitee.com/mgang/idea-plugin-start-time',
                                    '我的分享@https://gitee.com/mgang/my-share',
                                    'leetcode刷题笔记@https://gitee.com/mgang/leet-code',
                                    '我的日历打卡@https://mg.meiflower.top/calendar/m2/2023/index.html',
                                    'B站web直播入口@https://live.bilibili.com/p/html/web-hime/index.html?visit_id=287t35tjj1us',
                                    
                            ]
                        },
                        {
                            moduleId: 'mango-card',
                            moduleName: '芒果卡片',
                            use: false,
                            parts:[
                                    '芒果网盘@http://disk.meiflower.top/',
                                    '芒果卡片@https://mg.meiflower.top/card-admin/#/login',
                                    '芒果卡片构建@http://mg.meiflower.top/cp/bqr/',
                                    '点子队列@http://mg.meiflower.top/cp/keyqueue',
                                    '卡片预览@http://mg.meiflower.top/cardview/index.html?id=5f3245cc14434434810bece36ea97125'
                            ]
                        },
                        {
                            moduleId: 'about-note',
                            moduleName: '笔记相关',
                            parts:[
                                    'mangodoc@https://mangodoc.meiflower.top',
                                    'mangodoc-template@https://mangodoc-template.meiflower.top',
                                    'docsify-template@http://docsify-template.meiflower.top/#/',
                                    'docsify-note@http://docsify-note.meiflower.top/#/',
                                    '大刚学算法@https://alg.meiflower.top/#/',
                                    '大刚学设计模式@https://dp.meiflower.top/#/',
                                    'Java学习体系文档@https://java.meiflower.top/#/',
                                    '走上架构之路@https://arch.meiflower.top/#/',
                                    'CPU修行文档@http://mgang.gitee.io/s-cpu/#/'
                                    
                            ]
                        },
                        {
                            moduleId: 'offen-tool',
                            moduleName: '常用工具',
                            parts:[
                                'chrome商店@https://chrome.google.com/webstore/category/extensions',
                                '定稿设计@https://gd74865930.qiye.gaoding.com/smartdesign',
                                '百度统计@https://tongji.baidu.com/main/homepage/22511391/homepage/index',
                                '图片转base64@https://kz16.top/png2base64.html',
                                '谷歌翻译@https://translate.google.com.hk/?hl=zh-CN&sourceid=cnhp',
                                'processon@https://www.processon.com/login',
                                'drawio@https://app.diagrams.net/',
                                '华为云容器服务@https://console.huaweicloud.com/swr/?agencyId=9fb50aa2b84e4d9f820bb6d32ca2b5ab&region=cn-south-1&locale=zh-cn#/swr/warehouse/detail/hw_008618613073290_01/mangoorg/flask-api/guide',
                                'doocs md@https://doocs.gitee.io/md/',
                                'mvnrepository@https://mvnrepository.com/',
                                'favicon@https://favicon.io/',
                                'logo生成@https://www.logosc.cn/make',
                                'boss招聘@https://www.zhipin.com/shenzhen/',
                                '图片压缩@https://tinypng.com/',
                                '即时设计@https://js.design/workspace',
                                '可画设计@https://www.canva.cn/',
                                '可画视频编辑@https://www.canva.cn/design/DAFz6qoiO6Y/6Avs1vl-RckbASeqI9gn1g/edit'
                            ]
                        },
                        {
                            moduleId: 'offen-email',
                            moduleName: '常用邮箱',
                            parts:[
                                'QQ邮箱@https://mail.qq.com/cgi-bin/frame_html?sid=05f9Ec9lbnidJGUG&r=f6adff210c8f5793ce3d74cfcaa93fde&lang=zh',
                                '163邮箱@https://mail.163.com/',
                                'icloud邮箱@https://www.icloud.com.cn/mail/',
                                'iconfont@https://www.iconfont.cn/manage/index?manage_type=myprojects&projectId=4036078'
                            ]
                        },
                        {
                            moduleId: 'about-domain',
                            moduleName: '域名相关',
                            parts:[
                                'Free DNS@https://dns.he.net/index.cgi',
                                'ssl证书申请@https://freessl.cn/'
                            ]
                        },
                        {
                            moduleId: 'ai-about',
                            moduleName: 'AI相关',
                            parts:[
                                'ChatGPT@https://chatgpt.com/',
                                'Poe AI@https://poe.com/',
                                'Claude@https://claude.ai/chat/e9a44cfc-e12d-49cc-b9e7-85ef6dd587d2',
                                '智普清言@https://chatglm.cn/main/alltoolsdetail',
                                'Kimi@https://kimi.moonshot.cn/',
                                'groq@https://groq.com/',
                                'cloudflare ai playground@https://playground.ai.cloudflare.com/',
                                '林哥的大模型野榜@https://lyihub.com/chat',
                                '免魔法ChatGPT@https://chat.rawchat.cc/',
                                'AI合集@https://github.com/LiLittleCat/awesome-free-chatgpt',
                                '使用中的AI@https://openai.aifree.site/',
                                '文心一言@https://yiyan.baidu.com/',
                                '通义千问@https://tongyi.aliyun.com/',
                                '360GPT@https://www.so.com/zt/invite.html#/',
                                '星火认知@https://xinghuo.xfyun.cn/',
                                'huggingface chat@https://huggingface.co/chat/',
                                'picsart@https://picsart.com/create',
                                'freegpt@https://freegpt.one/',
                                'ai排行榜@https://chat.lmsys.org/',
                                'google aistudio@https://aistudio.google.com/app/prompts/new_chat'
                            ]
                        },
                        {
                            moduleId: 'sms-platform',
                            moduleName: '短信激活',
                            parts:[
                                'sms-activate@https://sms-activate.io/cn'
                            ]
                        },
                        {
                            moduleId: 'res-about',
                            moduleName: '资源清单',
                            parts:[
                                '云资源合集@https://gist.github.com/imba-tjd/d73258f0817255dbe77d64d40d985e76'
                            ]
                        }, 
                        {
                            moduleId: 'free-paas',
                            moduleName: 'paas平台',
                            parts:[
                                'fly.io@https://fly.io/dashboard',
                                'Railway@https://railway.app/dashboard',
                                'netlify@https://app.netlify.com/',
                                'vercel@https://vercel.com/dashboard',
                                'cloudflare@https://dash.cloudflare.com/',
                                'render@https://dashboard.render.com/web/srv-ckq83he2eoec739dofe0/settings',
                                'sealos云操作系统@https://bja.sealos.run/'
                            ]
                        },
                        {
                            moduleId: 'vm-container',
                            moduleName: '虚拟机容器相关',
                            parts:[
                                'Multipass@https://multipass.run/install',
                                'Podman@https://podman-desktop.io/downloads',
                                'Docker@https://www.docker.com/products/docker-desktop/'
                            ]
                        },
                        {
                            moduleId: 'online-coder',
                            moduleName: '在线代码编辑',
                            parts:[
                                'codesandbox@https://codesandbox.io/dashboard/recent',
                                'codepen@https://codepen.io/mg0324/pen/WNaZwYX',
                                'jsfiddle@https://jsfiddle.net/user/fiddles/all/',
                                'onlinegdb在线编辑器@https://www.onlinegdb.com/'
                            ]
                        },
                        {
                            moduleId: 'resource-nav',
                            moduleName: '资源导航',
                            parts:[
                                '千库网@https://588ku.com/so/shuqianye/',
                                '胖虎的工具箱@https://www.955code.com/',
                                'JDK11下载@https://blog.lupf.cn/articles/2022/02/24/1645713619397.html#toc_h2_17',
                                '各操作系统包@https://pkgs.org/'
                            ]
                        },
                        {
                            moduleId: 'front-ui',
                            moduleName: '前端UI库',
                            parts:[
                                'Layui@https://layui.gitee.io/v2/',
                                'heyui@https://www.heyui.top/',
                                '热门前端@https://mg.meiflower.top/skill/front/all'
                            ]
                        },
                        {
                            moduleId: 'cross-sale',
                            moduleName: '跨境电商运营',
                            parts:[
                                '速卖通@https://gsp.aliexpress.com/',
                                '17Track@https://www.17track.net/zh-cn'
                            ]
                        },
                        {
                            moduleId: 'code-manage',
                            moduleName: '代码托管',
                            parts:[
                                'Gitee@https://gitee.com/mgang',
                                'Github@https://github.com/mg0324',
                                'NPM packages@https://www.npmjs.com/settings/mgang/packages',
                                'DockerHub@https://hub.docker.com/'
                            ]
                        },
                        {
                            moduleId: 'open-project',
                            moduleName: '开源项目',
                            parts:[
                                    '深度学习飞桨@https://www.paddlepaddle.org.cn/',
                                    '网络工具frp@https://github.com/fatedier/frp',
                                    'spring-boot-demo@https://github.com/xkcoding/spring-boot-demo',
                                    'spring-brick@https://gitee.com/starblues/springboot-plugin-framework-parent',
                                    'sofa-jarslink@https://github.com/sofastack/sofa-jarslink',
                                    'JavaGuide轻量级http框架@https://github.com/Snailclimb/jsoncat',
                                    '代码导航@https://github.com/liyupi/code-nav',
                                    '微信Markdown编辑器@https://github.com/doocs/md'
                            ]
                        },
                        {
                            moduleId: 'al-study',
                            moduleName: '算法学习',
                            parts:[
                                '左神算法@https://github.com/mg0324/zuoshen-algorithm',
                                '算法4可视化@https://algs4.cs.princeton.edu/home/',
                                '牛客网@https://www.nowcoder.com/users/204732625',
                                '力扣@https://leetcode.cn/u/mangomei/',
                                'labuladong算法笔记@https://labuladong.gitee.io/algo/home/',
                                '算法可视化visualgo@https://visualgo.net/zh',
                                '代码可视化@https://algorithm-visualizer.org/'
                            ]
                        },
                        {
                            moduleId: 'it-man',
                            moduleName: 'IT大牛',
                            parts:[
                                'JavaGuide@https://github.com/Snailclimb',
                                'toBeBetterJavaer@https://github.com/itwanger/toBeBetterJavaer',
                                '龙进的博客@https://longjin666.cn/',
                                'liyupi@https://github.com/liyupi'
                            ]
                        },
                        {
                            moduleId: 'rspb',
                            moduleName: '树莓派',
                            parts:['树莓派操作系统@https://www.raspberrypi.com/software/operating-systems/']
                        },
                        {
                            moduleId: 'doc-about',
                            moduleName: '文档相关',
                            parts:[
                                'python-selenium3@https://python-selenium-zh.readthedocs.io/zh_CN/latest/',
                                'python-argparse@https://docs.python.org/zh-cn/3/library/argparse.html#',
                                'python-random@http://study.yali.edu.cn/pythonhelp/library/random.html',
                                'giscus app@https://giscus.app/zh-CN'
                            ]
                        },
                        {
                            moduleId: 'my-res',
                            moduleName: '我的资源',
                            parts:[
                                '我的蓝奏云@https://pc.woozooo.com/mydisk.php',
                                '七牛云oss@https://portal.qiniu.com/kodo/bucket/resource-v2?bucketName=mango',
                                '百度网盘@https://pan.baidu.com/',
                                '芒果网盘@http://disk.meiflower.top/',
                                'npm包@https://www.npmjs.com/'

                            ]
                        },
                        {
                            moduleId: 'cloud-parter',
                            moduleName: '云推广',
                            parts:[
                                '七牛云推广@https://portal.qiniu.com/cps/overview',
                                '腾讯云推广@https://console.cloud.tencent.com/spread/overview',
                                '阿里云推广@https://promotion.aliyun.com/ntms/yunparter/personal-center.html#/month-task',
                                '亿速云推广@https://uc2.yisu.com/index.php/parter/activity/index.html',
                                '看云推广@https://www.kancloud.cn/setting/parter'
                            ]
                        },
                        {
                            moduleId: 'sol-thing',
                            moduleName: '社会事宜',
                            parts:[
                                '广东交通局@https://gab.122.gov.cn/m/login',
                                '灵活就业事项@https://www.gdzwfw.gov.cn/portal/v2/search?region=440300&keyword=%E7%81%B5%E6%B4%BB%E5%B0%B1%E4%B8%9A&areaCode=440300&departmentCode=&onlyCorrespondingLevel=0&type=',
                                '深圳市公安局业务@https://msjw.ga.sz.gov.cn/?serviceType=1'
                            ]
                        },
                        {
                            moduleId: 'yl-res',
                            moduleName: '娱乐资源',
                            parts:[
                                '免费mp3@https://music.y444.cn/#/',
                                '腾讯视频@https://v.qq.com/'
                            ]
                        },
                        {
                            moduleId: 'store-img',
                            moduleName: '收藏图',
                            parts:[
                                '中国地图@https://www.gov.cn/xhtml/2016gov/images/guoqing/bigmap.jpg',
                            ]
                        }
                    ]
                };
            },
            computed: {
                linkCount(){
                    var sum = 0;
                    for(var node of this.nodes){
                        sum += node.parts.length;
                    }
                    return sum;
                }
            },
            methods: {
                aHref(v){
                    return window.location.href + "?id=" + v.moduleId;
                },
                theName(v){
                    return v.split('@')[0];
                },
                theHref(v){
                    return v.split('@')[1];
                }
            }
        });
    })();
</script>
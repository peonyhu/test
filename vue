<!doctype html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta content="initial-scale=1.0,user-scalable=no,maximum-scale=1,width=device-width" name="viewport">
	<meta name="format-detection" content="telephone=no">
	<link href="css/xs.css" rel="stylesheet" type="text/css">
	<title>新客私人定制</title>
</head>
<body class="xs_wrap">
<form>
<input type="hidden" value="5" id="friendId" name="friendId">
	<input type="hidden" name="friend" v-model="friend">
	<div class="xs_list">
		<div class="xs_listone">
			<div class="xs_icon"><em></em></div>
			<input type="text" value="" placeholder="请输入您的手机号码" id="mobile" v-on:blur="blur" @focus="focus" v-model="mobile">
			<p class="" id="mobile_prompt" :class="[xs_error]" v-text="mobile_prompt"></p>
		</div>
		<div class="xs_listone xs_listtwo">
			<div class="xs_icon"><em></em></div>
			<input type="text" value="" placeholder="请输入验证码" class="yzmval">
			<input id="xsreyzm" class="xsreyzm" value="发送" type="button" @click="send">
			<p :class="[xs_error]" id="yzm_prompt"  v-text="yzm_prompt"></p>
		</div>
		<div class="xs_listone xs_listthird">
			<div class="xs_icon"><em></em></div>
			<input type="text" value="" placeholder="请输入你的密码" id="pwd" v-on:blur='blurpwd' @focus="focuspwd" v-model='pwd'>
			<p class="" id="pwd_prompt" :class="[xs_error]" v-text="pwd_prompt"></p>
		</div>
		<div class="xs_listone xs_listthird">
			<div class="xs_icon"><em></em></div>
			<input type="text" value="" placeholder="请再次确认你的密码" id="repwd">
			<p class="" id="repwd_prompt"></p>
		</div>
		<a class="xs_bn" href="#" id="xsbnmobile" @click="nextStep">下一步</a>
		<div class="xs_info">
			<div class="xs_infotit"><em></em>*金汇金融由中国建设银行资金监管</div>
			<div class="xs_infolist">
				<ul class="xs_infoulone clearfix">
					<li></li>
					<li>信息披露</li>
					<li></li>
				</ul>
				<ul class="xs_infoultwo clearfix">
					<li class="">
						<em></em>金融机构产品聚合直销平台
					</li>
					<li class="">
						<span href="#"><em></em>15年用户最信任互联网金融平台</span>
					</li>
					<li class=""> 
						<em></em>累计成交额突破300亿
					</li>
				</ul>
			</div>
		</div>
	</div>
</form>
<!-- <script type="text/javascript" src="js/jquery-1.7.1.min.js"></script> -->
<script type="text/javascript" src="http://cdnjs.cloudflare.com/ajax/libs/vue/1.0.26/vue.min.js"></script>
<script src="https://cdn.jsdelivr.net/vue.resource/1.0.3/vue-resource.min.js"></script>
<script type="text/javascript">
	var vm = new Vue({
		el:'.xs_list',
		data:{
			mobile:'',
			pwd:'',
			kaptchaCode:'',
			mobile_prompt:'',
			pwd_prompt:'',
			yzm_prompt:'',
			xs_error:'xs_error',
			result:true,
			friend:5
		},
		methods:{
			blur:function(){
				if(this.mobile == ''){
					this.mobile_prompt = '*请输入手机号码';
					return false;
				}else if(!(/^1\d{10}$/.test(this.mobile))){
					this.mobile_prompt = '*输入错误，请输入11位手机号码';
					return false;
				}else{
					this.mobile_prompt = '';
				}
			},
			focus:function(){
				this.mobile_prompt = '';
			},
			blurpwd:function(){
				if(this.pwd == ''){
					this.pwd_prompt = '*请输入密码';
					return false;
				}else if(this.pwd.length < 6 || this.pwd.length > 16){
					this.pwd_prompt = '*密码长度应在6-16位，请重新输入';
					return false;
				}else{
					this.pwd_prompt = '';
				}
			},
			focuspwd:function(){
				this.pwd_prompt = '';
			},
			nextStep:function(){
				if(this.mobile == ''){
					this.mobile_prompt = '*请输入手机号码';
					return false;
				}
				if(this.pwd == ''){
					this.pwd_prompt = '*请输入密码';
					return false;
				}
			},
			send:function(){
				this.pwd_prompt = '';
				this.mobile_prompt = '';
				this.yzm_prompt = '';
				if(this.mobile == ''){
					this.mobile_prompt = '*请输入手机号码';
					return false;
				}else if(!(/^1\d{10}$/.test(this.mobile))){
					this.mobile_prompt = '*输入错误，请输入11位手机号码';
					return false;
				}else{
					if(Time == 10){
						// this.$http.post('http://gvwx-dev_zdhu.asjr365.com/redPacket/api.php?action=send',{
						//     mobile:this.mobile
						// },{
						//     emulateJSON:true
						// }).then(function(data){
						// 	var data = eval('('+data.data+')');
						// 	if(data.message.code == 0){
						// 		this.kaptchaCode_prompt = ''
		    //                     timedCount();
						// 	}else{
						// 		if(data.message.code == -205 || data.message.code == -222){
	     //                            this.kaptchaCode_prompt = '*'+data.message.message;  
						// 	    }else{
						// 	    	this.yzm_prompt = '*'+data.message.message;  
						// 	    }
						// 	}
						// },function(res){
						//     alert(res.status);
						// });
						
					}
				}
			}
		}
	})
//http://gvwx-dev_zdhu.asjr365.com/redPacket/api.php?action=send
var Time=10,    t;
var c = Time;
var xsreyzm = document.getElementById('xsreyzm');
function timedCount(){
    xsreyzm.value = c;
    xsreyzm.setAttribute("disabled","disabled");
    c=c-1;
    t=setTimeout("timedCount()",1000);
    if(c<0){
        c=Time;
        stopCount();
        xsreyzm.value="重新发送";
        xsreyzm.removeAttribute("disabled");
    }
}
function stopCount(){
    clearTimeout(t);
}
</script>
<!-- <script type="text/javascript" src="js/xs.js"></script> -->
</body>
</html>

# layuiUse
layui使用小结

１.　从父页面中弹出弹窗，在弹窗中通过点击确定按钮关闭弹窗的同时，使用

 //关闭弹窗
 
      var index = parent.layer.getFrameIndex(window.name);
      
      parent.layer.close(index);
      
               刷新父页面中的表格,　type:2的形式弹窗
	       
      parent.layui.table.reload('testReload');
      

 ３.　type:1的形式弹窗，使用此　语句　layui.table.reload('testReload');刷新父页表格数据
 
 其中　testReload　为表格ID
 
 4. 详情页回显数据
 
         <select disabled id='selectId'>
                  <!-- 后台读取值 -->
           </select>
 
 　select下拉框： 
  
     $("<option value="+datas.jobExcuteMode+">"+datas.jobExcuteMode+"</option>").appendTo("#selectId");
  
  单选按钮: 
  
       <div class="layui-input-block" id="radios" style="margin-left:180px;">
       <!-- 后台接口获取 -->
               <input type="radio" name="radio" value="0" title="否" disabled>
                <input type="radio" name="radio" value="1" title="是" disabled>
         </div>
	 
	 回显结果：
	 
           $("input[name=radio][value=1]").attr("checked", datas.jFailover == 1 ? true : false);
           $("input[name=radio][value=0]").attr("checked", datas.jFailover == 0 ? true : false);
	   
	   
　修改页面中的回显：
 
 　　　 $.ajax({
                url: '下拉框中的接口地址',
                type: 'get',
                success: function(data){
                     taskTypes = data.taskType; //作业类型
                    taskStatuss = data.taskStatus;  //作业状态
                    regCodes = data.regCode;
                    taskGroupCodes = data.taskGroupCode; //作业组编码
                    taskSubmitCycles = data.taskSubmitCycle;
                    taskExcuteModes = data.taskExcuteMode;
                    taskRunModes = data.taskRunMode;
                    taskShardingstrategys = data.taskShardingStrategyClass;
               
                }
            })
 　　　
	
	 //调接口数据 ,先回显出数据
            var jobCode = window.sessionStorage.getItem('jobCode');
            $.ajax({
                url: batchUrl + 'job-info/'+jobCode,
                type: 'get',
                xhrFields:{
                    withCredentials:true
                },
                crossDomain:true,
                success:function(data){
                    var datas = data.data;
		    //作业运行方式
                $.each(taskExcuteModes,function(index,item){
                    if(!taskRunMode){
                        var option = new Option(item.name,item.code);
                    }else {
                        var option = new Option(item.name,item.code);
                        // // 如果是之前的内容则设置选中
                        if(item.code == datas.taskRunMode) {
                            option.setAttribute("selected",'true');
                        }
                    };
                    $('#taskRunMode').append(option);//往下拉菜单里添加元素
                    form.render(); //这个很重要
                })
		
		
		}
	});

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
 
 　select下拉框： $("<option value="+datas.jobExcuteMode+">"+datas.jobExcuteMode+"</option>").appendTo("#selectId");
  
  单选按钮: 
  
       <div class="layui-input-block" id="radios" style="margin-left:180px;">
       <!-- 后台接口获取 -->
               <input type="radio" name="radio" value="0" title="否" disabled>
                <input type="radio" name="radio" value="1" title="是" disabled>
         </div>
	 
           $("input[name=radio][value=1]").attr("checked", datas.jFailover == 1 ? true : false);
           $("input[name=radio][value=0]").attr("checked", datas.jFailover == 0 ? true : false);
		


##Uploader上传组件##
                所需文件：uploader.js
                注：每个form只能对应一个上传域
                参数说明：
                        fileField：文件域(dom节点，必须有)
                        form:包含文件域的表单(dom节点，必须有)
                        fileType:文件类型 image(默认) | video | photo(图片有大小限制)
                        beforeStart:上传前操作函数 （返回一个对象 包含文件的基本信息：名字，后缀，全称）
                        success：成功回调函数 （返回一个对象 包含文件的完整信息 result.url:文件的路径）
                        fail: 失败回调函数 （返回一个错误对象 error.message: 错误信息）

                绑定：
                var uploader1 = Uploader({
                        fileField:file,
                        form:document.form,
                        fileType:'image',
                        beforeStart:function(file){
                                alert(file.value);
                        },
                        success:function(result){
                                alert(result.url);
                        },
                        fail:function(error){
                                alert(error.message);
                        }
                });

                上传：
                uploader1.submit() 或者 file.uploader.submit()


                demo:
                <div id="result"><div/>
                <form name="form1" id="form1"  >
        		
        		<p>
        			<span>change的时候上传 选择一张图片:</span>
        			<input type="file" name="file" id="file1">
        		</p>
        	
        	   </form>

               <script>
                        //上传    
                		var up = Uploader({
                			fileField:document.getElementById('file1'),
                			form:document.getElementById('form1'),
                			fileType:'image',
                			beforeStart:function(file){
                				document.getElementById('result').innerHTML = '正在上传：'+file.value;
                	           
                			},
                			success:function(result){
                				document.getElementById('result').innerHTML = '<a href="'+result.url+'">'+result.url+'</a>';
                			},
                			fail:function(error){
                				alert(error.message);
                			}
                		});
                		document.getElementById('form1').onchange = function(){
                			up.submit();
                		}

               </script>
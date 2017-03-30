# Vue

参考：http://cn.vuejs.org/v2/guide/events.html

---


 1. //根实例  VM
			new Vue({   //选项参数
				el:"#box",
				data:{//data传入的必须是对象或者函数
				message:"hello,Vue!"
			}
			});
 2. 在vue中事件处理程序中this指向的是根实例，vue会把data中的数据，放在根实例上
 3. //标签上可以放自定义属性
		//v-bind 动态的绑定数据，响应的数据绑定  当数据发生变化的时候，视图会自动更新
 4. v-bind:class="{class名字:一个表达式}"    class是否添加到这个元素上，取决于对应的表达式是true还是fasle
 5. 	v-bind: 简写为 :
				v-on:   简写为  @
 6. **绑定事件处理程序**  事件处理程序统一的写在选项项的methods中；
 7. **事件修饰符**	利用修饰符，methods 只有纯粹的数据逻辑，而不是去处理 DOM 事件细节
 8. v-if="表达式"  v-show=“表达式” 根据表达式的值是true或false，来决定使用这个指令的元素显示隐藏，
 v-if移入和添加使用指令的节点；
v-show切换css的display的block和none；
频繁切换元素显示隐藏，用v-show；
在触发某个事件后要先是某一块内容，之后就不在频繁切换了，就用v-if；
 9. template自定义标签 
					v-show不支持
 10. 在模板中不要放入过多的逻辑处理	在模板中放入太多的逻辑会让模板过重且难以维护
 11. **computed:**计算属性:计算后的值缓存起来，多次使用都用的是第一次计算后的值,	在计算属性函数中，依赖的数据发生了变化，会重新计算，然后把值缓存起来
 12. vue内置提供的方法或属性 调用的时候属性或方法加上$
 13. watch:对数据变化进行监控，deep为true是深度监控，
new Vue({
			el:'#box',
			data:{
				message:[{a:1}],
			},
			watch:{
				message:
				{
					handler:function(){
					console.log("我变了")
					},
					deep:true//深度监控
				}
				
			}
		})

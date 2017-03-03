<div class="markdown-body ng-scope" clip-copy-code="pre" ng-if="readme.previewed" cg-highlight="readme.preview"><h3 class="ng-scope"><a id="user-content-roomap-api" class="coding icon coding-anchor" href="/u/caybear/p/roomap/git#user-content-roomap-api" rel="nofollow noopener noreferrer"></a>ROOMAP API</h3> 
<p class="ng-scope">@(用法示例)[最后更新时间: 2017年03月03日]</p> 
<div class="markdown-toc ng-scope"> 
 <ul> 
  <li><a href="#user-content-roomap-api" id="markdown-toc-user-content-roomap-api" rel="nofollow noopener noreferrer">ROOMAP API</a> 
   <ul> 
    <li><a href="#user-content-jia-zai-di-tu-javascript-api" id="markdown-toc-user-content-jia-zai-di-tu-javascript-api" rel="nofollow noopener noreferrer">加载地图JavaScript API</a></li> 
    <li><a href="#user-content-xuan-ding-di-tu-de-divrong-qi" id="markdown-toc-user-content-xuan-ding-di-tu-de-divrong-qi" rel="nofollow noopener noreferrer">选定地图的div容器</a></li> 
    <li><a href="#user-content-chuang-jian-jiu-dian-di-tu-dui-xiang" id="markdown-toc-user-content-chuang-jian-jiu-dian-di-tu-dui-xiang" rel="nofollow noopener noreferrer">创建酒店地图对象</a></li> 
    <li><a href="#user-content-she-ding-lou-ceng-shi-fou-yin-cang" id="markdown-toc-user-content-she-ding-lou-ceng-shi-fou-yin-cang" rel="nofollow noopener noreferrer">设定楼层是否隐藏</a></li> 
    <li><a href="#user-content-she-ding-fang-jian-shi-fou-ke-xuan" id="markdown-toc-user-content-she-ding-fang-jian-shi-fou-ke-xuan" rel="nofollow noopener noreferrer">设定房间是否可选</a></li> 
    <li><a href="#user-content-yu-ding-qu-xiao-yu-ding-fang-jian" id="markdown-toc-user-content-yu-ding-qu-xiao-yu-ding-fang-jian" rel="nofollow noopener noreferrer">预定/取消预定房间</a></li> 
    <li><a href="#user-content-zhen-ting-yong-hu-hong-fa-shi-jian" id="markdown-toc-user-content-zhen-ting-yong-hu-hong-fa-shi-jian" rel="nofollow noopener noreferrer">侦听用户触发事件</a></li> 
   </ul> </li> 
 </ul> 
</div> 
<h5 class="ng-scope"><a id="user-content-jia-zai-di-tu-javascript-api" class="coding icon coding-anchor" href="/u/caybear/p/roomap/git#user-content-jia-zai-di-tu-javascript-api" rel="nofollow noopener noreferrer"></a>加载地图JavaScript API</h5> 
<div class="md-code" style="position: relative; min-height: 30px;"><pre class="ng-scope"><code class="hljs xml"><span class="hljs-comment">&lt;!--页面直接引入--&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-title">script</span> <span class="hljs-attribute">type</span>=<span class="hljs-value">"text/javascript"</span> <span class="hljs-attribute">src</span>=<span class="hljs-value">"http://caybear.com/maps?v=1.0.1&amp;key=您申请的key值"</span>&gt;</span><span class="undefined"></span><span class="hljs-tag">&lt;/<span class="hljs-title">script</span>&gt;</span> 
</code></pre><span class="copy-action" style="position: absolute; background: rgb(178, 177, 174); color: rgb(255, 255, 255); text-align: center; cursor: pointer; height: 30px; width: 30px; line-height: 30px; top: 0px; right: 0px; z-index: 999; display: none;"><i class="icon copy" style="margin-right: 0;"></i></span></div> 
<p class="ng-scope">###</p> 
<h5 class="ng-scope"><a id="user-content-xuan-ding-di-tu-de-divrong-qi" class="coding icon coding-anchor" href="/u/caybear/p/roomap/git#user-content-xuan-ding-di-tu-de-divrong-qi" rel="nofollow noopener noreferrer"></a>选定地图的div容器</h5> 
<div class="md-code" style="position: relative; min-height: 30px;"><pre class="ng-scope"><code class="hljs xml"><span class="hljs-comment">&lt;!--定义 id 名为 "map" 的 div标签，并设置其大小--&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-title">div</span> <span class="hljs-attribute">id</span>=<span class="hljs-value">"map"</span> <span class="hljs-attribute">style</span>=<span class="hljs-value">"width:414px; height:736px"</span>&gt;</span><span class="hljs-tag">&lt;/<span class="hljs-title">div</span>&gt;</span>
</code></pre><span class="copy-action" style="position: absolute; background: rgb(178, 177, 174); color: rgb(255, 255, 255); text-align: center; cursor: pointer; height: 30px; width: 30px; line-height: 30px; top: 0px; right: 0px; z-index: 999; display: none;"><i class="icon copy" style="margin-right: 0;"></i></span></div> 
<p class="ng-scope">###</p> 
<h5 class="ng-scope"><a id="user-content-chuang-jian-jiu-dian-di-tu-dui-xiang" class="coding icon coding-anchor" href="/u/caybear/p/roomap/git#user-content-chuang-jian-jiu-dian-di-tu-dui-xiang" rel="nofollow noopener noreferrer"></a>创建酒店地图对象</h5> 
<div class="md-code" style="position: relative; min-height: 30px;"><pre class="ng-scope"><code class="hljs typescript"><span class="hljs-comment">//在 id 为 "map" 的 div 层上绘制酒店图形</span>
<span class="hljs-keyword">var</span> hotel = RMap.hotel(<span class="hljs-string">'map'</span>,&lt;<span class="hljs-built_in">String</span>&gt; hotel_id,{
    zoom:<span class="hljs-number">17</span>, <span class="hljs-comment">//初始缩放级别</span>
    filter:{
        floors:&lt;<span class="hljs-built_in">Array</span>&gt; floors, <span class="hljs-comment">//隐藏楼层</span>
        rooms:&lt;<span class="hljs-built_in">Array</span>&gt; rooms <span class="hljs-comment">//设定不可选房间</span>
    }
})
</code></pre><span class="copy-action" style="position: absolute; background: rgb(178, 177, 174); color: rgb(255, 255, 255); text-align: center; cursor: pointer; height: 30px; width: 30px; line-height: 30px; top: 0px; right: 0px; z-index: 999; display: none;"><i class="icon copy" style="margin-right: 0;"></i></span></div> 
<table class="ng-scope">  
 <tbody><tr> 
  <th><small>参数</small></th> 
  <th><small>示例</small></th> 
  <th><small>说明</small></th> 
 </tr>  
 </tbody><tbody> 
  <tr> 
   <td><small>hotel_id</small></td> 
   <td><small>“iiiiiRT”</small></td> 
   <td><small>酒店ID</small></td> 
  </tr> 
  <tr> 
   <td><small>floors</small></td> 
   <td><small>[{floor:[“楼层”,...],building:”楼名”},...]</small></td> 
   <td><small>无”楼名”可置空</small></td> 
  </tr> 
  <tr> 
   <td><small>rooms</small></td> 
   <td><small>[{room:[“房间名”,...],building:”楼名”},...]</small></td> 
   <td><small>无”楼名”可置空</small></td> 
  </tr> 
 </tbody> 
</table> 
<p class="ng-scope">###</p> 
<h5 class="ng-scope"><a id="user-content-she-ding-lou-ceng-shi-fou-yin-cang" class="coding icon coding-anchor" href="/u/caybear/p/roomap/git#user-content-she-ding-lou-ceng-shi-fou-yin-cang" rel="nofollow noopener noreferrer"></a>设定楼层是否隐藏</h5> 
<div class="md-code" style="position: relative; min-height: 30px;"><pre class="ng-scope"><code class="hljs css"><span class="hljs-tag">hotel</span><span class="hljs-class">.hide</span>(&lt;<span class="hljs-tag">Array</span>&gt; <span class="hljs-tag">floors</span>)
<span class="hljs-tag">hotel</span><span class="hljs-class">.unhide</span>(&lt;<span class="hljs-tag">Array</span>&gt; <span class="hljs-tag">floors</span>)
</code></pre><span class="copy-action" style="position: absolute; background: rgb(178, 177, 174); color: rgb(255, 255, 255); text-align: center; cursor: pointer; height: 30px; width: 30px; line-height: 30px; top: 0px; right: 0px; display: none; z-index: 999;"><i class="icon copy" style="margin-right: 0;"></i></span></div> 
<table class="ng-scope">  
 <tbody><tr> 
  <th><small>参数</small></th> 
  <th><small>示例</small></th> 
  <th><small>说明</small></th> 
 </tr>  
 </tbody><tbody> 
  <tr> 
   <td><small>floors</small></td> 
   <td><small>[{floor:[“楼层”,...],building:”楼名”},...]</small></td> 
   <td><small>无”楼名”可置空</small></td> 
  </tr> 
 </tbody> 
</table> 
<p class="ng-scope">###</p> 
<h5 class="ng-scope"><a id="user-content-she-ding-fang-jian-shi-fou-ke-xuan" class="coding icon coding-anchor" href="/u/caybear/p/roomap/git#user-content-she-ding-fang-jian-shi-fou-ke-xuan" rel="nofollow noopener noreferrer"></a>设定房间是否可选</h5> 
<div class="md-code" style="position: relative; min-height: 30px;"><pre class="ng-scope"><code class="hljs css"><span class="hljs-tag">hotel</span><span class="hljs-class">.block</span>(&lt;<span class="hljs-tag">Array</span>&gt; <span class="hljs-tag">rooms</span>)
<span class="hljs-tag">hotel</span><span class="hljs-class">.unblock</span>(&lt;<span class="hljs-tag">Array</span>&gt; <span class="hljs-tag">rooms</span>)
</code></pre><span class="copy-action" style="position: absolute; background: rgb(178, 177, 174); color: rgb(255, 255, 255); text-align: center; cursor: pointer; height: 30px; width: 30px; line-height: 30px; top: 0px; right: 0px; display: none; z-index: 999;"><i class="icon copy" style="margin-right: 0;"></i></span></div> 
<table class="ng-scope">  
 <tbody><tr> 
  <th><small>参数</small></th> 
  <th><small>示例</small></th> 
  <th><small>说明</small></th> 
 </tr>  
 </tbody><tbody> 
  <tr> 
   <td><small>rooms</small></td> 
   <td><small>[{room:[“房间名”,...],building:”楼名”},...]</small></td> 
   <td><small>无”楼名”可置空</small></td> 
  </tr> 
 </tbody> 
</table> 
<p class="ng-scope">###</p> 
<h5 class="ng-scope"><a id="user-content-yu-ding-qu-xiao-yu-ding-fang-jian" class="coding icon coding-anchor" href="/u/caybear/p/roomap/git#user-content-yu-ding-qu-xiao-yu-ding-fang-jian" rel="nofollow noopener noreferrer"></a>预定/取消预定房间</h5> 
<div class="md-code" style="position: relative; min-height: 30px;"><pre class="ng-scope"><code class="hljs css"><span class="hljs-tag">hotel</span><span class="hljs-class">.book</span>(&lt;<span class="hljs-tag">Array</span>&gt; <span class="hljs-tag">rooms</span>)
<span class="hljs-tag">hotel</span><span class="hljs-class">.unbook</span>(&lt;<span class="hljs-tag">Array</span>&gt; <span class="hljs-tag">rooms</span>)
</code></pre><span class="copy-action" style="position: absolute; background: rgb(178, 177, 174); color: rgb(255, 255, 255); text-align: center; cursor: pointer; height: 30px; width: 30px; line-height: 30px; top: 0px; right: 0px; display: none; z-index: 999;"><i class="icon copy" style="margin-right: 0;"></i></span></div> 
<table class="ng-scope">  
 <tbody><tr> 
  <th><small>参数</small></th> 
  <th><small>示例</small></th> 
  <th><small>说明</small></th> 
 </tr>  
 </tbody><tbody> 
  <tr> 
   <td><small>rooms</small></td> 
   <td><small>[{room:[“房间名”,...],building:”楼名”},...]</small></td> 
   <td><small>无”楼名”可置空</small></td> 
  </tr> 
 </tbody> 
</table> 
<p class="ng-scope">###</p> 
<h5 class="ng-scope"><a id="user-content-zhen-ting-yong-hu-hong-fa-shi-jian" class="coding icon coding-anchor" href="/u/caybear/p/roomap/git#user-content-zhen-ting-yong-hu-hong-fa-shi-jian" rel="nofollow noopener noreferrer"></a>侦听用户触发事件</h5> 
<div class="md-code" style="position: relative; min-height: 30px;"><pre class="ng-scope"><code class="hljs actionscript">hotel.on(&lt;String&gt; event, <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">(&lt;Object&gt; data)</span></span>{
    <span class="hljs-comment">//todo</span>
})
</code></pre><span class="copy-action" style="position: absolute; background: rgb(178, 177, 174); color: rgb(255, 255, 255); text-align: center; cursor: pointer; height: 30px; width: 30px; line-height: 30px; top: 0px; right: 0px; display: none; z-index: 999;"><i class="icon copy" style="margin-right: 0;"></i></span></div> 
<table class="ng-scope">  
 <tbody><tr> 
  <th><small>参数</small></th> 
  <th><small>示例</small></th> 
  <th><small>说明</small></th> 
 </tr>  
 </tbody><tbody> 
  <tr> 
   <td><small>event</small></td> 
   <td><small>“click”</small></td> 
   <td><small>支持”click”</small></td> 
  </tr> 
  <tr> 
   <td><small>data</small></td> 
   <td><small>{room:[“房间名”,...],building:”楼名”}</small></td> 
   <td><small>无”楼名”可置空</small></td> 
  </tr> 
 </tbody> 
</table> 
<p class="ng-scope">###</p></div>

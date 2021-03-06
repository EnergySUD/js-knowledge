
# 防抖

### 在前端开发中会遇到一些频繁的事件触发，比如：

1. window 的 resize、scroll
2. mousedown、mousemove
3. keyup、keydown ……

### 防抖关键代码
```javascript
	function debounce(func, wait, immediate) {
	    let timeout, result;
	
	    let debounced = function () {
	        var context = this;
	        var args = arguments;
	
	        if (timeout) clearTimeout(timeout);
	        if (immediate) {
	            // 如果已经执行过，不再执行
	            var callNow = !timeout;
	            timeout = setTimeout(function(){
	                timeout = null;
	            }, wait)
	            if (callNow) result = func.apply(context, args)
	        }
	        else {
	            timeout = setTimeout(function(){
	                func.apply(context, args)
	            }, wait);
	        }
	        return result;
	    };
	
	    debounced.cancel = function() {
	        clearTimeout(timeout);
	        timeout = null;
	    };
	
	    return debounced;
	}
```

1. 声明式代码的更新性能消耗 = 找出差异的性能消耗 + 直接修改的性能消耗
   因此,如何能最小化找出差异的性能消耗就可以让声明式代码的性能无限接近命令式代码的性能,而所谓的虚拟 DOM 就是为了最小化找出差异这一步的性能消耗而出现的

所以到现在,应该至少清楚了: 采用虚拟 DOM 更新技术的性能理论上不可能比原生 js 操作 DOM 性能更高

2.  对比虚拟 DOM 与 innerHTML 在创建页面时的性能
    虚拟 DOM 创建页面的过程分为两步: 1.创建 js 对象,这个对象可以理解为真是 DOM 的描述 2.递归遍历虚拟 DOM 树并创建真实 DOM

        对比:
        	虚拟DOM: 创建javascript对象(VNode) + 新建所有DOM元素
        	innerHTML: 渲染HTML字符串 + 新建所有DOM元素
        		结论: 并无明显差异

3.  对比虚拟 DOM 与 innerHTML 在更新页面时的性能
    对比:
    虚拟 DOM: 创建 javascript 对象(VNode) + diff + 更新必要的 DOM
    innerHTML: 渲染 HTML 字符串 + 销毁所有旧 DOM + 新建所有新 DOM

        结论: innerHTML更新页面的过程是重新构建, 虚拟DOM是重新创建javascript对象,可以理解为虚拟DOM树,然后进行新旧DOM比对,找到变化的VNode并更新她

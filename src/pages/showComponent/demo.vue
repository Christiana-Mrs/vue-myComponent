<template>
  <div class="component">

    <!-- 组件展示   -->
    <div  class="component_left">
      <p>数字滚动组件</p>
      <ul class="flex">
        <ScrollNum
            v-for="(num, idx) of numArr"
            :key="idx"
            as="li"
            :i="num"
            :delay="idx + 1"
            class="num"
        />
      </ul>
    </div>

    <!-- 文字说明   -->
    <div class="component_right">
      <p class="component_tittle">组件说明</p>
      <p>
        如果把这个组件复制到项目中去 发现样式显示不正确的话，只需要解开CSS部分ul里注释掉的样式即可。<br/>
        出现这种现象的原因是你没有引入reset.css， 导致ul标签有默认的边距、li标签有默认的小圆点。如果有reset.css的话，就删掉这段没用的注释。
      </p>
      <p>
        这个组件封装的思路主要是用到了CSS变量+calc函数来控制滚动时长，在不传--width和--height宽高的情况下默认会是20 * 36，<br/>
        还可以只传宽不传高，利用calc函数能保证在只传宽度的情况下，高度依然能够保持住原有的比例。<br/>
        我知道这时肯定会有人说：想要保持比例用aspect-ratio就行了，何必那么麻烦呢？

      </p>
       <p>
         首先就是这个属性比较新，兼容性还不是特别好，虽然Edge、火狐和谷歌的最新几个版本都已经支持这一属性了，<br/>
         但Safari浏览器只有15-技术预览版才支持，而在IOS下则是完全不支持：
       </p>
       <div>
         <img class="img" src="@/assets/img/litu.png" alt="">
         <img class="img" src="@/assets/img/litu2.png" alt=""/>
       </div>

      <p>
        要知道用iPhone的用户大多数都会选择Safari，因为他们也不懂什么各种浏览器啥的，只知道点这个指南针🧭一样的图标是用来上网的。<br/>
        另一点则是我们其实并不是非要保持住这个比例，这是只是我封装组件的一个习惯。<br/>
        有时候懒，希望用组件时只传一个宽或者高就得了，没传的那个参数能够自动计算，所以才会封装成这个样子。<br/>
        你可以按照自己的喜好来，把那段代码改成你喜欢的样子。
      </p>

    </div>
  </div>
</template>
<script>
import ScrollNum from '@/components/component/ScrollNum.vue'
export default {
  name: "demo",
  components:{ ScrollNum },
  data: () => ({ num: 996 }),
  computed: {
    numArr () {
      const str = String(this.num)
      return [parseInt(str[0]), parseInt(str[1]), parseInt(str[2])]
    }
  }
}
</script>

<style scoped>
.component {
  display: flex;
  padding-top: 40px;
}
.component_left {
  width: 300px;
  height: 300px;
  background-color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  border-radius: 5%;
  box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1)
}
.component_right {
  padding: 0 50px;
}
.component_tittle {
  font-size: 26px;
  font-weight: 700;
}
  .flex,.tuwen {
    display: flex;
  }
  ul {
    padding: 0;
    margin: 0;
    list-style: none;
  }

  .num {
    --width: 26px;
    margin-right: 6px;
    border: 1px solid black;
    border-radius: 8px
  }
  .img {
    display: inline-block;
    width: 400px;
    margin-right: 50px;
    margin-bottom: 10px;
  }
</style>
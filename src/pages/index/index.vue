<script lang="ts" setup>
defineOptions({
  name: 'Home',
})
definePage({
  // 使用 type: "home" 属性设置首页，其他页面不需要设置，默认为page
  type: 'home',
  style: {
    // 'custom' 表示开启自定义导航栏，默认 'default'
    navigationStyle: 'custom',
    navigationBarTitleText: '首页',
  },
})

// 模拟数据
const movies = [
  {
    id: '1',
    title: '热门大片1',
    rating: '9.2',
    genre: '动作 / 科幻',
    poster: '/static/images/default-avatar.png',
  },
  {
    id: '2',
    title: '浪漫爱情',
    rating: '8.8',
    genre: '爱情 / 剧情',
    poster: '/static/images/default-avatar.png',
  },
  {
    id: '3',
    title: '喜剧之王',
    rating: '8.5',
    genre: '喜剧 / 家庭',
    poster: '/static/images/default-avatar.png',
  },
  {
    id: '4',
    title: '惊悚悬疑',
    rating: '8.1',
    genre: '悬疑 / 惊悚',
    poster: '/static/images/default-avatar.png',
  },
]

const cinemas = [
  {
    id: '1',
    name: '万达影城（西湖店）',
    address: '杭州市西湖区文三路123号 · 1.2km',
    tags: ['IMAX', '杜比全景声'],
    price: '¥45起',
  },
  {
    id: '2',
    name: 'CGV影城（湖滨店）',
    address: '杭州市上城区湖滨路456号 · 2.5km',
    tags: ['4DX', 'VIP厅'],
    price: '¥40起',
  },
  {
    id: '3',
    name: '大地影院（下沙店）',
    address: '杭州市江干区下沙街道文泽路99号 · 5.8km',
    tags: ['激光厅', '情侣座'],
    price: '¥35起',
  },
]

onLoad(() => {
  console.log('首页加载完成')
})
</script>

<template>
  <view class="min-h-screen bg-[#f5f5f5]">
    <!-- 顶部导航栏 -->
    <view class="fixed left-0 right-0 top-0 z-10 flex items-center justify-between bg-white px-4 py-3 shadow-sm">
      <div class="from-yellow-500 to-orange-500 bg-gradient-to-r bg-clip-text text-xl text-transparent font-bold">
        票时代
      </div>
      <div class="flex items-center">
        <view class="mr-4 flex items-center">
          <text class="mr-1">📍</text>
          <text>杭州</text>
          <text class="ml-1 text-xs">▼</text>
        </view>
        <view class="h-8 w-8 flex items-center justify-center rounded-full from-purple-500 to-pink-500 bg-gradient-to-r text-sm text-white">
          用
        </view>
      </div>
    </view>

    <!-- 主内容区域 -->
    <view class="pb-[60px] pt-[60px]">
      <!-- 轮播图 -->
      <view class="px-4 py-3">
        <view class="h-36 flex items-center justify-center rounded-xl from-purple-500 to-pink-500 bg-gradient-to-r text-white font-bold">
          🎬 热门电影推荐
        </view>
      </view>

      <!-- 快捷入口 -->
      <view class="px-4 py-3">
        <view class="grid grid-cols-4 gap-4">
          <view class="flex flex-col items-center">
            <view class="mb-1 h-12 w-12 flex items-center justify-center rounded-xl from-blue-500 to-cyan-500 bg-gradient-to-r text-xl text-white">
              🎬
            </view>
            <text class="text-xs">电影</text>
          </view>
          <view class="flex flex-col items-center">
            <view class="mb-1 h-12 w-12 flex items-center justify-center rounded-xl from-green-500 to-emerald-500 bg-gradient-to-r text-xl text-white">
              🎭
            </view>
            <text class="text-xs">演出</text>
          </view>
          <view class="flex flex-col items-center">
            <view class="mb-1 h-12 w-12 flex items-center justify-center rounded-xl from-yellow-500 to-amber-500 bg-gradient-to-r text-xl text-white">
              🛍️
            </view>
            <text class="text-xs">卖品</text>
          </view>
          <view class="flex flex-col items-center">
            <view class="mb-1 h-12 w-12 flex items-center justify-center rounded-xl from-red-500 to-pink-500 bg-gradient-to-r text-xl text-white">
              💳
            </view>
            <text class="text-xs">会员</text>
          </view>
        </view>
      </view>

      <!-- 正在热映 -->
      <view class="mt-2 bg-white px-4 py-3">
        <view class="mb-3 flex items-center justify-between">
          <text class="text-lg font-bold">🔥 正在热映</text>
          <text class="text-sm text-gray-500">查看更多 ›</text>
        </view>
        <view class="grid grid-cols-2 gap-4">
          <view v-for="movie in movies" :key="movie.id" class="overflow-hidden rounded-xl bg-gray-50">
            <view class="h-36 flex items-center justify-center from-blue-500 to-purple-500 bg-gradient-to-r">
              <text class="px-2 text-center text-sm text-white">电影海报<br>{{ movie.title }}</text>
            </view>
            <view class="p-2">
              <text class="truncate text-sm font-bold">{{ movie.title }}</text>
              <text class="mt-1 block text-xs text-yellow-500">⭐ {{ movie.rating }}</text>
              <text class="mt-1 block text-xs text-gray-500">{{ movie.genre }}</text>
            </view>
          </view>
        </view>
      </view>

      <!-- 附近影院 -->
      <view class="mt-2 bg-white px-4 py-3">
        <view class="mb-3 flex items-center justify-between">
          <text class="text-lg font-bold">🏢 附近影院</text>
          <text class="text-sm text-gray-500">查看更多 ›</text>
        </view>
        <view class="space-y-3">
          <view v-for="cinema in cinemas" :key="cinema.id" class="rounded-xl bg-gray-50 p-3">
            <text class="text-sm font-bold">{{ cinema.name }}</text>
            <text class="mt-1 block text-xs text-gray-500">{{ cinema.address }}</text>
            <view class="mt-2 flex flex-wrap gap-2">
              <text v-for="tag in cinema.tags" :key="tag" class="rounded-full bg-purple-100 px-2 py-0.5 text-xs text-purple-600">
                {{ tag }}
              </text>
            </view>
            <text class="mt-2 block text-sm text-yellow-500 font-bold">{{ cinema.price }}</text>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<style scoped>
/* 自定义样式 */
</style>

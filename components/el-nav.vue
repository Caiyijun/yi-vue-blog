<template>
    <el-header>
        <div class="nav cl">
            <div class="wrap">
                <div class="logo">
                  <nuxt-link :to="{name:index}">一个奕</nuxt-link>
                </div>
                <ul class="nav-left">
                    <li>
                      <nuxt-link :to="{name:index}">首页</nuxt-link>
                    </li>
                    <li>
                        <a href="#">关于我</a>
                    </li>
                </ul>
            </div>
        </div>
    </el-header>
</template>

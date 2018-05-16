<template>
    <div id = "editor">
        <nav>
            <ol>
                <li v-for="i in [0,1,2,3,4,5]"
                    :class="{active: currentTab === i}"
                    @click="currentTab = i">
                    <svg class="icon">
                    <use :xlink:href="`#icon-${icons[i]}`"></use></svg>
                </li>
            </ol>
        </nav>
        <ol class="panes">
            <li v-for="i in [0,1,2,3,4,5]"
                :class="{active: currentTab === i}">
                Tab {{i}}   
            </li>
        </ol>
    </div>
</template>

<script>
export default {
    data() {
        return{
            currentTab: 0,
            icons: ['shenfenzheng','work0','book','heart','goldcup','phone']
        }
    }
}
</script>


<style lang = "scss">
    #editor{
        border: 1px solid red;
        min-height: 100px;
        display: flex;
        > nav{
            background: #000;
            width: 60px;
        
            > ol > li{
                padding: 12px 0;
                text-align: center;
                > .icon{
                    width: 24px;
                    height: 24px;
                    fill: #fff;
                }
                &.active{
                    background: white;
                    > .icon{
                        fill: black;
                    }
                }
            }
        }
        > .panes > li{
            display: none;
        }
            &.active{
                display: block;
            }
    }
</style>

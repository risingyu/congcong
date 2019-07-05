<template>
    <div class="cinema_body">
        <ul>
            <li>
                <div>
                    <span>西安奥斯卡赛高国际影城</span>
                    <span class="q"><span class="price">25.8</span>元起</span>
                </div>
                <div class="address">
                    <span>经开区凤城五路与未央大道十字西南角赛高街区四层</span>
                    <span>888.8km</span>
                </div>
                <div class="card">
                    <div>小吃</div>
                    <div>影城卡</div>
                </div>
            </li>
            <li>
                <div>
                    <span>西安奥斯卡赛高国际影城</span>
                    <span class="q"><span class="price">25.8</span>元起</span>
                </div>
                <div class="address">
                    <span>经开区凤城五路与未央大道十字西南角赛高街区四层</span>
                    <span>888.8km</span>
                </div>
                <div class="card">
                    <div>小吃</div>
                    <div>影城卡</div>
                </div>
            </li>
            <li>
                <div>
                    <span>西安奥斯卡赛高国际影城</span>
                    <span class="q"><span class="price">25.8</span>元起</span>
                </div>
                <div class="address">
                    <span>经开区凤城五路与未央大道十字西南角赛高街区四层</span>
                    <span>888.8km</span>
                </div>
                <div class="card">
                    <div>小吃</div>
                    <div>影城卡</div>
                </div>
            </li>
            <li>
                <div>
                    <span>西安奥斯卡赛高国际影城</span>
                    <span class="q"><span class="price">25.8</span>元起</span>
                </div>
                <div class="address">
                    <span>经开区凤城五路与未央大道十字西南角赛高街区四层</span>
                    <span>888.8km</span>
                </div>
                <div class="card">
                    <div>小吃</div>
                    <div>影城卡</div>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name : 'CiList'
}
</script>

<style scoped>
#content .cinema_body{ flex: 1; overflow: auto;}
.cinema_body ul{ padding: 20px;}
.cinema_body li{ border-bottom: 1px solid #e6e6e6; margin-bottom: 20px;}
.cinema_body div{ margin-bottom: 10px;}
.cinema_body .q{ font-size: 11px; color: #f03d37;}
.cinema_body .price{ font-size: 18px;}
.cinema_body .address{ font-size: 13px; color: #666;}
.cinema_body .address span:nth-of-type(2){ float: right;}
.cinema_body .card{ display: flex;}
.cinema_body .card div{ padding: 0 3px; height: 15px; line-height: 15px; border-radius: 2px; color: #f90; border: 1px solid #f90;}
.cinema_body .card div.or{ color: #f90; border: 1px solid #f90;}
.cinema_body .card div.bl{ color: #589daf; border: 1px solid #589daf;}
</style>
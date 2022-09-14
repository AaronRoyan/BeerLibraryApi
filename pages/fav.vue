<script setup>
    const { data: fav, refresh } = useAsyncData("fav", () => {
        return $fetch("/api/fav"); 
        refresh();
    });
    const { isDarkMode, toggleDarkMode } = useDarkMode();
    
    const deleteItem = async (id) => {
        alert("Removed from WishList");
        await $fetch(`/api/fav/${id}`, { method: "delete" });
        refresh();
    }
    useHead({
        title: 'WishList',
        meta: [
            {
                name: 'viewport',
            },
        ]
    })
    </script>
    
    <template>
        <!-- {{cart}} -->
        <div class="shopping-cart" :style="isDarkMode ? { backgroundColor: 'rgb(255,255,255)' } : null">
            <!-- Title -->
            <div class="title">
                WishList
            </div>
    
            <!-- Product #1 -->
            <div class="item" v-for="(favItem, index) in fav">
                <div class="buttons">
                    <span class="delete-btn"></span>
                    <span class="like-btn"></span>
                </div>
    
                <div class="image">
                    <img :src=favItem.item.image_url alt="" style="width:25px; padding-top:1em; cursor:pointer" />
                </div>
    
                <div class="description">
                    <span>{{favItem.item.name}}</span>
                    <span>{{favItem.item.first_brewed}}</span>
                    <span>{{favItem.item.tagline}}</span>
                </div>    
              
    
                <div class="total-price">${{favItem.item.ebc}}</div>
                <button type="button" class="remove" @click="() =>deleteItem(cart.id)">x</button>
            </div>
    
            <!-- END OF PRODUCT -->
    
        </div>
    
    </template>
    
    <style>
    @import '~/assets/style/cart.css';
    </style>
    
    
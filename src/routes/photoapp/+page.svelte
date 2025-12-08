<h1>Photoapp </h1>

<p>Denna sida innehåller <strong>fina</strong> bilder </p>

<div class="photos">
    <div class ="image-wrapper">
        <img src = https://picsum.photos/id/70/367/267 alt="Flexbox egenskaper">
    </div>
        <div class ="image-wrapper">

        <img src = https://picsum.photos/id/88/367/267 alt="Flexbox egenskaper">
        </div>  
        <div class ="image-wrapper">

        <img src ="https://picsum.photos/id/93/367/267" alt="Flexbox egenskaper">
  
        </div>

</div>



<style>
    .photos{
        display:flex;
        max-width: 90vw;
        flex-wrap: wrap;
    }
  
    .photos{
        align-items:center;
        justify-content:center;
    }
    
     .image-wrapper{
        flex:1;
        width: 300px;
    
        
     }

     h1{
        text-align: center;
        font-size: 50px;
        margin: 20px;
        color: rgb(83, 1, 47);
     }
     
    .image-wrapper img{ 
        width: 100%;
        margin:10px;
        border-radius: 20px;
        box-shadow: 8px 16px 10px rgba(0,0,0,0.2);
     }

     .image-wrapper:hover { flex:2; }
     
     .image-wrapper:active{transform: scale(0.9); }
</style>


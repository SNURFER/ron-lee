<script>
    export let imageUrl;
  </script>
  
  <style>
    img {
        width: 100%;        
        height: auto;       
        max-width: 300px;   
        border-radius: 12px;
        margin-bottom: 20px;
        object-fit: cover;  
    }
  </style>
  
  <img src={imageUrl} alt="Main Image" />
  
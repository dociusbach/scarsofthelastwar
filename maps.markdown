---
layout: default
title: Maps
permalink: {{ site.baseurl }}/maps/
---

<style>
    body {
        font-family: 'Georgia', serif;
        background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
        color: #e8e8e8;
        line-height: 1.6;
        min-height: 100vh;
    }

    a {
        color: #f4d03f;
        text-decoration: underline;
    }

    a:hover {
        color: #ffd700;
        text-decoration: none;
    }

    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 20px;
    }

    .page-header {
        text-align: center;
        padding: 40px 20px;
        background: linear-gradient(180deg, rgba(139, 69, 19, 0.3) 0%, rgba(0, 0, 0, 0.2) 100%);
        border-bottom: 3px solid #d4af37;
        margin-bottom: 40px;
    }

    .page-header h1 {
        font-size: 2.5em;
        color: #d4af37;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
        margin-bottom: 10px;
    }

    .page-header p {
        color: #c9b68c;
        font-size: 1.2em;
        font-style: italic;
    }

    .back-link {
        display: inline-block;
        margin-bottom: 20px;
        padding: 10px 20px;
        background: rgba(139, 69, 19, 0.3);
        border: 2px solid #8b4513;
        border-radius: 5px;
        text-decoration: none;
        color: #d4af37;
        transition: all 0.3s ease;
    }

    .back-link:hover {
        background: rgba(139, 69, 19, 0.5);
        border-color: #d4af37;
        transform: translateX(-5px);
    }

    .maps-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
        gap: 25px;
        margin-bottom: 40px;
    }

    .map-tile {
        background: rgba(0, 0, 0, 0.4);
        border: 2px solid #8b4513;
        border-radius: 10px;
        overflow: hidden;
        transition: all 0.3s ease;
        cursor: pointer;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
    }

    .map-tile:hover {
        transform: translateY(-5px);
        border-color: #d4af37;
        box-shadow: 0 8px 20px rgba(212, 175, 55, 0.3);
    }

    .map-tile img {
        width: 100%;
        height: 250px;
        object-fit: cover;
        display: block;
    }

    .map-info {
        padding: 15px;
    }

    .map-title {
        color: #d4af37;
        font-size: 1.3em;
        margin-bottom: 5px;
    }

    .map-description {
        color: #c9b68c;
        font-size: 0.95em;
    }

    /* Lightbox Styles */
    .lightbox {
        display: none;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.95);
        backdrop-filter: blur(10px);
        z-index: 1000;
        justify-content: center;
        align-items: center;
        padding: 20px;
    }

    .lightbox.active {
        display: flex;
    }

    .lightbox-content {
        position: relative;
        max-width: 90%;
        max-height: 90%;
        animation: zoomIn 0.3s ease;
    }

    .lightbox-content img {
        max-width: 100%;
        max-height: 90vh;
        object-fit: contain;
        border: 3px solid #d4af37;
        border-radius: 5px;
        box-shadow: 0 0 30px rgba(212, 175, 55, 0.5);
    }

    .lightbox-close {
        position: absolute;
        top: -40px;
        right: 0;
        background: rgba(139, 69, 19, 0.8);
        border: 2px solid #d4af37;
        color: #d4af37;
        font-size: 30px;
        width: 40px;
        height: 40px;
        border-radius: 50%;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: all 0.3s ease;
    }

    .lightbox-close:hover {
        background: rgba(212, 175, 55, 0.9);
        color: #1a1a2e;
        transform: rotate(90deg);
    }

    .lightbox-title {
        position: absolute;
        bottom: -50px;
        left: 0;
        right: 0;
        text-align: center;
        color: #d4af37;
        font-size: 1.5em;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
    }

    @keyframes zoomIn {
        from {
            transform: scale(0.5);
            opacity: 0;
        }
        to {
            transform: scale(1);
            opacity: 1;
        }
    }

    @media (max-width: 768px) {
        .maps-grid {
            grid-template-columns: 1fr;
        }
        
        .lightbox-content {
            max-width: 95%;
        }
    }
</style>

<div class="container">
    <a href="{{ site.baseurl }}/" class="back-link">← Back to Home</a>
    <header class="page-header">
        <h1>🗺️ Campaign Maps</h1>
        <p>Explore the lands of {{ site.data.campaign.campaign_info.name }}</p>
    </header>
    <div class="maps-grid">
{% for map in site.data.campaign.maps %}
        <div class="map-tile" onclick="openLightbox('{{ map.image }}', '{{ map.title }}')">
            <img src="{{ site.baseurl }}/{{ map.image }}" alt="{{ map.title }}">
            <div class="map-info">
                <h3 class="map-title">{{ map.title }}</h3>
{% if map.description %}
                <p class="map-description">{{ map.description }}</p>
{% endif %}
            </div>
        </div>
{% endfor %}
    </div>
</div>

<div class="lightbox" id="lightbox" onclick="closeLightbox(event)">
    <div class="lightbox-content">
        <div class="lightbox-close" onclick="closeLightbox(event)">×</div>
        <img id="lightbox-img" src="" alt="">
        <div class="lightbox-title" id="lightbox-title"></div>
    </div>
</div>

<script>
function openLightbox(imageSrc, title) {
    const lightbox = document.getElementById('lightbox');
    const lightboxImg = document.getElementById('lightbox-img');
    const lightboxTitle = document.getElementById('lightbox-title');
    
    lightboxImg.src = '{{ site.baseurl }}/' + imageSrc;
    lightboxTitle.textContent = title;
    lightbox.classList.add('active');
    document.body.style.overflow = 'hidden';
}

function closeLightbox(event) {
    if (event.target.id === 'lightbox' || event.target.classList.contains('lightbox-close')) {
        const lightbox = document.getElementById('lightbox');
        lightbox.classList.remove('active');
        document.body.style.overflow = 'auto';
    }
}

document.addEventListener('keydown', function(event) {
    if (event.key === 'Escape') {
        const lightbox = document.getElementById('lightbox');
        if (lightbox.classList.contains('active')) {
            lightbox.classList.remove('active');
            document.body.style.overflow = 'auto';
        }
    }
});
</script>
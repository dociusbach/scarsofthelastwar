---
layout: page
title: Characters
permalink: {{ site.baseurl }}/characters/
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

    .characters-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 30px;
        margin-bottom: 40px;
    }

    .character-card {
        background: rgba(0, 0, 0, 0.4);
        border: 2px solid #8b4513;
        border-radius: 10px;
        padding: 25px;
        transition: all 0.3s ease;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
    }

    .character-card:hover {
        transform: translateY(-5px);
        border-color: #d4af37;
        box-shadow: 0 8px 20px rgba(212, 175, 55, 0.3);
    }

    .character-header {
        border-bottom: 2px solid #8b4513;
        padding-bottom: 15px;
        margin-bottom: 15px;
    }

    .character-name {
        font-size: 1.8em;
        color: #d4af37;
        margin-bottom: 5px;
    }

    .character-class {
        font-size: 1.2em;
        color: #c9b68c;
        font-style: italic;
    }

    .character-info {
        margin-top: 15px;
    }

    .info-row {
        display: flex;
        justify-content: space-between;
        padding: 8px 0;
        border-bottom: 1px solid rgba(139, 69, 19, 0.3);
    }

    .info-label {
        color: #d4af37;
        font-weight: bold;
    }

    .info-value {
        color: #e8e8e8;
    }

    .party-count {
        text-align: center;
        padding: 20px;
        background: rgba(212, 175, 55, 0.1);
        border-radius: 8px;
        border-left: 4px solid #d4af37;
        margin-bottom: 30px;
    }

    .party-count h2 {
        color: #d4af37;
        margin-bottom: 5px;
    }

    @media (max-width: 768px) {
        .characters-grid {
            grid-template-columns: 1fr;
        }
    }
</style>
<div class="container">
    <a href="{{ site.baseurl }}/" class="back-link">← Back to Home</a>
    <header class="page-header">
        <h1>👥 The Adventuring Party</h1>
        <p>Heroes of {{ site.data.campaign.campaign_info.name }}</p>
    </header>
    <div class="party-count">
        <h2>Party Size: {{ site.data.campaign.party | size }} Adventurers</h2>
    </div>
    <div class="characters-grid">
{% for character in site.data.campaign.party %}
        <div class="character-card">
            <div class="character-header">
                 <img src="{{ site.baseurl }}/assets/image/{{ character.player_code }}.png" alt="{{ character.name }}">
                <h2 class="character-name">{{ character.name }}</h2>
                <p class="character-class">{{ character.race }} {{ character.class }}</p>
            </div>
            <div class="character-info">
                <div class="info-row">
                    <span class="info-label">Player:</span>
                    <span class="info-value">{{ character.player }}</span>
                </div>
{% if character.level %}
                <div class="info-row">
                    <span class="info-label">Level:</span>
                    <span class="info-value">{{ character.level }}</span>
                </div>
{% endif %}
{% if character.background %}
                <div class="info-row">
                    <span class="info-label">Background:</span>
                    <span class="info-value">{{ character.background }}</span>
                </div>
{% endif %}
            </div>
        </div>
{% endfor %}
    </div>
</div>
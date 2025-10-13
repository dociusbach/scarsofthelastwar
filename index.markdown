---
layout: default
title: Campaign Hub
next_session:
  date: "Saturday, October 13, 2025"
  time: "7:00 PM - 10:00 PM"
  location: "Gaming and Streaming Discord"
---

<style>
    body {
        font-family: 'Georgia', serif;
        background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
        color: #e8e8e8;
        line-height: 1.6;
        min-height: 100vh;
    }

    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 20px;
    }

    header.campaign-header {
        text-align: center;
        padding: 60px 20px;
        background: linear-gradient(180deg, rgba(139, 69, 19, 0.3) 0%, rgba(0, 0, 0, 0.2) 100%);
        border-bottom: 3px solid #d4af37;
        margin-bottom: 40px;
    }

    h1 {
        font-size: 3em;
        color: #d4af37;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
        margin-bottom: 10px;
        letter-spacing: 2px;
    }

    .subtitle {
        font-size: 1.3em;
        color: #c9b68c;
        font-style: italic;
    }

    .welcome-section {
        background: rgba(0, 0, 0, 0.4);
        padding: 30px;
        border-radius: 10px;
        border: 2px solid #8b4513;
        margin-bottom: 40px;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
    }

    .welcome-section h2 {
        color: #d4af37;
        margin-bottom: 15px;
        font-size: 2em;
    }

    .welcome-section p {
        font-size: 1.1em;
        margin-bottom: 15px;
    }

    .nav-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: 25px;
        margin-bottom: 40px;
    }

    .nav-card {
        background: rgba(139, 69, 19, 0.3);
        padding: 30px;
        border-radius: 10px;
        border: 2px solid #8b4513;
        text-align: center;
        transition: all 0.3s ease;
        cursor: pointer;
        text-decoration: none;
        color: inherit;
        display: block;
    }

    .nav-card:hover {
        transform: translateY(-5px);
        border-color: #d4af37;
        box-shadow: 0 8px 20px rgba(212, 175, 55, 0.3);
    }

    .nav-card h3 {
        color: #d4af37;
        font-size: 1.5em;
        margin-bottom: 10px;
    }

    .nav-card p {
        color: #c9b68c;
    }

    .icon {
        font-size: 3em;
        margin-bottom: 15px;
    }

    .session-info {
        background: rgba(212, 175, 55, 0.1);
        padding: 20px;
        border-radius: 8px;
        border-left: 4px solid #d4af37;
        margin-top: 20px;
    }

    .session-info h3 {
        color: #d4af37;
        margin-bottom: 10px;
    }

    footer.campaign-footer {
        text-align: center;
        padding: 30px;
        color: #888;
        border-top: 2px solid #8b4513;
        margin-top: 40px;
    }

    @media (max-width: 768px) {
        h1 {
            font-size: 2em;
        }
        
        .nav-grid {
            grid-template-columns: 1fr;
        }
    }
</style>

<div class="container">
    <header class="campaign-header">
        <h1>⚔️ {{ site.data.campaign.campaign_info.name }} ⚔️</h1>
        <p class="subtitle">{{ site.data.campaign.campaign_info.subtitle }}</p>
    </header>

    <div class="welcome-section">
        <h2>Welcome, Adventurers!</h2>
        <p>
            {{ site.data.campaign.greeting }}
        </p>

        <div class="session-info">
            <h3>📅 Next Session</h3>
            <p><strong>Date:</strong> {{ site.data.campaign.next_session.date }}</p>
            <p><strong>Time:</strong> {{ site.data.campaign.next_session.time }}</p>
            <p><strong>Location:</strong> {{ site.data.campaign.next_session.location }}</p>
        </div>
    </div>

    <div class="nav-grid">
        <a href="{{ site.baseurl }}/characters" class="nav-card">
            <div class="icon">👥</div>
            <h3>Characters</h3>
            <p>Meet the heroes of our tale and track their progress</p>
        </a>

        <a href="/sessions" class="nav-card">
            <div class="icon">📖</div>
            <h3>Session Notes</h3>
            <p>Review past adventures and recap what happened</p>
        </a>

        <a href="/world" class="nav-card">
            <div class="icon">🗺️</div>
            <h3>World & Lore</h3>
            <p>Explore locations, NPCs, and the history of our world</p>
        </a>

        <a href="/rules" class="nav-card">
            <div class="icon">📜</div>
            <h3>House Rules</h3>
            <p>Campaign-specific rules and guidelines</p>
        </a>

        <a href="/resources" class="nav-card">
            <div class="icon">🎲</div>
            <h3>Resources</h3>
            <p>Useful tools, character sheets, and references</p>
        </a>

        <a href="/gallery" class="nav-card">
            <div class="icon">🖼️</div>
            <h3>Gallery</h3>
            <p>Maps, art, and visual inspiration</p>
        </a>
    </div>

    <footer class="campaign-footer">
        <p>May your rolls be high and your adventures legendary!</p>
        <p><em>Last Updated: {{ site.time | date: "%B %d, %Y" }}</em></p>
    </footer>
</div>
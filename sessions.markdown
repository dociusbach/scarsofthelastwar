---
layout: page
title: Session Notes
permalink: {{ site.baseurl }}/sessions/
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

    .sessions-list {
        display: flex;
        flex-direction: column;
        gap: 30px;
        margin-bottom: 40px;
    }

    .session-card {
        background: rgba(0, 0, 0, 0.4);
        border: 2px solid #8b4513;
        border-radius: 10px;
        padding: 30px;
        transition: all 0.3s ease;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
    }

    .session-card:hover {
        transform: translateY(-3px);
        border-color: #d4af37;
        box-shadow: 0 8px 20px rgba(212, 175, 55, 0.3);
    }

    .session-header {
        border-bottom: 2px solid #8b4513;
        padding-bottom: 15px;
        margin-bottom: 20px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
        gap: 10px;
    }

    .session-number {
        font-size: 0.9em;
        color: #d4af37;
        background: rgba(139, 69, 19, 0.3);
        padding: 5px 15px;
        border-radius: 20px;
        border: 1px solid #8b4513;
    }

    .session-title {
        font-size: 2em;
        color: #d4af37;
        margin: 10px 0;
        flex: 1 1 100%;
    }

    .session-date {
        color: #c9b68c;
        font-style: italic;
    }

    .session-meta {
        display: flex;
        gap: 20px;
        margin-bottom: 15px;
        flex-wrap: wrap;
    }

    .meta-item {
        color: #c9b68c;
        font-size: 0.95em;
    }

    .meta-label {
        color: #d4af37;
        font-weight: bold;
    }

    .session-excerpt {
        color: #e8e8e8;
        margin-bottom: 20px;
        line-height: 1.8;
    }

    .read-more {
        display: inline-block;
        padding: 10px 20px;
        background: rgba(139, 69, 19, 0.5);
        border: 2px solid #8b4513;
        border-radius: 5px;
        color: #d4af37;
        text-decoration: none;
        transition: all 0.3s ease;
    }

    .read-more:hover {
        background: rgba(212, 175, 55, 0.3);
        border-color: #d4af37;
        transform: translateX(5px);
    }

    .no-sessions {
        text-align: center;
        padding: 60px 20px;
        background: rgba(0, 0, 0, 0.4);
        border: 2px solid #8b4513;
        border-radius: 10px;
    }

    .no-sessions h2 {
        color: #d4af37;
        font-size: 1.8em;
        margin-bottom: 15px;
    }

    .no-sessions p {
        color: #c9b68c;
    }

    @media (max-width: 768px) {
        .session-header {
            flex-direction: column;
            align-items: flex-start;
        }
        
        .session-title {
            font-size: 1.5em;
        }
    }
</style>

<div class="container">
    <a href="{{ site.baseurl }}/" class="back-link">← Back to Home</a>
    <header class="page-header">
        <h1>📖 Session Notes</h1>
        <p>The chronicles of {{ site.data.campaign.campaign_info.name }}</p>
    </header>
    <div class="sessions-list">
{% assign sorted_sessions = site.sessions | sort: 'session_number' | reverse %}
{% if sorted_sessions.size > 0 %}
{% for session in sorted_sessions %}
        <article class="session-card">
            <div class="session-header">
                <span class="session-number">Session {{ session.session_number }}</span>
                <span class="session-date">{{ session.date | date: "%B %d, %Y" }}</span>
                <h2 class="session-title">{{ session.title }}</h2>
            </div>
{% if session.location or session.dm %}
            <div class="session-meta">
{% if session.location %}
                <span class="meta-item"><span class="meta-label">Location:</span> {{ session.location }}</span>
{% endif %}
{% if session.dm %}
                <span class="meta-item"><span class="meta-label">DM:</span> {{ session.dm }}</span>
{% endif %}
            </div>
{% endif %}
            <div class="session-excerpt">
                {{ session.excerpt | strip_html | truncatewords: 50 }}
            </div>
            <a href="{{ session.url | relative_url }}" class="read-more">Read Full Session →</a>
        </article>
{% endfor %}
{% else %}
        <div class="no-sessions">
            <h2>No Sessions Yet</h2>
            <p>The adventure is just beginning! Session notes will appear here once your first session is recorded.</p>
        </div>
{% endif %}
    </div>
</div>
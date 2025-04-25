
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>StreamVault - Your Media Server</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <!-- Sidebar -->
        <div class="sidebar">
            <div class="sidebar-header">
                <div class="logo" id="home-logo">
                    <span class="logo-icon">🎬</span>
                    <span class="logo-text">StreamVault</span>
                </div>
            </div>
            <ul class="nav-menu">
                <li class="nav-item">
                    <a href="#" class="nav-link active" data-section="home">
                        <span class="nav-icon">🏠</span>
                        <span class="nav-text">Home</span>
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link" data-section="movies">
                        <span class="nav-icon">🎞️</span>
                        <span class="nav-text">Movies</span>
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link" data-section="shows">
                        <span class="nav-icon">📺</span>
                        <span class="nav-text">TV Shows</span>
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link" data-section="music">
                        <span class="nav-icon">🎵</span>
                        <span class="nav-text">Music</span>
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link" data-section="photos">
                        <span class="nav-icon">📷</span>
                        <span class="nav-text">Photos</span>
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link" data-section="library">
                        <span class="nav-icon">📚</span>
                        <span class="nav-text">Library</span>
                    </a>
                </li>
                <li class="nav-item">
                    <a href="#" class="nav-link" data-section="settings">
                        <span class="nav-icon">⚙️</span>
                        <span class="nav-text">Settings</span>
                    </a>
                </li>
            </ul>
        </div>

        <!-- Main Content -->
        <div class="main-content">
            <div class="header">
                <div class="search-bar">
                    <span class="search-icon">🔍</span>
                    <input type="text" placeholder="Search your media...">
                </div>
                <div class="user-actions">
                    <span class="action-icon" id="add-media">➕</span>
                    <span class="action-icon" id="notifications">🔔</span>
                    <span class="action-icon" id="user-profile">👤</span>
                </div>
            </div>

            <!-- Home Section -->
            <div id="home-section" class="content-section">
                <h2 class="section-title">Continue Watching</h2>
                <div class="media-grid" id="continue-watching">
                    <!-- Dynamically populated -->
                </div>

                <h2 class="section-title">Recently Added</h2>
                <div class="media-grid" id="recently-added">
                    <!-- Dynamically populated -->
                </div>
            </div>

            <!-- Movies Section -->
            <div id="movies-section" class="content-section" style="display: none;">
                <h2 class="section-title">Movies</h2>
                <div class="filter-bar">
                    <select class="filter-select">
                        <option value="all">All Movies</option>
                        <option value="action">Action</option>
                        <option value="comedy">Comedy</option>
                        <option value="drama">Drama</option>
                        <option value="scifi">Sci-Fi</option>
                    </select>
                    <select class="filter-select">
                        <option value="recent">Recently Added</option>
                        <option value="alphabetical">Alphabetical</option>
                        <option value="year">Release Year</option>
                    </select>
                </div>
                <div class="media-grid" id="movies-grid">
                    <!-- Will be populated with movies -->
                </div>
            </div>

            <!-- TV Shows Section -->
            <div id="shows-section" class="content-section" style="display: none;">
                <h2 class="section-title">TV Shows</h2>
                <div class="filter-bar">
                    <select class="filter-select">
                        <option value="all">All Shows</option>
                        <option value="drama">Drama</option>
                        <option value="comedy">Comedy</option>
                        <option value="scifi">Sci-Fi</option>
                        <option value="documentary">Documentary</option>
                    </select>
                    <select class="filter-select">
                        <option value="recent">Recently Added</option>
                        <option value="alphabetical">Alphabetical</option>
                        <option value="year">Release Year</option>
                    </select>
                </div>
                <div class="media-grid" id="shows-grid">
                    <!-- Will be populated with shows -->
                </div>
            </div>

            <!-- Music Section -->
            <div id="music-section" class="content-section" style="display: none;">
                <h2 class="section-title">Music</h2>
                <div class="filter-bar">
                    <select class="filter-select">
                        <option value="all">All Music</option>
                        <option value="albums">Albums</option>
                        <option value="artists">Artists</option>
                        <option value="playlists">Playlists</option>
                    </select>
                    <select class="filter-select">
                        <option value="recent">Recently Added</option>
                        <option value="alphabetical">Alphabetical</option>
                        <option value="most-played">Most Played</option>
                    </select>
                </div>
                <div class="media-grid" id="music-grid">
                    <!-- Will be populated with music -->
                </div>
            </div>

            <!-- Photos Section -->
            <div id="photos-section" class="content-section" style="display: none;">
                <h2 class="section-title">Photo Albums</h2>
                <div class="filter-bar">
                    <select class="filter-select">
                        <option value="all">All Albums</option>
                        <option value="people">People</option>
                        <option value="places">Places</option>
                        <option value="events">Events</option>
                    </select>
                    <select class="filter-select">
                        <option value="recent">Recently Added</option>
                        <option value="alphabetical">Alphabetical</option>
                        <option value="oldest">Oldest First</option>
                    </select>
                </div>
                <div class="media-grid" id="photos-grid">
                    <!-- Will be populated with photo albums -->
                </div>
            </div>

            <!-- Library Section -->
            <div id="library-section" class="content-section" style="display: none;">
                <h2 class="section-title">Media Libraries</h2>
                <div class="library-list">
                    <div class="library-item">
                        <div class="library-icon">🎬</div>
                        <div class="library-info">
                            <h3>Movies</h3>
                            <p>Path: /media/movies</p>
                            <p>Items: 42</p>
                        </div>
                        <div class="library-actions">
                            <button class="library-btn">Scan</button>
                            <button class="library-btn">Edit</button>
                        </div>
                    </div>
                    <div class="library-item">
                        <div class="library-icon">📺</div>
                        <div class="library-info">
                            <h3>TV Shows</h3>
                            <p>Path: /media/tvshows</p>
                            <p>Items: 15</p>
                        </div>
                        <div class="library-actions">
                            <button class="library-btn">Scan</button>
                            <button class="library-btn">Edit</button>
                        </div>
                    </div>
                    <div class="library-item">
                        <div class="library-icon">🎵</div>
                        <div class="library-info">
                            <h3>Music</h3>
                            <p>Path: /media/music</p>
                            <p>Items: 128</p>
                        </div>
                        <div class="library-actions">
                            <button class="library-btn">Scan</button>
                            <button class="library-btn">Edit</button>
                        </div>
                    </div>
                    <div class="library-item">
                        <div class="library-icon">📷</div>
                        <div class="library-info">
                            <h3>Photos</h3>
                            <p>Path: /media/photos</p>
                            <p>Items: 256</p>
                        </div>
                        <div class="library-actions">
                            <button class="library-btn">Scan</button>
                            <button class="library-btn">Edit</button>
                        </div>
                    </div>
                </div>
                <button class="add-library-btn">+ Add New Library</button>
            </div>

            <!-- Settings Section -->
            <div id="settings-section" class="content-section" style="display: none;">
                <h2 class="section-title">Settings</h2>
                <div class="settings-container">
                    <div class="settings-panel">
                        <h3 class="settings-panel-title">General Settings</h3>
                        <div class="settings-form">
                            <div class="form-group">
                                <label class="form-label">Server Name</label>
                                <input type="text" class="form-input" value="StreamVault Server">
                            </div>
                            <div class="form-group">
                                <label class="form-label">Theme</label>
                                <select class="form-input">
                                    <option value="dark">Dark Theme</option>
                                    <option value="light">Light Theme</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Language</label>
                                <select class="form-input">
                                    <option value="en">English</option>
                                    <option value="es">Spanish</option>
                                    <option value="fr">French</option>
                                </select>
                            </div>
                        </div>
                    </div>
                    <div class="settings-panel">
                        <h3 class="settings-panel-title">Playback Settings</h3>
                        <div class="settings-form">
                            <div class="form-group">
                                <label class="form-label">Default Quality</label>
                                <select class="form-input">
                                    <option value="auto">Auto</option>
                                    <option value="1080p">1080p</option>
                                    <option value="720p">720p</option>
                                    <option value="480p">480p</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Auto Play Next Episode</label>
                                <div class="toggle-switch">
                                    <input type="checkbox" id="autoplay" checked>
                                    <label for="autoplay"></label>
                                </div>
                            </div>
                            <div class="form-group">
                                <label class="form-label">Enable Subtitles by Default</label>
                                <div class="toggle-switch">
                                    <input type="checkbox" id="subtitles">
                                    <label for="subtitles"></label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Media Player -->
            <div id="media-player" class="player-container">
                <div class="player-header">
                    <h3 class="player-title">Media Title</h3>
                    <span class="player-close">×</span>
                </div>
                <div class="video-player">
                    <video id="video" width="100%" height="100%" controls>
                        <source src="" type="video/mp4">
                        Your browser does not support the video tag.
                    </video>
                </div>
                <div class="player-controls">
                    <div class="control-group">
                        <button class="control-btn">⏮️</button>
                        <button class="control-btn" id="play-pause">⏸️</button>
                        <button class="control-btn">⏭️</button>
                    </div>
                    <div class="progress-bar">
                        <div class="progress"></div>
                    </div>
                    <div class="control-group">
                        <button class="control-btn">🔊</button>
                        <button class="control-btn">⚙️</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Add Media Modal -->
    <div class="modal" id="add-media-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Add Media</h3>
                <span class="modal-close">×</span>
            </div>
            <form id="add-media-form">
                <div class="form-group">
                    <label class="form-label">Media Type</label>
                    <select class="form-input" id="media-type">
                        <option value="movie">Movie</option>
                        <option value="show">TV Show</option>
                        <option value="music">Music</option>
                        <option value="photo">Photo</option>
                    </select>
                </div>
                <div class="form-group">
                    <label class="form-label">Title</label>
                    <input type="text" class="form-input" id="media-title" required>
                </div>
                <div class="form-group">
                    <label class="form-label">File Path</label>
                    <input type="text" class="form-input" id="media-path" required>
                </div>
                <div class="form-group">
                    <label class="form-label">Thumbnail URL</label>
                    <input type="text" class="form-input" id="media-thumbnail">
                </div>
                <div class="form-group">
                    <label class="form-label">Year</label>
                    <input type="number" class="form-input" id="media-year">
                </div>
                <button type="submit" class="form-submit">Add Media</button>
            </form>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>
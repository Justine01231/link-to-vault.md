// Database simulation
class MediaDatabase {
    constructor() {
        this.mediaItems = JSON.parse(localStorage.getItem('mediaItems')) || [];
        this.continueWatching = JSON.parse(localStorage.getItem('continueWatching')) || [];
        this.recentlyAdded = [];
        this.loadDefaultMedia();
        this.updateRecentlyAdded();
    }

    loadDefaultMedia() {
        if (this.mediaItems.length === 0) {
            // Add default media if database is empty
            const defaultMedia = [
                {
                    id: 1,
                    title: "Big Buck Bunny",
                    type: "movie",
                    year: 2008,
                    path: "https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4",
                    thumbnail: "/api/placeholder/180/250",
                    dateAdded: new Date(2023, 3, 15).getTime(),
                    progress: 0.3
                },
                {
                    id: 2,
                    title: "Nature Documentary",
                    type: "movie",
                    year: 2022,
                    path: "https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4",
                    thumbnail: "/api/placeholder/180/250",
                    dateAdded: new Date(2023, 4, 10).getTime(),
                    progress: 0.7
                },
                {
                    id: 3,
                    title: "Space Exploration",
                    type: "show",
                    year: 2021,
                    path: "https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/TearsOfSteel.mp4",
                    thumbnail: "/api/placeholder/180/250",
                    dateAdded: new Date(2023, 5, 5).getTime(),
                    progress: 0.5
                },
                {
                    id: 4,
                    title: "Adventure Time",
                    type: "show",
                    year: 2019,
                    path: "https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/Sintel.mp4",
                    thumbnail: "/api/placeholder/180/250",
                    dateAdded: new Date(2023, 6, 20).getTime(),
                    progress: 0.1
                },
                {
                    id: 5,
                    title: "The Matrix",
                    type: "movie",
                    year: 1999,
                    path: "https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4",
                    thumbnail: "/api/placeholder/180/250",
                    dateAdded: new Date(2023, 7, 5).getTime(),
                    progress: 0
                },
                {
                    id: 6,
                    title: "Inception",
                    type: "movie",
                    year: 2010,
                    path: "https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4",
                    thumbnail: "/api/placeholder/180/250",
                    dateAdded: new Date(2023, 8, 12).getTime(),
                    progress: 0
                },
                {
                    id: 7,
                    title: "Breaking Bad",
                    type: "show",
                    year: 2008,
                    path: "https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/TearsOfSteel.mp4",
                    thumbnail: "/api/placeholder/180/250",
                    dateAdded: new Date(2023, 9, 8).getTime(),
                    progress: 0
                },
                {
                    id: 8,
                    title: "Classical Collection",
                    type: "music",
                    year: 2021,
                    path: "https://example.com/music/classical.mp3",
                    thumbnail: "/api/placeholder/180/250",
                    dateAdded: new Date(2023, 10, 15).getTime(),
                    progress: 0
                },
                {
                    id: 9,
                    title: "Jazz Favorites",
                    type: "music",
                    year: 2022,
                    path: "https://example.com/music/jazz.mp3",
                    thumbnail: "/api/placeholder/180/250",
                    dateAdded: new Date(2023, 11, 20).getTime(),
                    progress: 0
                },
                {
                    id: 10,
                    title: "Vacation Photos",
                    type: "photo",
                    year: 2023,
                    path: "https://example.com/photos/vacation",
                    thumbnail: "/api/placeholder/180/250",
                    dateAdded: new Date(2024, 0, 5).getTime(),
                    progress: 0
                }
            ];
            
            this.mediaItems = defaultMedia;
            this.continueWatching = [1, 2, 3];
            this.saveToStorage();
        }
    }

    updateRecentlyAdded() {
        // Get media items sorted by date added (most recent first)
        this.recentlyAdded = [...this.mediaItems]
            .sort((a, b) => b.dateAdded - a.dateAdded)
            .slice(0, 6)
            .map(item => item.id);
    }

    getMediaByType(type) {
        return this.mediaItems.filter(item => item.type === type);
    }

    addMedia(mediaItem) {
        const id = this.mediaItems.length > 0 ? 
            Math.max(...this.mediaItems.map(item => item.id)) + 1 : 1;
        
        const newMedia = {
            id,
            ...mediaItem,
            dateAdded: Date.now(),
            progress: 0
        };
        
        this.mediaItems.push(newMedia);
        this.updateRecentlyAdded();
        this.saveToStorage();
        return newMedia;
    }

    getMediaById(id) {
        return this.mediaItems.find(item => item.id === id);
    }

    updateMediaProgress(id, progress) {
        const mediaIndex = this.mediaItems.findIndex(item => item.id === id);
        if (mediaIndex !== -1) {
            this.mediaItems[mediaIndex].progress = progress;
            
            // Add to continue watching if not already there
            if (!this.continueWatching.includes(id)) {
                this.continueWatching.unshift(id);
                this.continueWatching = this.continueWatching.slice(0, 6); // Keep only 6 items
            }
            
            this.saveToStorage();
        }
    }

    getContinueWatching() {
        return this.continueWatching.map(id => this.getMediaById(id)).filter(Boolean);
    }

    getRecentlyAdded() {
        return this.recentlyAdded.map(id => this.getMediaById(id)).filter(Boolean);
    }

    saveToStorage() {
        localStorage.setItem('mediaItems', JSON.stringify(this.mediaItems));
        localStorage.setItem('continueWatching', JSON.stringify(this.continueWatching));
    }
}

// Initialize the application
document.addEventListener('DOMContentLoaded', function() {
    const db = new MediaDatabase();
    const continueWatchingGrid = document.getElementById('continue-watching');
    const recentlyAddedGrid = document.getElementById('recently-added');
    const moviesGrid = document.getElementById('movies-grid');
    const showsGrid = document.getElementById('shows-grid');
    const musicGrid = document.getElementById('music-grid');
    const photosGrid = document.getElementById('photos-grid');
    const mediaPlayer = document.getElementById('media-player');
    const video = document.getElementById('video');
    const playerTitle = document.querySelector('.player-title');
    const playerCloseBtn = document.querySelector('.player-close');
    const playPauseBtn = document.getElementById('play-pause');
    const addMediaBtn = document.getElementById('add-media');
    const addMediaModal = document.getElementById('add-media-modal');
    const modalCloseBtn = document.querySelector('.modal-close');
    const addMediaForm = document.getElementById('add-media-form');
    const homeLogo = document.getElementById('home-logo');

    // Render continue watching section
    function renderContinueWatching() {
        continueWatchingGrid.innerHTML = '';
        const continueItems = db.getContinueWatching();
        
        continueItems.forEach(item => {
            const card = createMediaCard(item);
            continueWatchingGrid.appendChild(card);
        });
    }

    // Render recently added section
    function renderRecentlyAdded() {
        recentlyAddedGrid.innerHTML = '';
        const recentItems = db.getRecentlyAdded();
        
        recentItems.forEach(item => {
            const card = createMediaCard(item);
            recentlyAddedGrid.appendChild(card);
        });
    }

    // Render media by type
    function renderMediaByType(type, container) {
        container.innerHTML = '';
        const items = db.getMediaByType(type);
        
        if (items.length === 0) {
            const emptyMessage = document.createElement('div');
            emptyMessage.className = 'empty-message';
            emptyMessage.textContent = `No ${type} items found. Add some media to get started.`;
            container.appendChild(emptyMessage);
            return;
        }
        
        items.forEach(item => {
            const card = createMediaCard(item);
            container.appendChild(card);
        });
    }

    // Create media card element
    function createMediaCard(media) {
        const card = document.createElement('div');
        card.className = 'media-card';
        card.dataset.id = media.id;
        
        const thumbnail = document.createElement('img');
        thumbnail.className = 'media-thumbnail';
        thumbnail.src = media.thumbnail;
        thumbnail.alt = media.title;
        
        const info = document.createElement('div');
        info.className = 'media-info';
        
        const title = document.createElement('h4');
        title.className = 'media-title';
        title.textContent = media.title;
        
        const meta = document.createElement('div');
        meta.className = 'media-meta';
        
        const year = document.createElement('span');
        year.textContent = media.year;
        
        const type = document.createElement('span');
        type.textContent = media.type.charAt(0).toUpperCase() + media.type.slice(1);
        
        meta.appendChild(year);
        meta.appendChild(type);
        
        info.appendChild(title);
        info.appendChild(meta);
        
        card.appendChild(thumbnail);
        card.appendChild(info);
        
        // Add progress bar if there's progress
        if (media.progress > 0) {
            const progressContainer = document.createElement('div');
            progressContainer.className = 'progress-bar';
            progressContainer.style.margin = '0';
            progressContainer.style.height = '3px';
            
            const progress = document.createElement('div');
            progress.className = 'progress';
            progress.style.width = `${media.progress * 100}%`;
            
            progressContainer.appendChild(progress);
            info.appendChild(progressContainer);
        }
        
        // Add click event to play the media
        card.addEventListener('click', () => {
            playMedia(media);
        });
        
        return card;
    }

    // Play media function
    function playMedia(media) {
        playerTitle.textContent = media.title;
        video.src = media.path;
        video.currentTime = media.progress * video.duration || 0;
        mediaPlayer.style.display = 'block';
        video.play();
        
        // Update progress as the video plays
        video.addEventListener('timeupdate', () => {
            const progress = video.currentTime / video.duration;
            document.querySelector('#media-player .progress').style.width = `${progress * 100}%`;
            db.updateMediaProgress(media.id, progress);
        });
    }

    // Close player function
    playerCloseBtn.addEventListener('click', () => {
        video.pause();
        mediaPlayer.style.display = 'none';
    });

    // Play/Pause button
    playPauseBtn.addEventListener('click', () => {
        if (video.paused) {
            video.play();
            playPauseBtn.textContent = '⏸️';
        } else {
            video.pause();
            playPauseBtn.textContent = '▶️';
        }
    });

    // Add media button
    addMediaBtn.addEventListener('click', () => {
        addMediaModal.style.display = 'flex';
    });

    // Close modal button
    modalCloseBtn.addEventListener('click', () => {
        addMediaModal.style.display = 'none';
    });

    // Close modal when clicking outside
    addMediaModal.addEventListener('click', (e) => {
        if (e.target === addMediaModal) {
            addMediaModal.style.display = 'none';
        }
    });

    // Submit form
    addMediaForm.addEventListener('submit', (e) => {
        e.preventDefault();
        
        const newMedia = {
            title: document.getElementById('media-title').value,
            type: document.getElementById('media-type').value,
            path: document.getElementById('media-path').value,
            thumbnail: document.getElementById('media-thumbnail').value || "/api/placeholder/180/250",
            year: parseInt(document.getElementById('media-year').value) || new Date().getFullYear()
        };
        
        db.addMedia(newMedia);
        addMediaForm.reset();
        addMediaModal.style.display = 'none';
        
        // Refresh the current view
        const activeSection = document.querySelector('.nav-link.active').getAttribute('data-section');
        navigateToSection(activeSection);
    });

    // Logo click - go home
    homeLogo.addEventListener('click', () => {
        navigateToSection('home');
        document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
        document.querySelector('.nav-link[data-section="home"]').classList.add('active');
    });

    // Navigation function
    function navigateToSection(section) {
        // Hide all sections
        document.querySelectorAll('.content-section').forEach(s => {
            s.style.display = 'none';
        });
        
        // Show the selected section
        const selectedSection = document.getElementById(`${section}-section`);
        if (selectedSection) {
            selectedSection.style.display = 'block';
            
            // Load section-specific content
            switch(section) {
                case 'home':
                    renderContinueWatching();
                    renderRecentlyAdded();
                    break;
                case 'movies':
                    renderMediaByType('movie', moviesGrid);
                    break;
                case 'shows':
                    renderMediaByType('show', showsGrid);
                    break;
                case 'music':
                    renderMediaByType('music', musicGrid);
                    break;
                case 'photos':
                    renderMediaByType('photo', photosGrid);
                    break;
                // Library and settings don't need data loading
            }
        }
    }

    // Navigation
    document.querySelectorAll('.nav-link').forEach(link => {
        link.addEventListener('click', (e) => {
            e.preventDefault();
            
            // Remove active class from all links
            document.querySelector
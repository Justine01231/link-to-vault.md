:root {

--primary-color: #007bff;

--secondary-color: #6c757d;

--dark-bg: #1a1a1a;

--medium-bg: #2d2d2d;

--light-bg: #3d3d3d;

--text-color: #f8f9fa;

--border-radius: 8px;

}

  

* {

margin: 0;

padding: 0;

box-sizing: border-box;

font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;

}

  

body {

background-color: var(--dark-bg);

color: var(--text-color);

line-height: 1.6;

}

  

.container {

display: flex;

min-height: 100vh;

}

  

/* Sidebar */

.sidebar {

width: 250px;

background-color: var(--medium-bg);

padding: 20px 0;

height: 100vh;

position: fixed;

overflow-y: auto;

}

  

.sidebar-header {

padding: 0 20px 20px;

}

  

.logo {

color: var(--primary-color);

font-size: 24px;

font-weight: bold;

display: flex;

align-items: center;

margin-bottom: 20px;

}

  

.logo-icon {

margin-right: 10px;

font-size: 28px;

}

  

.nav-menu {

list-style: none;

}

  

.nav-item {

margin-bottom: 5px;

}

  

.nav-link {

display: flex;

align-items: center;

padding: 10px 20px;

color: var(--text-color);

text-decoration: none;

transition: all 0.3s;

}

  

.nav-link:hover, .nav-link.active {

background-color: var(--light-bg);

}

  

.nav-icon {

margin-right: 10px;

font-size: 18px;

}

  

/* Main Content */

.main-content {

flex: 1;

margin-left: 250px;

padding: 20px;

}

  

.header {

display: flex;

justify-content: space-between;

align-items: center;

margin-bottom: 30px;

}

  

.search-bar {

position: relative;

width: 40%;

}

  

.search-bar input {

width: 100%;

padding: 10px 15px;

padding-left: 40px;

border-radius: var(--border-radius);

border: none;

background-color: var(--light-bg);

color: var(--text-color);

}

  

.search-icon {

position: absolute;

left: 15px;

top: 50%;

transform: translateY(-50%);

color: var(--secondary-color);

}

  

.user-actions {

display: flex;

align-items: center;

}

  

.action-icon {

margin-left: 15px;

cursor: pointer;

font-size: 20px;

}

  

/* Media Grid */

.section-title {

margin: 30px 0 20px;

font-size: 22px;

}

  

.media-grid {

display: grid;

grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));

gap: 20px;

margin-bottom: 30px;

}

  

.media-card {

background-color: var(--medium-bg);

border-radius: var(--border-radius);

overflow: hidden;

transition: transform 0.3s;

cursor: pointer;

}

  

.media-card:hover {

transform: scale(1.05);

}

  

.media-thumbnail {

width: 100%;

height: 250px;

object-fit: cover;

}

  

.media-info {

padding: 15px;

}

  

.media-title {

font-size: 16px;

font-weight: 500;

margin-bottom: 5px;

}

  

.media-meta {

font-size: 14px;

color: var(--secondary-color);

display: flex;

justify-content: space-between;

}

  

/* Media Player */

.player-container {

background-color: var(--medium-bg);

border-radius: var(--border-radius);

padding: 20px;

margin-top: 20px;

display: none;

}

  

.player-header {

display: flex;

justify-content: space-between;

margin-bottom: 20px;

}

  

.player-title {

font-size: 20px;

font-weight: 500;

}

  

.player-close {

cursor: pointer;

font-size: 24px;

}

  

.video-player {

width: 100%;

border-radius: var(--border-radius);

background-color: black;

height: 500px;

}

  

.player-controls {

display: flex;

justify-content: space-between;

align-items: center;

margin-top: 20px;

}

  

.control-group {

display: flex;

align-items: center;

}

  

.control-btn {

background: none;

border: none;

color: var(--text-color);

cursor: pointer;

font-size: 18px;

margin-right: 15px;

}

  

.progress-bar {

flex-grow: 1;

height: 5px;

background-color: var(--light-bg);

border-radius: 5px;

margin: 0 20px;

position: relative;

}

  

.progress {

position: absolute;

height: 100%;

background-color: var(--primary-color);

border-radius: 5px;

width: 30%;

}

  

/* Modal */

.modal {

display: none;

position: fixed;

top: 0;

left: 0;

width: 100%;

height: 100%;

background-color: rgba(0, 0, 0, 0.7);

z-index: 100;

justify-content: center;

align-items: center;

}

  

.modal-content {

background-color: var(--medium-bg);

border-radius: var(--border-radius);

padding: 20px;

width: 500px;

max-width: 90%;

}

  

.modal-header {

display: flex;

justify-content: space-between;

align-items: center;

margin-bottom: 20px;

}

  

.modal-title {

font-size: 20px;

font-weight: 500;

}

  

.modal-close {

cursor: pointer;

font-size: 24px;

}

  

.form-group {

margin-bottom: 15px;

}

  

.form-label {

display: block;

margin-bottom: 5px;

}

  

.form-input {

width: 100%;

padding: 10px;

border-radius: var(--border-radius);

border: 1px solid var(--light-bg);

background-color: var(--dark-bg);

color: var(--text-color);

}

  

.form-submit {

background-color: var(--primary-color);

color: white;

border: none;

padding: 10px 15px;

border-radius: var(--border-radius);

cursor: pointer;

margin-top: 10px;

}

  

/* Responsive */

@media (max-width: 768px) {

.sidebar {

width: 70px;

padding: 10px 0;

}

  

.sidebar-header {

padding: 0 10px 10px;

}

  

.logo-text, .nav-text {

display: none;

}

  

.nav-link {

padding: 10px;

justify-content: center;

}

  

.nav-icon {

margin-right: 0;

}

  

.main-content {

margin-left: 70px;

}

}
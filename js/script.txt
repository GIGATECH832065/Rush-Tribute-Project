// Typewriter Effect
const typewriterText = [
    "Rush",
    "Fly By Night",
    "Caress of Steel",
    "2112",
    "A Farwell to Kings",
    "Hemispheres",
    "Permanent Waves",
    "Moving Pictures",
    "Grace Under Pressure",
    "Power Windows",
    "Hold Your Fire",
    "Presto",
    "Roll the Bones",
    "Counterparts",
    "Test for Echo",
    "Vapor Trails",
    "Snakes & Arrows",
    "Clockwork Angels"
];
let index = 0;
let charIndex = 0;
const typewriterElement = document.getElementById('typewriter-text');

function type() {
    if (charIndex < typewriterText[index].length) {
        typewriterElement.textContent += typewriterText[index].charAt(charIndex);
        charIndex++;
        setTimeout(type, 100);
    } else {
        setTimeout(erase, 2000);
    }
}

function erase() {
    if (charIndex > 0) {
        typewriterElement.textContent = typewriterText[index].substring(0, charIndex - 1);
        charIndex--;
        setTimeout(erase, 50);
    } else {
        index = (index + 1) % typewriterText.length;
        setTimeout(type, 500);
    }
}

// Light/Dark Mode Toggle
const modeSwitch = document.getElementById('mode-switch');
if (modeSwitch) {
    modeSwitch.addEventListener('change', () => {
        document.body.classList.toggle('light-mode');
    });
}

// Audio Toggle for Hero Video
const video = document.querySelector('.hero-video');
const audioToggle = document.querySelector('.audio-toggle');
if (video && audioToggle) {
    audioToggle.addEventListener('click', () => {
        video.muted = !video.muted;
        audioToggle.textContent = video.muted ? 'Toggle Audio' : 'Mute Audio';
    });
}

// Video Scroll Functionality for videos.html
function scrollVideos(direction) {
    const scrollContainer = document.querySelector('.video-scroll');
    if (scrollContainer) {
        const scrollAmount = 800; // Adjust based on video-box width
        const currentScroll = scrollContainer.scrollLeft;
        let newScroll;

        if (direction === 'left') {
            newScroll = currentScroll - scrollAmount;
        } else if (direction === 'right') {
            newScroll = currentScroll + scrollAmount;
        }

        scrollContainer.scrollTo({
            left: newScroll,
            behavior: 'smooth'
        });

        console.log(`Scrolling ${direction}: ${newScroll}`); // Debug log
    } else {
        console.error('Scroll container not found'); // Debug log
    }
}

// Start typewriter effect after DOM is loaded
document.addEventListener('DOMContentLoaded', () => {
    if (typewriterElement) {
        type();
    }
    console.log('DOM fully loaded'); // Debug log
});
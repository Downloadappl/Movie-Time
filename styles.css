const apiKey = '481a4ece'; // مفتاح API الخاص بك من OMDb

function fetchMoviesByType(type, containerId) {
    fetch(`https://www.omdbapi.com/?s=${type}&apikey=${apiKey}`)
        .then(response => response.json())
        .then(data => {
            console.log(data); // عرض الرد في وحدة التحكم
            const movies = data.Search;
            const movieContainer = document.getElementById(containerId);
            movieContainer.innerHTML = '';
            if (movies && movies.length > 0) {
                movies.forEach(movie => {
                    const movieElement = document.createElement('div');
                    movieElement.className = 'movie';
                    movieElement.onclick = () => openModal(movie);
                    movieElement.innerHTML = `
                        <img src="${movie.Poster}" alt="${movie.Title}">
                        <h2>${movie.Title}</h2>
                        <p>${movie.Year}</p>
                    `;
                    movieContainer.appendChild(movieElement);
                });
            } else {
                movieContainer.innerHTML = `<p>لم يتم العثور على أفلام ${type}.</p>`;
            }
        })
        .catch(error => {
            console.error('Error fetching movies:', error);
            document.getElementById(containerId).innerHTML = `<p>حدث خطأ أثناء جلب تفاصيل الأفلام ${type}.</p>`;
        });
}

function searchMovies() {
    const query = document.getElementById('searchInput').value;
    fetch(`https://www.omdbapi.com/?s=${encodeURIComponent(query)}&apikey=${apiKey}`)
        .then(response => response.json())
        .then(data => {
            console.log(data); // عرض الرد في وحدة التحكم
            const movies = data.Search;
            const movieContainer = document.getElementById('searchMovies');
            movieContainer.innerHTML = '';
            if (movies && movies.length > 0) {
                movies.forEach(movie => {
                    const movieElement = document.createElement('div');
                    movieElement.className = 'movie';
                    movieElement.onclick = () => openModal(movie);
                    movieElement.innerHTML = `
                        <img src="${movie.Poster}" alt="${movie.Title}">
                        <h2>${movie.Title}</h2>
                        <p>${movie.Year}</p>
                    `;
                    movieContainer.appendChild(movieElement);
                });
            } else {
                movieContainer.innerHTML = `<p>لم يتم العثور على أفلام أو مسلسلات لـ "${query}".</p>`;
            }
        })
        .catch(error => {
            console.error('Error fetching movies:', error);
            document.getElementById('searchMovies').innerHTML = `<p>حدث خطأ أثناء جلب تفاصيل الأفلام.</p>`;
        });
}

function openModal(movie) {
    document.getElementById('modalPoster').src = movie.Poster;
    document.getElementById('modalTitle').innerText = movie.Title;
    document.getElementById('modalYear').innerText = `السنة: ${movie.Year}`;
    document.getElementById('modalPlot').innerText = movie.Plot || 'لا توجد تفاصيل متاحة.';
    document.getElementById('modalLink').href = `https://www.imdb.com/title/${movie.imdbID}/`; // رابط لمشاهدة الفيلم على IMDb
    
    // ضع رابط تحميل الترجمة إذا كان متاحًا
    // هذا رابط عام لموقع Subscene كمثال، يمكنك تغييره حسب الحاجة
    document.getElementById('modalSubtitleLink').href = `https://subscene.com/subtitles/title/${encodeURIComponent(movie.Title)}`;
    document.getElementById('modalSubtitleLink').style.display = 'block';
    
    document.getElementById('movieModal').style.display = 'flex';
}

function closeModal() {
    document.getElementById('movieModal').style.display = 'none';
}

function toggleMode() {
    document.body.classList.toggle('light-mode');
    const icon = document.getElementById('modeIcon');
    if (document.body.classList.contains('light-mode')) {
        icon.classList.remove('fa-sun');
        icon.classList.add('fa-moon');
    } else {
        icon.classList.remove('fa-moon');
        icon.classList.add('fa-sun');
    }
}

// تحميل الأفلام عند فتح الصفحة
window.onload = () => {
    fetchMoviesByType('action', 'actionMovies');
    fetchMoviesByType('drama', 'dramaMovies');
    fetchMoviesByType('comedy', 'comedyMovies');
    fetchMoviesByType('horror', 'horrorMovies');
    fetchMoviesByType('adventure', 'adventureMovies');
    fetchMoviesByType('science fiction', 'sciFiMovies');
    fetchMoviesByType('series', 'seriesMovies');
};

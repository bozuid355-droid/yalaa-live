<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>كورة لايف - بث مباشر</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.rtl.min.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.0/font/bootstrap-icons.css">
    <style>
        body { background-color: #121212; color: #eee; font-family: 'Segoe UI', Tahoma, sans-serif; min-height: 100vh; margin: 0; }
        .navbar { background-color: #000; border-bottom: 3px solid #198754; }
        
        .match-card {
            background: linear-gradient(145deg, #1e1e1e, #252525);
            border-radius: 15px;
            margin-bottom: 25px;
            border: 1px solid #333;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        .match-card:hover {
            transform: translateY(-5px);
            border-color: #198754;
            box-shadow: 0 5px 15px rgba(40, 167, 69, 0.3);
        }
        .live-badge {
            background-color: #dc3545;
            color: white;
            padding: 5px 12px;
            border-radius: 0 0 0 10px;
            font-size: 0.8rem;
            position: absolute;
            top: 0;
            right: 0;
            font-weight: bold;
            animation: pulse 2s infinite;
        }
        .team-name { font-size: 1.25rem; font-weight: bold; margin: 10px 0; }
        .vs-badge { background: #198754; color: #fff; border-radius: 50%; width: 40px; height: 40px; display: flex; align-items: center; justify-content: center; margin: 0 auto; font-weight: bold; font-size: 0.9rem; }
        .match-time { color: #aaa; font-size: 0.9rem; margin-top: 10px; }
        
        @keyframes pulse { 0% { opacity: 1; } 50% { opacity: 0.7; } 100% { opacity: 1; } }
        
        .empty-state { padding: 50px; text-align: center; color: #666; }
    </style>
</head>
<body>

<nav class="navbar navbar-dark">
    <div class="container">
        <a class="navbar-brand fw-bold" href="#">
            <i class="bi bi-tv-fill text-success"></i> KOORA <span class="text-success">LIVE</span>
        </a>
    </div>
</nav>

<div class="container mt-5">
    <div class="text-center mb-5">
        <h2 class="fw-bold">مباريات اليوم <span class="text-success">المباشرة</span></h2>
        <p class="text-muted">اضغط على "مشاهدة" لمتابعة البث</p>
    </div>

    <div class="row" id="matchesContainer"></div>

    <div id="noMatchesMsg" class="empty-state" style="display: none;">
        <i class="bi bi-broadcast display-1 mb-3 d-block"></i>
        <h3>لا توجد مباريات جارية الآن</h3>
        <p>انتظر حتى يقوم الأدمن بإضافة مباريات جديدة.</p>
    </div>
</div>

<div class="modal fade" id="videoModal" tabindex="-1" aria-hidden="true">
    <div class="modal-dialog modal-lg modal-dialog-centered">
        <div class="modal-content bg-dark border-secondary">
            <div class="modal-header border-0">
                <h5 class="modal-title text-white" id="modalTitle">مشاهدة المباراة</h5>
                <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button>
            </div>
            <div class="modal-body p-0 bg-black text-center" id="videoContainer"></div>
        </div>
    </div>
</div>

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
<script>
    document.addEventListener('DOMContentLoaded', loadMatchesUser);

    function loadMatchesUser() {
        const matches = JSON.parse(localStorage.getItem('live_matches') || '[]');
        const container = document.getElementById('matchesContainer');
        const emptyMsg = document.getElementById('noMatchesMsg');

        container.innerHTML = '';

        if (matches.length === 0) {
            emptyMsg.style.display = 'block';
        } else {
            emptyMsg.style.display = 'none';
            matches.forEach(m => {
                container.innerHTML += `
                    <div class="col-md-6 col-lg-4">
                        <div class="match-card text-center p-4">
                            <div class="live-badge"><i class="bi bi-circle-fill small me-1"></i> مباشر</div>
                            <div class="row align-items-center mb-3">
                                <div class="col-5 team-name">${m.teamA}</div>
                                <div class="col-2"><div class="vs-badge">VS</div></div>
                                <div class="col-5 team-name">${m.teamB}</div>
                            </div>
                            <div class="match-time mb-3"><i class="bi bi-clock"></i> ${m.time}</div>
                            <button class="btn btn-success w-100 rounded-pill fw-bold" onclick='openVideo(${JSON.stringify(m)})'>
                                <i class="bi bi-play-fill"></i> مشاهدة الآن
                            </button>
                        </div>
                    </div>
                `;
            });
        }
    }

    const videoModal = new bootstrap.Modal(document.getElementById('videoModal'));

    function openVideo(match) {
        document.getElementById('modalTitle').innerText = `${match.teamA} ضد ${match.teamB}`;
        document.getElementById('videoContainer').innerHTML = match.embed;
        videoModal.show();
    }

    document.getElementById('videoModal').addEventListener('hidden.bs.modal', () => {
        document.getElementById('videoContainer').innerHTML = '';
    });

    setInterval(loadMatchesUser, 10000);
</script>

</body>
</html>

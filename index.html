// ===================== ESTADO Y PERSISTENCIA =====================
const STORAGE_KEY = 'becadosUtepsaState_v1';

const COLOR_CYCLE = ['#1D4E89', '#2166AC', '#4393C3', '#85B7EB', '#2E86AB', '#5DA9E9'];

function defaultState() {
  return {
    perfil: {
      nombre: 'María López',
      iniciales: 'ML',
      beca: 'Beca Bachiller Destacado',
      semestre: 'Semestre 2-2025',
      metaHoras: 80
    },
    categorias: [
      { id: 'cat-cultura', nombre: 'Cultura' },
      { id: 'cat-deporte', nombre: 'Deporte' },
      { id: 'cat-social', nombre: 'Social' },
      { id: 'cat-academico', nombre: 'Académico' }
    ],
    actividades: [
      { id: 'a1', nombre: 'Feria universitaria UTEPSA', categoria: 'cat-social', horas: 6, fecha: '2025-06-10', estado: 'Aprobada', icono: '👥' },
      { id: 'a2', nombre: 'Tutoría de matemáticas', categoria: 'cat-academico', horas: 4, fecha: '2025-06-05', estado: 'Aprobada', icono: '📚' },
      { id: 'a3', nombre: 'Taller de liderazgo', categoria: 'cat-cultura', horas: 8, fecha: '2025-05-30', estado: 'Pendiente', icono: '🕐' },
      { id: 'a4', nombre: 'Campaña solidaria', categoria: 'cat-social', horas: 5, fecha: '2025-05-22', estado: 'Aprobada', icono: '❤️' },
      { id: 'a5', nombre: 'Selección de voleibol', categoria: 'cat-deporte', horas: 18, fecha: '2025-05-15', estado: 'Aprobada', icono: '🏐' },
      { id: 'a6', nombre: 'Coro institucional', categoria: 'cat-cultura', horas: 12, fecha: '2025-05-02', estado: 'Aprobada', icono: '🎵' }
    ],
    notificaciones: [
      { texto: '⚠ Actividad pendiente de aprobación', tipo: 'ambar' },
      { texto: '✓ 8 hrs registradas — 12 jun', tipo: 'verde' },
      { texto: '📅 Nueva actividad disponible', tipo: 'azul' }
    ],
    adminMode: false
  };
}

let state = loadState();

function loadState() {
  try {
    const raw = localStorage.getItem(STORAGE_KEY);
    if (!raw) return defaultState();
    const parsed = JSON.parse(raw);
    // saneo básico por si falta alguna llave (versiones futuras)
    const base = defaultState();
    return Object.assign(base, parsed);
  } catch (e) {
    return defaultState();
  }
}

function saveState() {
  try {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
  } catch (e) {
    console.error('No se pudo guardar el estado', e);
  }
}

// ===================== HELPERS =====================
function catNombre(id) {
  const c = state.categorias.find(c => c.id === id);
  return c ? c.nombre : 'Sin categoría';
}

function catColor(id) {
  const idx = state.categorias.findIndex(c => c.id === id);
  return COLOR_CYCLE[idx % COLOR_CYCLE.length] || '#1D4E89';
}

function horasAprobadas() {
  return state.actividades
    .filter(a => a.estado === 'Aprobada')
    .reduce((sum, a) => sum + Number(a.horas), 0);
}

function horasPendientes() {
  return state.actividades
    .filter(a => a.estado === 'Pendiente')
    .reduce((sum, a) => sum + Number(a.horas), 0);
}

function horasPorCategoria() {
  const map = {};
  state.categorias.forEach(c => map[c.id] = 0);
  state.actividades.filter(a => a.estado === 'Aprobada').forEach(a => {
    map[a.categoria] = (map[a.categoria] || 0) + Number(a.horas);
  });
  return map;
}

function fmtFecha(iso) {
  if (!iso) return '—';
  const [y, m, d] = iso.split('-');
  const meses = ['ene','feb','mar','abr','may','jun','jul','ago','sep','oct','nov','dic'];
  return `${parseInt(d,10)} ${meses[parseInt(m,10)-1]} ${y}`;
}

function todayIso() {
  return new Date().toISOString().slice(0,10);
}

function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  clearTimeout(window.__toastTimer);
  window.__toastTimer = setTimeout(() => t.classList.remove('show'), 2600);
}

function addNotif(texto, tipo) {
  state.notificaciones.unshift({ texto, tipo });
  state.notificaciones = state.notificaciones.slice(0, 8);
}

// ===================== NAVEGACIÓN =====================
const VIEWS = ['inicio', 'horas', 'actividades', 'historial', 'perfil'];
let currentView = 'inicio';

function goTo(view) {
  if (!VIEWS.includes(view)) return;
  currentView = view;
  VIEWS.forEach(v => {
    document.getElementById('view-' + v).classList.toggle('active', v === view);
  });
  document.querySelectorAll('.nav-links button[data-go]').forEach(btn => {
    btn.classList.toggle('active', btn.dataset.go === view);
  });
  document.querySelectorAll('.bn-item[data-go]').forEach(btn => {
    btn.classList.toggle('active', btn.dataset.go === view);
  });
  window.scrollTo({ top: 0, behavior: 'smooth' });
  renderAll();
}

document.querySelectorAll('[data-go]').forEach(el => {
  el.addEventListener('click', () => goTo(el.dataset.go));
});

// ===================== RENDER: INICIO =====================
function renderInicio() {
  const acumuladas = horasAprobadas();
  const meta = Number(state.perfil.metaHoras) || 1;
  const faltantes = Math.max(meta - acumuladas, 0);
  const pct = Math.min((acumuladas / meta) * 100, 100);

  document.getElementById('heroGreeting').textContent = `Hola, ${state.perfil.nombre} 👋`;
  document.getElementById('heroSub').textContent = `${state.perfil.beca} · ${state.perfil.semestre}`;
  document.getElementById('heroPill').textContent = `${pct.toFixed(1)}% completado este semestre`;

  const circumference = 188.5;
  const offset = circumference - (circumference * pct / 100);
  document.getElementById('ringFill').setAttribute('stroke-dashoffset', offset.toFixed(1));
  document.getElementById('ringHrs').textContent = acumuladas;
  document.getElementById('ringGoal').textContent = `de ${meta} hrs`;

  document.getElementById('statAcum').textContent = acumuladas;
  document.getElementById('statFalt').textContent = faltantes;

  // próxima actividad: la pendiente/futura más cercana
  const futuras = state.actividades
    .filter(a => a.estado !== 'Rechazada' && a.fecha >= todayIso())
    .sort((a,b) => a.fecha.localeCompare(b.fecha));
  if (futuras.length) {
    document.getElementById('statProxFecha').textContent = fmtFecha(futuras[0].fecha);
    document.getElementById('statProxNom').textContent = futuras[0].nombre;
  } else {
    document.getElementById('statProxFecha').textContent = '—';
    document.getElementById('statProxNom').textContent = 'Sin actividades próximas';
  }

  const alertBox = document.getElementById('inicioAlert');
  if (faltantes > 0) {
    alertBox.innerHTML = `<div class="alert"><svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"/><path d="M13.73 21a2 2 0 0 1-3.46 0"/></svg><span>Te faltan <strong>${faltantes} horas</strong> para completar tu cuota del semestre.</span></div>`;
  } else {
    alertBox.innerHTML = `<div class="alert"><svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M20 6 9 17l-5-5"/></svg><span>¡Completaste tu cuota de horas del semestre! 🎉</span></div>`;
  }

  renderCategoryProgress('catProgressList');
  renderNotifList();
  renderRecentActivities();
}

function renderCategoryProgress(targetId) {
  const target = document.getElementById(targetId);
  const map = horasPorCategoria();
  const max = Math.max(...Object.values(map), 1);
  target.innerHTML = state.categorias.map(c => {
    const hrs = map[c.id] || 0;
    const widthPct = Math.min((hrs / max) * 100, 100);
    return `<div class="prog-item">
      <div class="prog-row"><span>${escapeHtml(c.nombre)}</span><span>${hrs} hrs</span></div>
      <div class="prog-track"><div class="prog-fill" style="width:${widthPct}%;background:${catColor(c.id)}"></div></div>
    </div>`;
  }).join('') || '<div class="empty-note">Aún no hay categorías configuradas.</div>';
}

function renderNotifList() {
  const target = document.getElementById('notifList');
  if (!state.notificaciones.length) {
    target.innerHTML = '<div class="empty-note">No tienes notificaciones por ahora.</div>';
    return;
  }
  target.innerHTML = state.notificaciones.map(n =>
    `<div class="notif-item notif-${n.tipo}">${escapeHtml(n.texto)}</div>`
  ).join('');
}

function renderRecentActivities() {
  const target = document.getElementById('recentActList');
  const recientes = [...state.actividades].sort((a,b) => b.fecha.localeCompare(a.fecha)).slice(0,4);
  if (!recientes.length) {
    target.innerHTML = '<div class="empty-note">Aún no registraste actividades.</div>';
    return;
  }
  target.innerHTML = recientes.map(a => actItemHtml(a, false)).join('');
}

function actItemHtml(a, withAdminActions) {
  const statusClass = a.estado === 'Aprobada' ? 'status-ok' : a.estado === 'Pendiente' ? 'status-pend' : 'status-rej';
  const hrsClass = a.estado === 'Aprobada' ? 'ok' : a.estado === 'Pendiente' ? 'pend' : 'rej';
  const adminBtns = (withAdminActions && a.estado === 'Pendiente') ? `
    <div class="act-actions">
      <button class="mini-btn approve" data-approve="${a.id}">Aprobar</button>
      <button class="mini-btn reject" data-reject="${a.id}">Rechazar</button>
    </div>` : '';
  return `<li class="act-item">
    <div class="act-icon" style="background:${hexLight(catColor(a.categoria))}">${a.icono || '📌'}</div>
    <div class="act-info">
      <div class="act-name">${escapeHtml(a.nombre)}</div>
      <div class="act-meta">${fmtFecha(a.fecha)} · <span class="act-status ${statusClass}">${a.estado}</span> · ${escapeHtml(catNombre(a.categoria))}</div>
    </div>
    ${adminBtns}
    <span class="act-hrs ${hrsClass}">+${a.horas} hrs</span>
  </li>`;
}

function hexLight(hex) {
  // Genera una versión clara aproximada del color para el fondo del ícono
  return hex + '22';
}

function escapeHtml(str) {
  const div = document.createElement('div');
  div.textContent = str;
  return div.innerHTML;
}

// ===================== RENDER: MIS HORAS =====================
function renderHoras() {
  document.getElementById('horasAcum2').textContent = horasAprobadas();
  document.getElementById('horasMeta2').textContent = state.perfil.metaHoras;
  document.getElementById('horasPend2').textContent = horasPendientes();
  renderCategoryProgress('catProgressList2');
}

// ===================== RENDER: ACTIVIDADES (form) =====================
function populateCategorySelect() {
  const sel = document.getElementById('actCategoria');
  sel.innerHTML = state.categorias.map(c => `<option value="${c.id}">${escapeHtml(c.nombre)}</option>`).join('');
}

function renderUpcoming() {
  const target = document.getElementById('upcomingList');
  const emptyNote = document.getElementById('upcomingEmpty');
  const futuras = state.actividades
    .filter(a => a.estado !== 'Rechazada' && a.fecha >= todayIso())
    .sort((a,b) => a.fecha.localeCompare(b.fecha));
  if (!futuras.length) {
    target.innerHTML = '';
    emptyNote.style.display = 'block';
    return;
  }
  emptyNote.style.display = 'none';
  target.innerHTML = futuras.map(a => actItemHtml(a, state.adminMode)).join('');
}

document.getElementById('actForm').addEventListener('submit', function(e) {
  e.preventDefault();
  const nombre = document.getElementById('actNombre').value.trim();
  const categoria = document.getElementById('actCategoria').value;
  const horasInput = document.getElementById('actHoras');
  const horas = parseFloat(horasInput.value);
  const fechaInput = document.getElementById('actFecha');
  const fecha = fechaInput.value || todayIso();

  let valid = true;
  document.getElementById('errNombre').classList.remove('show');
  document.getElementById('errHoras').classList.remove('show');

  if (!nombre) {
    document.getElementById('errNombre').classList.add('show');
    valid = false;
  }
  if (!horas || horas <= 0 || horas > 40) {
    document.getElementById('errHoras').classList.add('show');
    valid = false;
  }
  if (!valid) return;

  const nueva = {
    id: 'a' + Date.now(),
    nombre,
    categoria,
    horas,
    fecha,
    estado: 'Pendiente',
    icono: '🕐'
  };
  state.actividades.unshift(nueva);
  addNotif(`📌 Nueva actividad registrada: ${nombre} (pendiente de aprobación)`, 'ambar');
  saveState();
  showToast('Actividad registrada. Queda pendiente de aprobación.');
  this.reset();
  renderAll();
});

// ===================== RENDER: HISTORIAL =====================
let historyFilter = 'todas';

document.getElementById('filterRow').addEventListener('click', (e) => {
  const btn = e.target.closest('.filter-chip');
  if (!btn) return;
  historyFilter = btn.dataset.filter;
  document.querySelectorAll('.filter-chip').forEach(b => b.classList.toggle('active', b === btn));
  renderHistorial();
});

function renderHistorial() {
  const target = document.getElementById('historyList');
  const emptyNote = document.getElementById('historyEmpty');
  let lista = [...state.actividades].sort((a,b) => b.fecha.localeCompare(a.fecha));
  if (historyFilter !== 'todas') {
    lista = lista.filter(a => a.estado === historyFilter);
  }

  const bannerTarget = document.getElementById('adminBannerHistorial');
  if (state.adminMode) {
    const pendCount = state.actividades.filter(a => a.estado === 'Pendiente').length;
    bannerTarget.innerHTML = `<div class="admin-banner">🛠 Modo administrador activo — puedes aprobar o rechazar actividades pendientes (${pendCount} en espera).</div>`;
  } else {
    bannerTarget.innerHTML = '';
  }

  if (!lista.length) {
    target.innerHTML = '';
    emptyNote.style.display = 'block';
    return;
  }
  emptyNote.style.display = 'none';
  target.innerHTML = lista.map(a => actItemHtml(a, state.adminMode)).join('');
}

// Delegación de eventos para aprobar/rechazar (funciona en historial y próximas)
document.addEventListener('click', (e) => {
  const approveId = e.target.dataset && e.target.dataset.approve;
  const rejectId = e.target.dataset && e.target.dataset.reject;
  if (approveId) {
    const act = state.actividades.find(a => a.id === approveId);
    if (act) {
      act.estado = 'Aprobada';
      addNotif(`✓ Actividad aprobada: ${act.nombre} (+${act.horas} hrs)`, 'verde');
      saveState();
      showToast('Actividad aprobada.');
      renderAll();
    }
  }
  if (rejectId) {
    const act = state.actividades.find(a => a.id === rejectId);
    if (act) {
      act.estado = 'Rechazada';
      addNotif(`✕ Actividad rechazada: ${act.nombre}`, 'rojo');
      saveState();
      showToast('Actividad rechazada.');
      renderAll();
    }
  }
});

// ===================== MODO ADMIN =====================
document.getElementById('adminToggle').addEventListener('click', () => {
  state.adminMode = !state.adminMode;
  saveState();
  document.getElementById('adminToggle').classList.toggle('on', state.adminMode);
  document.getElementById('adminToggle').textContent = state.adminMode ? 'Modo admin: ON' : 'Modo admin';
  showToast(state.adminMode ? 'Modo administrador activado.' : 'Modo administrador desactivado.');
  renderAll();
});

// ===================== RENDER: PERFIL =====================
function renderPerfil() {
  document.getElementById('profileAvatar').textContent = state.perfil.iniciales;
  document.getElementById('profileName').textContent = state.perfil.nombre;
  document.getElementById('profileSub').textContent = `${state.perfil.beca} · ${state.perfil.semestre}`;
  document.getElementById('cfgNombre').value = state.perfil.nombre;
  document.getElementById('cfgBeca').value = state.perfil.beca;
  document.getElementById('cfgSemestre').value = state.perfil.semestre;
  document.getElementById('cfgMeta').value = state.perfil.metaHoras;
  renderCategoryEditor();
}

function renderCategoryEditor() {
  const target = document.getElementById('categoryEditor');
  const map = horasPorCategoria();
  target.innerHTML = state.categorias.map(c => `
    <div class="cat-row" data-cat-id="${c.id}">
      <input type="text" value="${escapeHtml(c.nombre)}" data-cat-name="${c.id}">
      <input type="text" value="${map[c.id] || 0} hrs" disabled style="color:var(--muted);background:var(--gray-bg)">
      <button type="button" class="cat-del" data-cat-del="${c.id}" title="Eliminar categoría">✕</button>
    </div>
  `).join('');
}

document.getElementById('saveProfileBtn').addEventListener('click', () => {
  const nombre = document.getElementById('cfgNombre').value.trim();
  const beca = document.getElementById('cfgBeca').value.trim();
  const semestre = document.getElementById('cfgSemestre').value.trim();
  const meta = parseInt(document.getElementById('cfgMeta').value, 10);

  if (!nombre || !beca || !semestre || !meta || meta <= 0) {
    showToast('Revisa que todos los campos estén completos y la meta sea válida.');
    return;
  }

  state.perfil.nombre = nombre;
  state.perfil.beca = beca;
  state.perfil.semestre = semestre;
  state.perfil.metaHoras = meta;
  state.perfil.iniciales = nombre.split(' ').filter(Boolean).slice(0,2).map(p => p[0].toUpperCase()).join('') || 'NN';

  saveState();
  showToast('Perfil actualizado correctamente.');
  renderAll();
});

document.getElementById('addCategoryBtn').addEventListener('click', () => {
  const id = 'cat-' + Date.now();
  state.categorias.push({ id, nombre: 'Nueva categoría' });
  saveState();
  renderCategoryEditor();
});

document.getElementById('categoryEditor').addEventListener('change', (e) => {
  const id = e.target.dataset.catName;
  if (!id) return;
  const cat = state.categorias.find(c => c.id === id);
  if (cat) {
    const nuevoNombre = e.target.value.trim() || cat.nombre;
    cat.nombre = nuevoNombre;
    saveState();
    showToast('Categoría actualizada.');
    renderAll();
  }
});

document.getElementById('categoryEditor').addEventListener('click', (e) => {
  const id = e.target.dataset.catDel;
  if (!id) return;
  if (state.categorias.length <= 1) {
    showToast('Debe quedar al menos una categoría.');
    return;
  }
  const enUso = state.actividades.some(a => a.categoria === id);
  if (enUso && !confirm('Esta categoría tiene actividades registradas. ¿Eliminarla de todas formas? Las actividades quedarán sin categoría visible.')) {
    return;
  }
  state.categorias = state.categorias.filter(c => c.id !== id);
  saveState();
  renderCategoryEditor();
  renderAll();
});

document.getElementById('resetDataBtn').addEventListener('click', () => {
  if (!confirm('¿Seguro que quieres restablecer todos los datos a los valores de ejemplo? Esta acción no se puede deshacer.')) return;
  state = defaultState();
  saveState();
  showToast('Datos restablecidos.');
  renderAll();
});

// ===================== CAMPANA DE NOTIFICACIONES =====================
document.getElementById('bellBtn').addEventListener('click', () => {
  goTo('inicio');
  document.getElementById('notifDot').classList.remove('show');
});

// ===================== RENDER GENERAL =====================
function renderAll() {
  populateCategorySelect();
  renderInicio();
  renderHoras();
  renderUpcoming();
  renderHistorial();
  renderPerfil();

  document.getElementById('adminToggle').classList.toggle('on', state.adminMode);
  document.getElementById('adminToggle').textContent = state.adminMode ? 'Modo admin: ON' : 'Modo admin';

  const hayPendientes = state.actividades.some(a => a.estado === 'Pendiente');
  document.getElementById('notifDot').classList.toggle('show', hayPendientes);
}

// Fecha mínima sugerida en el form = hoy (no obligatoria, pero ayuda)
document.getElementById('actFecha').value = todayIso();

renderAll();

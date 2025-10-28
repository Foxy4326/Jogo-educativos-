<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Executores e Scripts</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; line-height: 1.6; color: #333; background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); min-height: 100vh; }
        .container { max-width: 1200px; margin: 0 auto; padding: 20px; }
        .hidden { display: none !important; }
        .hero { text-align: center; padding: 60px 20px; color: white; }
        .hero h1 { font-size: 2.5rem; margin-bottom: 1rem; text-shadow: 2px 2px 4px rgba(0,0,0,0.3); }
        .hero p { font-size: 1.2rem; margin-bottom: 2rem; opacity: 0.9; }
        .section { background: white; margin: 30px 0; padding: 30px; border-radius: 15px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); }
        .section h2 { color: #4a5568; margin-bottom: 25px; font-size: 1.8rem; border-bottom: 3px solid #667eea; padding-bottom: 10px; }
        .grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 20px; margin-top: 20px; }
        .card { background: #f8f9fa; border: 1px solid #e9ecef; border-radius: 12px; padding: 20px; transition: all 0.3s ease; box-shadow: 0 4px 6px rgba(0,0,0,0.05); }
        .card:hover { transform: translateY(-5px); box-shadow: 0 8px 25px rgba(0,0,0,0.15); }
        .card-header h3 { color: #2d3748; margin-bottom: 15px; font-size: 1.3rem; }
        .card-body p { color: #4a5568; margin-bottom: 15px; line-height: 1.5; }
        .date { color: #718096; font-size: 0.9rem; font-style: italic; }
        .card-actions { margin-top: 20px; display: flex; gap: 10px; }
        .auth-section { background: white; margin: 50px auto; padding: 40px; border-radius: 15px; box-shadow: 0 15px 35px rgba(0,0,0,0.1); max-width: 400px; text-align: center; }
        .auth-section h1 { color: #4a5568; margin-bottom: 25px; }
        .auth-form, .upload-form { display: flex; flex-direction: column; gap: 15px; }
        .upload-section { background: white; margin: 30px 0; padding: 30px; border-radius: 15px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); }
        .upload-form { max-width: 600px; }
        .form-actions { display: flex; gap: 12px; flex-wrap: wrap; }
        input, textarea, select { padding: 12px; border: 2px solid #e2e8f0; border-radius: 8px; font-size: 1rem; transition: border-color 0.3s ease; width: 100%; }
        input:focus, textarea:focus, select:focus { outline: none; border-color: #667eea; }
        textarea { min-height: 100px; resize: vertical; }
        .file-upload-container { display: flex; gap: 10px; align-items: center; margin-bottom: 10px; }
        .file-upload-btn { background: #4299e1; color: white; padding: 10px 16px; border: none; border-radius: 6px; cursor: pointer; font-size: 0.9rem; }
        .file-upload-btn:hover { background: #3182ce; }
        .file-name { color: #718096; font-size: 0.9rem; }
        .upload-type-selector { display: flex; gap: 12px; margin-bottom: 15px; }
        .upload-type-btn { flex: 1; padding: 10px; border: 2px solid #e2e8f0; background: white; border-radius: 6px; cursor: pointer; text-align: center; transition: all 0.3s ease; }
        .upload-type-btn.active { background: #667eea; color: white; border-color: #667eea; }
        .btn { padding: 12px 20px; border: none; border-radius: 8px; font-size: 1rem; font-weight: 600; cursor: pointer; transition: all 0.3s ease; text-decoration: none; display: inline-block; text-align: center; }
        .btn-primary { background: #667eea; color: white; }
        .btn-primary:hover { background: #5a6fd8; transform: translateY(-2px); }
        .btn-success { background: #48bb78; color: white; }
        .btn-success:hover { background: #3fa76c; transform: translateY(-2px); }
        .btn-warning { background: #ed8936; color: white; }
        .btn-warning:hover { background: #e37820; }
        .btn-danger { background: #f56565; color: white; }
        .btn-danger:hover { background: #e53e3e; }
        .btn-secondary { background: #a0aec0; color: white; }
        .btn-secondary:hover { background: #9099a6; }
        .btn-outline { background: transparent; color: white; border: 2px solid white; }
        .btn-outline:hover { background: white; color: #667eea; }
        .btn-small { padding: 8px 12px; font-size: 0.85rem; }
        .download-btn { background: #4299e1; color: white; width: 100%; margin-top: 10px; }
        .download-btn:hover { background: #3182ce; }
        .alert { padding: 12px; border-radius: 6px; margin: 15px 0; font-weight: 500; }
        .alert-error { background: #fed7d7; color: #c53030; border: 1px solid #feb2b2; }
        .alert-success { background: #c6f6d5; color: #276749; border: 1px solid #9ae6b4; }
        .empty-message { text-align: center; color: #718096; font-style: italic; padding: 30px; grid-column: 1 / -1; }
        .logout-admin-btn { position: fixed; top: 15px; right: 15px; z-index: 1000; }
        
        @media (max-width: 768px) {
            .container { padding: 10px; }
            .hero h1 { font-size: 2rem; }
            .section { padding: 20px; margin: 15px 0; }
            .grid { grid-template-columns: 1fr; }
            .auth-section { margin: 20px; padding: 25px; }
            .upload-section { padding: 20px; }
            .form-actions, .upload-type-selector { flex-direction: column; }
            .logout-admin-btn { position: relative; top: auto; right: auto; margin: 10px 0; }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Seção de Autenticação -->
        <section id="auth" class="auth-section">
            <div class="auth-container">
                <h1>Acesso Administrativo</h1>
                <form id="auth-form" class="auth-form">
                    <input type="password" id="access-code" placeholder="Digite o código de acesso" required>
                    <button type="submit" class="btn btn-primary">Acessar</button>
                </form>
                <div id="auth-message" class="alert alert-error hidden"></div>
            </div>
        </section>

        <!-- Seção de Upload (Admin) -->
        <section id="upload" class="upload-section hidden">
            <h2>Publicar Novo Conteúdo</h2>
            
            <!-- Formulário de Upload -->
            <div id="upload-form-container">
                <form id="upload-form" class="upload-form">
                    <input type="text" id="title" placeholder="Título" required>
                    <textarea id="description" placeholder="Descrição" required></textarea>
                    <select id="type" required>
                        <option value="">Selecione o tipo</option>
                        <option value="executor">Executor</option>
                        <option value="script">Script</option>
                    </select>
                    
                    <div class="upload-type-selector">
                        <button type="button" class="upload-type-btn active" data-type="url">URL/Link</button>
                        <button type="button" class="upload-type-btn" data-type="file">Arquivo APK</button>
                    </div>
                    
                    <div id="url-field">
                        <input type="url" id="download-url" placeholder="https://exemplo.com/download" required>
                    </div>
                    
                    <div id="file-field" class="hidden">
                        <div class="file-upload-container">
                            <input type="file" id="file-upload" accept=".apk,.apks,.zip,.rar,.7z" class="hidden">
                            <button type="button" id="file-select-btn" class="file-upload-btn">Selecionar APK</button>
                            <span id="file-name" class="file-name">Nenhum arquivo selecionado</span>
                        </div>
                        <small style="color: #718096; font-size: 0.8rem;">
                            ⚠️ Para APKs, use URLs externas. Arquivos locais funcionam apenas durante a sessão.
                        </small>
                    </div>
                    
                    <button type="submit" class="btn btn-success">Publicar</button>
                </form>
            </div>
            
            <!-- Formulário de Edição -->
            <div id="edit-form-container" class="hidden">
                <form id="edit-form" class="upload-form">
                    <input type="hidden" id="edit-id">
                    <input type="text" id="edit-title" placeholder="Título" required>
                    <textarea id="edit-description" placeholder="Descrição" required></textarea>
                    <select id="edit-type" required>
                        <option value="executor">Executor</option>
                        <option value="script">Script</option>
                    </select>
                    
                    <div class="upload-type-selector">
                        <button type="button" class="upload-type-btn active" data-type="url">URL/Link</button>
                        <button type="button" class="upload-type-btn" data-type="file">Arquivo APK</button>
                    </div>
                    
                    <div id="edit-url-field">
                        <input type="url" id="edit-download-url" placeholder="URL de Download" required>
                    </div>
                    
                    <div id="edit-file-field" class="hidden">
                        <div class="file-upload-container">
                            <input type="file" id="edit-file-upload" accept=".apk,.apks,.zip,.rar,.7z" class="hidden">
                            <button type="button" id="edit-file-select-btn" class="file-upload-btn">Selecionar APK</button>
                            <span id="edit-file-name" class="file-name">Nenhum arquivo selecionado</span>
                        </div>
                        <small style="color: #718096; font-size: 0.8rem;">
                            ⚠️ Para APKs, use URLs externas. Arquivos locais funcionam apenas durante a sessão.
                        </small>
                    </div>
                    
                    <div class="form-actions">
                        <button type="submit" class="btn btn-success">Atualizar</button>
                        <button type="button" id="cancel-edit-btn" class="btn btn-secondary">Cancelar</button>
                    </div>
                </form>
            </div>
            
            <div id="upload-message" class="alert hidden"></div>
            <button id="add-item-btn" class="btn btn-primary">Adicionar Novo Item</button>
        </section>

        <!-- Conteúdo Principal -->
        <main id="main-content">
            <header class="hero">
                <h1>Executores e Scripts</h1>
                <p>Encontre os melhores executores e scripts em um só lugar</p>
                <button id="logout-btn" class="btn btn-outline hidden">Sair do Admin</button>
            </header>

            <!-- Seção de Executores -->
            <section id="executors" class="section">
                <h2>Executores Disponíveis</h2>
                <div id="executors-grid" class="grid">
                    <!-- Os executores serão carregados aqui via JavaScript -->
                </div>
            </section>

            <!-- Seção de Scripts -->
            <section id="scripts" class="section">
                <h2>Scripts Disponíveis</h2>
                <div id="scripts-grid" class="grid">
                    <!-- Os scripts serão carregados aqui via JavaScript -->
                </div>
            </section>
        </main>
    </div>

    <button id="logout-admin" class="logout-admin-btn btn btn-danger hidden">Sair</button>

    <script>
    // Configuração
    const SECRET_CODE = "admin123";
    let currentUploadType = 'url';
    let temporaryFileStorage = {}; // Armazena arquivos apenas durante a sessão

    // Inicialização quando o DOM estiver carregado
    document.addEventListener('DOMContentLoaded', function() {
        console.log('DOM carregado - inicializando aplicação...');
        
        // Elementos DOM
        const elements = {
            authSection: document.getElementById('auth'),
            uploadSection: document.getElementById('upload'),
            authForm: document.getElementById('auth-form'),
            uploadForm: document.getElementById('upload-form'),
            editForm: document.getElementById('edit-form'),
            accessCodeInput: document.getElementById('access-code'),
            authMessage: document.getElementById('auth-message'),
            uploadMessage: document.getElementById('upload-message'),
            logoutBtn: document.getElementById('logout-btn'),
            logoutAdminBtn: document.getElementById('logout-admin'),
            executorsGrid: document.getElementById('executors-grid'),
            scriptsGrid: document.getElementById('scripts-grid'),
            uploadFormContainer: document.getElementById('upload-form-container'),
            editFormContainer: document.getElementById('edit-form-container'),
            cancelEditBtn: document.getElementById('cancel-edit-btn'),
            addItemBtn: document.getElementById('add-item-btn'),
            fileUpload: document.getElementById('file-upload'),
            fileSelectBtn: document.getElementById('file-select-btn'),
            fileName: document.getElementById('file-name'),
            urlField: document.getElementById('url-field'),
            fileField: document.getElementById('file-field'),
            uploadTypeBtns: document.querySelectorAll('.upload-type-btn'),
            editFileUpload: document.getElementById('edit-file-upload'),
            editFileSelectBtn: document.getElementById('edit-file-select-btn'),
            editFileName: document.getElementById('edit-file-name'),
            editUrlField: document.getElementById('edit-url-field'),
            editFileField: document.getElementById('edit-file-field')
        };

        // Armazenamento
        let publishedItems = JSON.parse(localStorage.getItem('publishedItems')) || [];

        // Funções de Upload
        function setUploadType(type) {
            currentUploadType = type;
            
            // Atualizar botões de tipo
            elements.uploadTypeBtns.forEach(btn => {
                btn.classList.toggle('active', btn.dataset.type === type);
            });

            const editUploadTypeBtns = document.querySelectorAll('#edit-form-container .upload-type-btn');
            editUploadTypeBtns.forEach(btn => {
                btn.classList.toggle('active', btn.dataset.type === type);
            });
            
            // Mostrar/ocultar campos apropriados
            if (type === 'url') {
                elements.urlField.classList.remove('hidden');
                elements.fileField.classList.add('hidden');
                elements.editUrlField.classList.remove('hidden');
                elements.editFileField.classList.add('hidden');
                
                // Atualizar atributos required
                elements.fileUpload.removeAttribute('required');
                document.getElementById('download-url').setAttribute('required', 'true');
            } else {
                elements.urlField.classList.add('hidden');
                elements.fileField.classList.remove('hidden');
                elements.editUrlField.classList.add('hidden');
                elements.editFileField.classList.remove('hidden');
                
                // Atualizar atributos required
                document.getElementById('download-url').removeAttribute('required');
                elements.fileUpload.setAttribute('required', 'true');
            }
        }

        function handleFileSelect(fileInput, fileNameElement) {
            if (fileInput.files.length > 0) {
                const file = fileInput.files[0];
                fileNameElement.textContent = `${file.name} (${formatFileSize(file.size)})`;
                
                // Validar tipo de arquivo
                const validExtensions = ['.apk', '.apks', '.zip', '.rar', '.7z'];
                const fileExtension = '.' + file.name.toLowerCase().split('.').pop();
                
                if (!validExtensions.includes(fileExtension)) {
                    showAlert('Por favor, selecione um arquivo APK, ZIP ou RAR válido.', true);
                    fileInput.value = '';
                    fileNameElement.textContent = 'Nenhum arquivo selecionado';
                    return false;
                }

                // Verificar tamanho do arquivo (máximo 50MB para demonstração)
                if (file.size > 50 * 1024 * 1024) {
                    showAlert('Arquivo muito grande. Use URLs externas para arquivos grandes.', true);
                    fileInput.value = '';
                    fileNameElement.textContent = 'Nenhum arquivo selecionado';
                    return false;
                }
                return true;
            }
            return false;
        }

        function saveFileToTemporaryStorage(file) {
            return new Promise((resolve, reject) => {
                const reader = new FileReader();
                
                reader.onload = function(e) {
                    try {
                        const fileId = 'temp_file_' + Date.now() + '_' + Math.random().toString(36).substr(2, 9);
                        temporaryFileStorage[fileId] = {
                            name: file.name,
                            type: file.type,
                            size: file.size,
                            data: e.target.result,
                            uploadDate: new Date().toISOString()
                        };
                        
                        resolve({ 
                            fileId, 
                            fileName: file.name 
                        });
                    } catch (error) {
                        reject(new Error('Erro ao processar o arquivo: ' + error.message));
                    }
                };
                
                reader.onerror = () => {
                    reject(new Error('Erro ao ler o arquivo'));
                };
                
                reader.readAsDataURL(file);
            });
        }

        function downloadTemporaryFile(fileId) {
            const fileData = temporaryFileStorage[fileId];
            if (!fileData) {
                throw new Error('Arquivo não encontrado no armazenamento temporário');
            }

            // Criar link de download usando DataURL
            const a = document.createElement('a');
            a.href = fileData.data;
            a.download = fileData.name;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
        }

        // Funções Principais
        function saveItems() {
            try {
                localStorage.setItem('publishedItems', JSON.stringify(publishedItems));
                return true;
            } catch (error) {
                console.error('Erro ao salvar itens:', error);
                showAlert('Erro ao salvar os dados.', true);
                return false;
            }
        }

        function checkAuthStatus() {
            const isAuthenticated = localStorage.getItem('authenticated') === 'true';
            if (isAuthenticated) {
                showUploadSection();
            }
        }

        function showUploadSection() {
            elements.authSection.classList.add('hidden');
            elements.uploadSection.classList.remove('hidden');
            elements.logoutBtn.classList.remove('hidden');
            elements.logoutAdminBtn.classList.remove('hidden');
        }

        function hideUploadSection() {
            elements.authSection.classList.remove('hidden');
            elements.uploadSection.classList.add('hidden');
            elements.logoutBtn.classList.add('hidden');
            elements.logoutAdminBtn.classList.add('hidden');
            localStorage.removeItem('authenticated');
        }

        function displayPublishedItems() {
            displayItemsInGrid(elements.executorsGrid, 'executor');
            displayItemsInGrid(elements.scriptsGrid, 'script');
        }

        function displayItemsInGrid(gridElement, type) {
            gridElement.innerHTML = '';
            const items = publishedItems.filter(i => i.type === type);
            
            if (items.length === 0) {
                gridElement.innerHTML = `<div class="empty-message">Nenhum ${type} publicado ainda.</div>`;
                return;
            }

            items.forEach(item => {
                const card = createCard(item);
                gridElement.appendChild(card);
            });
        }

        function createCard(item) {
            const card = document.createElement('div');
            card.className = 'card';
            
            const dateText = item.lastUpdate 
                ? `Atualizado em: ${item.lastUpdate}` 
                : `Publicado em: ${item.date || new Date().toLocaleDateString('pt-BR')}`;
            
            const isAdmin = localStorage.getItem('authenticated') === 'true';
            const adminButtons = isAdmin ? `
                <div class="card-actions">
                    <button class="btn btn-warning btn-small edit-btn" data-id="${item.id}">Editar</button>
                    <button class="btn btn-danger btn-small delete-btn" data-id="${item.id}">Excluir</button>
                </div>
            ` : '';

            const fileInfo = item.fileSize ? `
                <div style="font-size: 0.8rem; color: #718096; margin-top: 5px;">
                    <div>Tamanho: ${formatFileSize(item.fileSize)}</div>
                    <div>Nome: ${item.fileName}</div>
                    ${item.downloadType === 'file' ? '<div>⚠️ Arquivo temporário (apenas esta sessão)</div>' : ''}
                </div>
            ` : '';

            card.innerHTML = `
                <div class="card-header">
                    <h3>${escapeHtml(item.title)}</h3>
                </div>
                <div class="card-body">
                    <p>${escapeHtml(item.description)}</p>
                    <p class="date">${dateText}</p>
                    ${fileInfo}
                    <button class="btn download-btn" data-id="${item.id}">
                        ${item.type === 'executor' ? '📱 Baixar APK' : '📜 Baixar Script'}
                    </button>
                    ${adminButtons}
                </div>
            `;

            // Evento de download
            const downloadBtn = card.querySelector('.download-btn');
            downloadBtn.addEventListener('click', () => handleDownload(item));

            // Eventos de admin
            if (isAdmin) {
                const editBtn = card.querySelector('.edit-btn');
                const deleteBtn = card.querySelector('.delete-btn');
                
                if (editBtn) editBtn.addEventListener('click', () => showEditForm(item.id));
                if (deleteBtn) deleteBtn.addEventListener('click', () => deleteItem(item.id));
            }
            
            return card;
        }

        function handleDownload(item) {
            console.log('Iniciando download:', item);
            
            if (item.downloadType === 'file' && item.fileId) {
                // Download de arquivo local temporário
                try {
                    if (temporaryFileStorage[item.fileId]) {
                        downloadTemporaryFile(item.fileId);
                        showAlert('Download iniciado!');
                    } else {
                        showAlert('Arquivo não disponível. Faça upload novamente.', true);
                    }
                } catch (error) {
                    console.error('Erro no download:', error);
                    showAlert('Erro ao baixar arquivo: ' + error.message, true);
                }
            } else {
                // Download por URL externa
                if (item.downloadUrl && item.downloadUrl !== '#') {
                    window.open(item.downloadUrl, '_blank');
                    showAlert('Abrindo link de download...');
                } else {
                    showAlert('Link de download não disponível.', true);
                }
            }
        }

        function escapeHtml(text) {
            if (!text) return '';
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }

        function formatFileSize(bytes) {
            if (!bytes || bytes === 0) return '0 Bytes';
            const k = 1024;
            const sizes = ['Bytes', 'KB', 'MB', 'GB'];
            const i = Math.floor(Math.log(bytes) / Math.log(k));
            return parseFloat((bytes / Math.pow(k, i)).toFixed(2)) + ' ' + sizes[i];
        }

        function deleteItem(id) {
            if (!confirm('Tem certeza que deseja excluir este item?')) return;

            const item = publishedItems.find(i => i.id === id);
            if (item) {
                // Limpar arquivo temporário se existir
                if (item.fileId && temporaryFileStorage[item.fileId]) {
                    delete temporaryFileStorage[item.fileId];
                }
                
                publishedItems = publishedItems.filter(i => i.id !== id);
                if (saveItems()) {
                    displayPublishedItems();
                    showAlert('Item excluído com sucesso.');
                }
            }
        }

        function showEditForm(id) {
            const item = publishedItems.find(i => i.id === id);
            if (!item) return;

            document.getElementById('edit-id').value = id;
            document.getElementById('edit-title').value = item.title;
            document.getElementById('edit-description').value = item.description;
            document.getElementById('edit-type').value = item.type;

            if (item.fileId) {
                setUploadType('file');
                elements.editFileName.textContent = `${item.fileName} (${formatFileSize(item.fileSize)})`;
                document.getElementById('edit-download-url').value = '';
            } else {
                setUploadType('url');
                document.getElementById('edit-download-url').value = item.downloadUrl;
                elements.editFileName.textContent = 'Nenhum arquivo selecionado';
            }

            elements.uploadFormContainer.classList.add('hidden');
            elements.editFormContainer.classList.remove('hidden');
            elements.editFormContainer.scrollIntoView({ behavior: 'smooth' });
        }

        function cancelEdit() {
            elements.editFormContainer.classList.add('hidden');
            elements.uploadFormContainer.classList.remove('hidden');
            elements.editForm.reset();
            setUploadType('url');
        }

        function showAlert(message, isError = false) {
            if (!elements.uploadMessage) return;
            
            elements.uploadMessage.textContent = message;
            elements.uploadMessage.className = isError ? 'alert alert-error' : 'alert alert-success';
            elements.uploadMessage.classList.remove('hidden');
            
            setTimeout(() => {
                elements.uploadMessage.classList.add('hidden');
            }, 4000);
        }

        function handleLogout() {
            hideUploadSection();
            displayPublishedItems();
        }

        // Event Listeners
        function initializeEventListeners() {
            console.log('Inicializando event listeners...');

            // Upload type buttons
            elements.uploadTypeBtns.forEach(btn => {
                btn.addEventListener('click', () => setUploadType(btn.dataset.type));
            });

            const editUploadTypeBtns = document.querySelectorAll('#edit-form-container .upload-type-btn');
            editUploadTypeBtns.forEach(btn => {
                btn.addEventListener('click', () => setUploadType(btn.dataset.type));
            });

            // File selection
            elements.fileSelectBtn.addEventListener('click', () => elements.fileUpload.click());
            elements.fileUpload.addEventListener('change', () => handleFileSelect(elements.fileUpload, elements.fileName));
            
            elements.editFileSelectBtn.addEventListener('click', () => elements.editFileUpload.click());
            elements.editFileUpload.addEventListener('change', () => handleFileSelect(elements.editFileUpload, elements.editFileName));

            // Authentication
            elements.authForm.addEventListener('submit', (e) => {
                e.preventDefault();
                const code = elements.accessCodeInput.value.trim();
                
                if (code === SECRET_CODE) {
                    localStorage.setItem('authenticated', 'true');
                    showUploadSection();
                    elements.authMessage.classList.add('hidden');
                    displayPublishedItems();
                } else {
                    elements.authMessage.textContent = 'Código de acesso incorreto. Tente novamente.';
                    elements.authMessage.classList.remove('hidden');
                    elements.accessCodeInput.value = '';
                }
            });

            // Logout
            elements.logoutBtn.addEventListener('click', (e) => {
                e.preventDefault();
                handleLogout();
            });

            elements.logoutAdminBtn.addEventListener('click', handleLogout);

            // Upload form
            elements.uploadForm.addEventListener('submit', async (e) => {
                e.preventDefault();
                
                const title = document.getElementById('title').value.trim();
                const description = document.getElementById('description').value.trim();
                const type = document.getElementById('type').value;

                if (!title || !description || !type) {
                    showAlert('Preencha todos os campos', true);
                    return;
                }

                let downloadUrl = '', fileId = null, fileNameText = '', fileSize = 0;

                try {
                    if (currentUploadType === 'url') {
                        downloadUrl = document.getElementById('download-url').value.trim();
                        if (!downloadUrl) {
                            showAlert('Informe a URL de download', true);
                            return;
                        }
                    } else {
                        if (!elements.fileUpload.files || elements.fileUpload.files.length === 0) {
                            showAlert('Selecione um arquivo APK para upload', true);
                            return;
                        }

                        const file = elements.fileUpload.files[0];
                        if (!handleFileSelect(elements.fileUpload, elements.fileName)) {
                            return;
                        }

                        const result = await saveFileToTemporaryStorage(file);
                        fileId = result.fileId;
                        fileNameText = result.fileName;
                        fileSize = file.size;
                        downloadUrl = '#'; // Placeholder para arquivos locais
                    }

                    const newItem = {
                        id: Date.now(),
                        title,
                        description,
                        type,
                        downloadUrl,
                        downloadType: currentUploadType,
                        fileId,
                        fileName: fileNameText,
                        fileSize,
                        date: new Date().toLocaleDateString('pt-BR')
                    };

                    publishedItems.push(newItem);
                    
                    if (saveItems()) {
                        displayPublishedItems();
                        elements.uploadForm.reset();
                        elements.fileName.textContent = 'Nenhum arquivo selecionado';
                        elements.fileUpload.value = '';
                        setUploadType('url');
                        showAlert('Conteúdo publicado com sucesso!');
                    }
                } catch (error) {
                    console.error('Erro no upload:', error);
                    showAlert('Erro ao publicar conteúdo: ' + error.message, true);
                }
            });

            // Edit form
            elements.editForm.addEventListener('submit', async (e) => {
                e.preventDefault();
                
                const id = parseInt(document.getElementById('edit-id').value);
                const item = publishedItems.find(i => i.id === id);
                if (!item) return;

                item.title = document.getElementById('edit-title').value.trim();
                item.description = document.getElementById('edit-description').value.trim();
                item.type = document.getElementById('edit-type').value;

                try {
                    if (currentUploadType === 'url') {
                        // Limpar arquivo anterior se existir
                        if (item.fileId && temporaryFileStorage[item.fileId]) {
                            delete temporaryFileStorage[item.fileId];
                            item.fileId = null;
                            item.fileName = '';
                            item.fileSize = 0;
                        }
                        item.downloadUrl = document.getElementById('edit-download-url').value.trim();
                        if (!item.downloadUrl) {
                            showAlert('Informe a URL de download', true);
                            return;
                        }
                    } else {
                        if (elements.editFileUpload.files && elements.editFileUpload.files.length > 0) {
                            const file = elements.editFileUpload.files[0];
                            const result = await saveFileToTemporaryStorage(file);
                            
                            // Limpar arquivo anterior
                            if (item.fileId && temporaryFileStorage[item.fileId]) {
                                delete temporaryFileStorage[item.fileId];
                            }
                            
                            item.fileId = result.fileId;
                            item.fileName = result.fileName;
                            item.fileSize = file.size;
                            item.downloadUrl = '#'; // Placeholder para arquivos locais
                        }
                    }

                    item.downloadType = currentUploadType;
                    item.lastUpdate = new Date().toLocaleDateString('pt-BR');
                    
                    if (saveItems()) {
                        displayPublishedItems();
                        cancelEdit();
                        showAlert('Conteúdo atualizado com sucesso!');
                    }
                } catch (error) {
                    console.error('Erro na edição:', error);
                    showAlert('Erro ao atualizar conteúdo: ' + error.message, true);
                }
            });

            // Cancel edit
            elements.cancelEditBtn.addEventListener('click', cancelEdit);

            // Add new item
            elements.addItemBtn.addEventListener('click', () => {
                cancelEdit();
                elements.uploadFormContainer.scrollIntoView({ behavior: 'smooth' });
            });
        }

        // Inicializar a aplicação
        initializeEventListeners();
        checkAuthStatus();
        displayPublishedItems();
        setUploadType('url');
        console.log('Aplicação inicializada com sucesso!');
    });

    // Tratamento de erros globais
    window.addEventListener('error', (e) => {
        console.error('Erro global:', e.error);
    });
    </script>
</body>
</html>
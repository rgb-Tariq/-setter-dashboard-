# -setter-dashboard-<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard Setters - Connecté</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body { font-family: 'Segoe UI', sans-serif; background: #0a0a0a; min-height: 100vh; padding: 20px; color: #fff; }
        
        .container { max-width: 1400px; margin: 0 auto; }
        
        /* Login Screen */
        .login-container { 
            display: flex; 
            justify-content: center; 
            align-items: center; 
            min-height: 100vh; 
        }
        
        .login-box { 
            background: #1a1a1a; 
            padding: 40px; 
            border-radius: 15px; 
            box-shadow: 0 0 30px rgba(255,0,0,0.3); 
            border: 1px solid rgba(255,0,0,0.2); 
            width: 100%; 
            max-width: 400px; 
        }
        
        .login-box h1 { color: #FF0000; margin-bottom: 20px; text-align: center; text-shadow: 0 0 20px rgba(255,0,0,0.8); }
        
        .login-form-group { margin-bottom: 20px; }
        
        .login-form-group label { display: block; margin-bottom: 8px; color: #fff; font-weight: 600; }
        
        .login-form-group input { 
            width: 100%; 
            padding: 12px; 
            border: 2px solid rgba(255,0,0,0.3); 
            border-radius: 8px; 
            background: #0a0a0a; 
            color: #fff; 
            font-size: 1em; 
        }
        
        .login-form-group input:focus { outline: none; border-color: #FF0000; box-shadow: 0 0 15px rgba(255,0,0,0.4); }
        
        .login-btn { 
            width: 100%; 
            background: #FF0000; 
            color: white; 
            border: none; 
            padding: 15px; 
            border-radius: 10px; 
            font-size: 1.1em; 
            font-weight: 600; 
            cursor: pointer; 
            transition: all 0.3s; 
            box-shadow: 0 0 30px rgba(255,0,0,0.5); 
        }
        
        .login-btn:hover { transform: translateY(-2px); box-shadow: 0 0 40px rgba(255,0,0,0.8); }
        
        .error-message { color: #FF0000; margin-top: 10px; text-align: center; }
        
        .user-info { 
            display: flex; 
            justify-content: space-between; 
            align-items: center; 
            margin-bottom: 20px; 
            padding: 15px; 
            background: #1a1a1a; 
            border-radius: 10px; 
            border: 1px solid rgba(255,0,0,0.2); 
        }
        
        .user-info span { color: #999; }
        
        .user-info strong { color: #FF0000; }
        
        .logout-btn { 
            background: #1a1a1a; 
            color: #FF0000; 
            border: 2px solid #FF0000; 
            padding: 10px 20px; 
            border-radius: 8px; 
            cursor: pointer; 
            font-weight: 600; 
            transition: all 0.3s; 
        }
        
        .logout-btn:hover { background: #FF0000; color: white; }
        
        .header { background: #1a1a1a; padding: 30px; border-radius: 15px; margin-bottom: 30px; box-shadow: 0 0 30px rgba(255,0,0,0.3); border: 1px solid rgba(255,0,0,0.2); }
        
        .header h1 { color: #FF0000; font-size: 2.5em; margin-bottom: 10px; text-shadow: 0 0 20px rgba(255,0,0,0.8); }
        
        .header p { color: #999; font-size: 1.1em; }
        
        .tabs { display: flex; gap: 10px; margin-bottom: 30px; flex-wrap: wrap; }
        
        .tab-button { background: #1a1a1a; border: 1px solid rgba(255,0,0,0.3); color: #fff; padding: 15px 30px; border-radius: 10px; font-size: 1.1em; font-weight: 600; cursor: pointer; transition: all 0.3s; box-shadow: 0 0 15px rgba(255,0,0,0.1); }
        
        .tab-button:hover { transform: translateY(-2px); box-shadow: 0 0 25px rgba(255,0,0,0.4); }
        
        .tab-button.active { background: #FF0000; box-shadow: 0 0 30px rgba(255,0,0,0.6); }
        
        .tab-content { display: none; }
        
        .tab-content.active { display: block; }
        
        .form-section { background: #1a1a1a; padding: 30px; border-radius: 15px; margin-bottom: 20px; box-shadow: 0 0 20px rgba(255,0,0,0.2); border: 1px solid rgba(255,0,0,0.2); }
        
        .form-section h2 { color: #FF0000; margin-bottom: 20px; font-size: 1.8em; border-bottom: 3px solid #FF0000; padding-bottom: 10px; text-shadow: 0 0 15px rgba(255,0,0,0.6); }
        
        .form-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; margin-bottom: 20px; }
        
        .form-group { display: flex; flex-direction: column; }
        
        .form-group label { font-weight: 600; margin-bottom: 8px; color: #fff; }
        
        .form-group input, .form-group select, .form-group textarea { padding: 12px; border: 2px solid rgba(255,0,0,0.3); border-radius: 8px; font-size: 1em; background: #0a0a0a; color: #fff; transition: all 0.3s; font-family: inherit; }
        
        .form-group input:focus, .form-group select:focus, .form-group textarea:focus { outline: none; border-color: #FF0000; box-shadow: 0 0 15px rgba(255,0,0,0.4); }
        
        .form-group textarea { resize: vertical; min-height: 80px; }
        
        .radio-group { display: flex; gap: 20px; margin-top: 8px; }
        
        .radio-group label { display: flex; align-items: center; gap: 8px; font-weight: normal; cursor: pointer; }
        
        .submit-btn { background: #FF0000; color: white; border: none; padding: 15px 40px; border-radius: 10px; font-size: 1.2em; font-weight: 600; cursor: pointer; transition: all 0.3s; box-shadow: 0 0 30px rgba(255,0,0,0.5); width: 100%; }
        
        .submit-btn:hover { transform: translateY(-2px); box-shadow: 0 0 40px rgba(255,0,0,0.8); }
        
        .stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; margin-bottom: 30px; }
        
        .stat-card { background: #1a1a1a; padding: 25px; border-radius: 15px; box-shadow: 0 0 20px rgba(255,0,0,0.2); text-align: center; border: 1px solid rgba(255,0,0,0.2); }
        
        .stat-card h3 { color: #999; font-size: 0.9em; margin-bottom: 10px; text-transform: uppercase; letter-spacing: 1px; }
        
        .stat-card .value { font-size: 2.5em; font-weight: 700; color: #FF0000; margin-bottom: 5px; text-shadow: 0 0 20px rgba(255,0,0,0.6); }
        
        .stat-card .subtitle { color: #666; font-size: 0.9em; }
        
        .setter-list { background: #1a1a1a; padding: 30px; border-radius: 15px; box-shadow: 0 0 20px rgba(255,0,0,0.2); margin-bottom: 20px; border: 1px solid rgba(255,0,0,0.2); }
        
        .setter-list h2 { color: #FF0000; margin-bottom: 20px; font-size: 1.8em; text-shadow: 0 0 15px rgba(255,0,0,0.6); }
        
        .setter-item { background: #0a0a0a; padding: 20px; border-radius: 10px; margin-bottom: 15px; border-left: 5px solid #FF0000; box-shadow: 0 0 15px rgba(255,0,0,0.15); }
        
        .setter-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px; flex-wrap: wrap; }
        
        .setter-name { font-size: 1.3em; font-weight: 700; color: #fff; }
        
        .setter-ca { font-size: 1.5em; font-weight: 700; color: #FF0000; text-shadow: 0 0 15px rgba(255,0,0,0.6); }
        
        .setter-metrics { display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 15px; }
        
        .metric { display: flex; flex-direction: column; }
        
        .metric-label { font-size: 0.85em; color: #999; margin-bottom: 5px; }
        
        .metric-value { font-size: 1.2em; font-weight: 600; color: #fff; }
        
        .export-section { background: #1a1a1a; padding: 30px; border-radius: 15px; box-shadow: 0 0 20px rgba(255,0,0,0.2); margin-bottom: 20px; border: 1px solid rgba(255,0,0,0.2); }
        
        .export-section h2 { color: #FF0000; text-shadow: 0 0 15px rgba(255,0,0,0.6); margin-bottom: 15px; }
        
        .export-btn { background: #FF0000; color: white; border: none; padding: 15px 40px; border-radius: 10px; font-size: 1.1em; font-weight: 600; cursor: pointer; transition: all 0.3s; margin-right: 10px; margin-bottom: 10px; box-shadow: 0 0 20px rgba(255,0,0,0.4); }
        
        .export-btn:hover { box-shadow: 0 0 30px rgba(255,0,0,0.7); transform: translateY(-2px); }
        
        .delete-btn { background: #1a1a1a; color: #FF0000; border: 2px solid #FF0000; padding: 15px 40px; border-radius: 10px; font-size: 1.1em; font-weight: 600; cursor: pointer; transition: all 0.3s; }
        
        .delete-btn:hover { background: #FF0000; color: white; box-shadow: 0 0 30px rgba(255,0,0,0.7); transform: translateY(-2px); }
        
        .insights { background: #1a1a1a; padding: 30px; border-radius: 15px; box-shadow: 0 0 20px rgba(255,0,0,0.2); margin-bottom: 20px; border: 1px solid rgba(255,0,0,0.2); }
        
        .insights h2 { color: #FF0000; margin-bottom: 20px; font-size: 1.8em; text-shadow: 0 0 15px rgba(255,0,0,0.6); }
        
        .insight-item { background: #0a0a0a; padding: 15px; border-radius: 8px; margin-bottom: 10px; border-left: 4px solid #FF0000; color: #fff; box-shadow: 0 0 10px rgba(255,0,0,0.1); }
        
        .insight-item.warning { border-left-color: #ffc107; box-shadow: 0 0 10px rgba(255,193,7,0.1); }
        
        .top-performer { border-left-color: #FFD700; background: linear-gradient(135deg, rgba(255,215,0,0.1) 0%, rgba(255,215,0,0.05) 100%); box-shadow: 0 0 20px rgba(255,215,0,0.2); }
        
        .empty-state { text-align: center; padding: 60px 20px; color: #666; }
        
        .loading { text-align: center; padding: 20px; color: #999; }
        
        /* Mobile Optimizations */
        @media (max-width: 768px) {
            body { padding: 10px; }
            
            .container { max-width: 100%; }
            
            .header { padding: 20px; }
            .header h1 { font-size: 1.8em; }
            .header p { font-size: 0.9em; }
            
            .login-box { padding: 25px; margin: 10px; }
            
            .user-info { 
                flex-direction: column; 
                gap: 10px; 
                text-align: center; 
            }
            .user-info span { display: block; margin: 5px 0; }
            
            .tabs { 
                flex-direction: column; 
                gap: 8px; 
            }
            .tab-button { 
                width: 100%; 
                padding: 12px 20px; 
                font-size: 1em; 
            }
            
            .form-section { padding: 20px; }
            .form-section h2 { font-size: 1.4em; }
            .form-grid, .stats-grid, .setter-metrics { 
                grid-template-columns: 1fr; 
                gap: 15px; 
            }
            
            .form-group input, .form-group select, .form-group textarea {
                font-size: 16px; /* Évite le zoom sur iOS */
            }
            
            .radio-group { 
                flex-direction: column; 
                gap: 10px; 
            }
            
            .submit-btn, .export-btn, .delete-btn {
                width: 100%;
                margin: 5px 0;
                padding: 12px 20px;
                font-size: 1em;
            }
            
            .stat-card { padding: 20px; }
            .stat-card .value { font-size: 2em; }
            
            .setter-item { padding: 15px; }
            .setter-header { flex-direction: column; align-items: flex-start; gap: 10px; }
            
            .export-section { padding: 20px; }
            
            .insights { padding: 20px; }
            .insights h2 { font-size: 1.4em; }
            
            #pasteData {
                font-size: 14px;
                min-height: 120px;
            }
        }
        
        @media (max-width: 480px) {
            .header h1 { font-size: 1.5em; }
            .form-section h2 { font-size: 1.2em; }
            .tab-button { font-size: 0.9em; padding: 10px 15px; }
        }
    </style>
</head>
<body>
    <!-- Écran de login -->
    <div id="loginScreen" class="login-container">
        <div class="login-box">
            <h1>🔐 Connexion</h1>
            <form id="loginForm">
                <div class="login-form-group">
                    <label>Nom d'utilisateur</label>
                    <input type="text" id="loginUsername" required autocomplete="username">
                </div>
                <div class="login-form-group">
                    <label>Mot de passe</label>
                    <input type="password" id="loginPassword" required autocomplete="current-password">
                </div>
                <button type="submit" class="login-btn">Se connecter</button>
                <div id="loginError" class="error-message"></div>
            </form>
        </div>
    </div>

    <!-- Dashboard principal -->
    <div id="dashboard" style="display: none;">
        <div class="container">
            <div class="user-info">
                <div>
                    <span>Connecté en tant que: <strong id="currentUser"></strong></span>
                    <span style="margin-left: 20px; color: #666;">Rôle: <strong id="currentRole"></strong></span>
                </div>
                <button class="logout-btn" onclick="logout()">Déconnexion</button>
            </div>

            <div class="header">
                <h1>📊 Dashboard Setters</h1>
                <p>Tracker de performance quotidienne - Cashflow & Qualité</p>
            </div>

            <div class="tabs">
                <button class="tab-button active" onclick="switchTab('saisie')">📝 Saisie</button>
                <button class="tab-button" onclick="switchTab('analytics')">📈 Analytics</button>
                <button class="tab-button" onclick="switchTab('export')">💾 Export</button>
                <button class="tab-button" id="adminTab" onclick="switchTab('admin')" style="display: none;">⚙️ Admin</button>
            </div>

            <div id="saisie" class="tab-content active">
                <form id="dailyForm">
                    <div class="form-section">
                        <h2>📋 Informations de base</h2>
                        <div class="form-grid">
                            <div class="form-group"><label>Nom du Setter *</label><input type="text" id="setterName" required></div>
                            <div class="form-group"><label>Date *</label><input type="date" id="date" required></div>
                            <div class="form-group"><label>Heures travaillées *</label><input type="number" id="heuresTravaillees" step="0.5" min="0" required></div>
                        </div>
                    </div>

                    <div class="form-section">
                        <h2>🔥 A. Volume d'activité</h2>
                        <div class="form-grid">
                            <div class="form-group"><label>Outbounds envoyés *</label><input type="number" id="outbounds" min="0" required></div>
                            <div class="form-group"><label>Inbounds reçus *</label><input type="number" id="inbounds" min="0" required></div>
                            <div class="form-group"><label>Conversations actives *</label><input type="number" id="conversations" min="0" required></div>
                            <div class="form-group"><label>Follow-ups envoyés *</label><input type="number" id="followups" min="0" required></div>
                        </div>
                    </div>

                    <div class="form-section">
                        <h2>🎯 B. Qualité des leads</h2>
                        <div class="form-grid">
                            <div class="form-group"><label>Leads qualifiés *</label><input type="number" id="leadsQualifies" min="0" required></div>
                            <div class="form-group"><label>Qualité moyenne (/10) *</label><input type="number" id="qualiteMoyenne" min="0" max="10" step="0.1" required></div>
                            <div class="form-group">
                                <label>Objection principale *</label>
                                <select id="objectionPrincipale" required>
                                    <option value="">Sélectionner...</option>
                                    <option value="Trop cher">Trop cher</option>
                                    <option value="Pas maintenant">Pas maintenant</option>
                                    <option value="Pas convaincu">Pas convaincu</option>
                                    <option value="Pas la cible">Pas la cible</option>
                                    <option value="Juste curieux">Juste curieux</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label>Source principale *</label>
                                <select id="sourcePrincipale" required>
                                    <option value="">Sélectionner...</option>
                                    <option value="Reels">Reels</option>
                                    <option value="TikTok">TikTok</option>
                                    <option value="YouTube">YouTube</option>
                                    <option value="Ads">Ads</option>
                                    <option value="Autre">Autre</option>
                                </select>
                            </div>
                        </div>
                    </div>

                    <div class="form-section">
                        <h2>💰 C. Cashflow (150€)</h2>
                        <div class="form-grid">
                            <div class="form-group"><label>Personnes intéressées *</label><input type="number" id="personnesInteressees" min="0" required></div>
                            <div class="form-group"><label>Ventes réelles *</label><input type="number" id="ventesReelles" min="0" required></div>
                            <div class="form-group"><label>CA généré (auto)</label><input type="text" id="montantGenere" readonly style="background: #0a0a0a; font-weight: 700; color: #FF0000; font-size: 1.2em; text-shadow: 0 0 15px rgba(255,0,0,0.6); border: 2px solid rgba(255,0,0,0.5);"></div>
                        </div>
                    </div>

                    <div class="form-section">
                        <h2>📞 D. Qualité des Calls</h2>
                        <div class="form-grid">
                            <div class="form-group"><label>Calls envoyés au closer *</label><input type="number" id="callsEnvoyes" min="0" required></div>
                            <div class="form-group">
                                <label>Calls bien qualifiés ? *</label>
                                <div class="radio-group">
                                    <label><input type="radio" name="callsQualifies" value="Oui" required> Oui</label>
                                    <label><input type="radio" name="callsQualifies" value="Non"> Non</label>
                                </div>
                            </div>
                            <div class="form-group"><label>Retour closer (/10) *</label><input type="number" id="retourCloser" min="1" max="10" step="0.1" required></div>
                        </div>
                    </div>

                    <div class="form-section">
                        <h2>🎯 E. Contrôle & Optimisation</h2>
                        <div class="form-grid">
                            <div class="form-group">
                                <label>Script respecté ? *</label>
                                <div class="radio-group">
                                    <label><input type="radio" name="scriptRespecte" value="Oui" required> Oui</label>
                                    <label><input type="radio" name="scriptRespecte" value="Non"> Non</label>
                                </div>
                            </div>
                        </div>
                        <div class="form-grid">
                            <div class="form-group"><label>Objection bloquante</label><textarea id="objectionBloquante"></textarea></div>
                            <div class="form-group"><label>WIN du jour 🏆</label><textarea id="winDuJour"></textarea></div>
                            <div class="form-group"><label>FAIL du jour</label><textarea id="failDuJour"></textarea></div>
                            <div class="form-group"><label>Liens conversations</label><textarea id="liensConversations"></textarea></div>
                        </div>
                    </div>

                    <button type="submit" class="submit-btn">💾 Enregistrer la journée</button>
                </form>
            </div>

            <div id="analytics" class="tab-content">
                <div class="loading" id="analyticsLoading">Chargement des données...</div>
                <div class="stats-grid" id="globalStats"></div>
                <div class="insights" id="insights"></div>
                <div class="setter-list" id="setterList"></div>
            </div>

            <div id="export" class="tab-content">
                <div class="export-section">
                    <h2>💾 Export & Gestion</h2>
                    <p style="color: #999; margin-bottom: 20px;">Exporte toutes les données en CSV pour analyse.</p>
                    <button class="export-btn" onclick="exportToCSV()">📊 Exporter CSV</button>
                    <button class="export-btn" onclick="exportToJSON()">📄 Exporter JSON</button>
                    <button class="export-btn" onclick="copyToClipboard()">📋 Copier les données</button>
                    <button class="delete-btn" onclick="deleteAllData()" id="deleteBtn" style="display: none;">🗑️ Supprimer tout</button>
                    
                    <div style="margin-top: 30px; padding: 20px; background: #0a0a0a; border-radius: 10px; border: 1px solid rgba(255,0,0,0.2);">
                        <h3 style="margin-bottom: 10px; color: #FF0000;">📊 Statistiques</h3>
                        <p id="totalEntries" style="font-size: 1.2em; color: #fff;"></p>
                    </div>

                    <div style="margin-top: 30px; padding: 20px; background: #0a0a0a; border-radius: 10px; border: 1px solid rgba(255,0,0,0.2);">
                        <h3 style="margin-bottom: 15px; color: #FF0000;">📥 Coller & Importer</h3>
                        <p style="color: #999; margin-bottom: 15px;">Collez ici des données JSON pour les importer directement</p>
                        <textarea id="pasteData" placeholder='Collez vos données JSON ici... Exemple: [{"setterName":"Hugo","date":"2025-12-05",...}]' style="width: 100%; min-height: 150px; padding: 12px; border: 2px solid rgba(255,0,0,0.3); border-radius: 8px; background: #1a1a1a; color: #fff; font-family: monospace; font-size: 0.9em; margin-bottom: 15px;"></textarea>
                        <div style="display: flex; gap: 10px; align-items: center;">
                            <button class="export-btn" onclick="importFromPaste()" style="width: auto;">📥 Importer depuis le presse-papiers</button>
                            <select id="pasteUserId" style="padding: 10px; border: 2px solid rgba(255,0,0,0.3); border-radius: 8px; background: #1a1a1a; color: #fff;">
                                <option value="">Utilisateur actuel</option>
                            </select>
                        </div>
                        <div id="pasteResult" style="margin-top: 15px;"></div>
                    </div>
                </div>
            </div>

            <div id="admin" class="tab-content">
                <div class="form-section">
                    <h2>👥 Gestion des Utilisateurs</h2>
                    <div class="form-grid">
                        <div class="form-group">
                            <label>Nom d'utilisateur</label>
                            <input type="text" id="newUsername" placeholder="nom_utilisateur">
                        </div>
                        <div class="form-group">
                            <label>Mot de passe</label>
                            <input type="password" id="newPassword" placeholder="motdepasse123">
                        </div>
                        <div class="form-group">
                            <label>Rôle</label>
                            <select id="newRole">
                                <option value="setter">Setter</option>
                                <option value="admin">Admin</option>
                            </select>
                        </div>
                    </div>
                    <button class="export-btn" onclick="createUser()" style="width: auto; margin-top: 10px;">➕ Créer un utilisateur</button>
                    <div id="userList" style="margin-top: 30px;"></div>
                </div>

                <div class="form-section">
                    <h2>📥 Import de Données</h2>
                    <p style="color: #999; margin-bottom: 20px;">Importez des données depuis un fichier CSV ou JSON.</p>
                    <div class="form-grid">
                        <div class="form-group">
                            <label>Fichier à importer (CSV ou JSON)</label>
                            <input type="file" id="importFile" accept=".csv,.json" onchange="handleFileSelect(event)">
                        </div>
                        <div class="form-group">
                            <label>Importer pour l'utilisateur (optionnel)</label>
                            <select id="importUserId">
                                <option value="">Utilisateur actuel</option>
                            </select>
                        </div>
                    </div>
                    <button class="export-btn" onclick="importData()" id="importBtn" disabled style="width: auto; margin-top: 10px;">📥 Importer les données</button>
                    <div id="importResult" style="margin-top: 20px;"></div>
                </div>
            </div>
        </div>
    </div>

    <script>
        const API_URL = window.location.origin;
        let authToken = localStorage.getItem('authToken');
        let currentUser = null;

        // Vérifier si l'utilisateur est déjà connecté
        async function checkAuth() {
            if (!authToken) {
                showLogin();
                return;
            }

            try {
                const response = await fetch(`${API_URL}/api/auth/verify`, {
                    headers: { 'Authorization': `Bearer ${authToken}` }
                });

                if (response.ok) {
                    const data = await response.json();
                    currentUser = data.user;
                    showDashboard();
                } else {
                    showLogin();
                }
            } catch (error) {
                console.error('Erreur vérification auth:', error);
                showLogin();
            }
        }

        // Login
        document.getElementById('loginForm').addEventListener('submit', async (e) => {
            e.preventDefault();
            const username = document.getElementById('loginUsername').value;
            const password = document.getElementById('loginPassword').value;
            const errorDiv = document.getElementById('loginError');

            try {
                const response = await fetch(`${API_URL}/api/auth/login`, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({ username, password })
                });

                const data = await response.json();

                if (response.ok) {
                    authToken = data.token;
                    currentUser = data.user;
                    localStorage.setItem('authToken', authToken);
                    showDashboard();
                } else {
                    errorDiv.textContent = data.error || 'Erreur de connexion';
                }
            } catch (error) {
                errorDiv.textContent = 'Erreur de connexion au serveur';
            }
        });

        // Logout
        function logout() {
            localStorage.removeItem('authToken');
            authToken = null;
            currentUser = null;
            showLogin();
        }

        function showLogin() {
            document.getElementById('loginScreen').style.display = 'flex';
            document.getElementById('dashboard').style.display = 'none';
        }

        function showDashboard() {
            document.getElementById('loginScreen').style.display = 'none';
            document.getElementById('dashboard').style.display = 'block';
            document.getElementById('currentUser').textContent = currentUser.username;
            document.getElementById('currentRole').textContent = currentUser.role;
            
            if (currentUser.role === 'admin') {
                document.getElementById('deleteBtn').style.display = 'inline-block';
                document.getElementById('adminTab').style.display = 'inline-block';
                loadUsers();
                loadUsersForImport();
                loadUsersForPaste();
            } else {
                loadUsersForPaste();
            }
        }

        // Date par défaut
        document.getElementById('date').valueAsDate = new Date();

        // Calcul CA
        document.getElementById('ventesReelles').addEventListener('input', function() {
            document.getElementById('montantGenere').value = (parseInt(this.value) || 0) * 150 + ' €';
        });

        // Switch tabs
        function switchTab(tabName) {
            document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.tab-button').forEach(b => b.classList.remove('active'));
            document.getElementById(tabName).classList.add('active');
            event.target.classList.add('active');

            if (tabName === 'analytics') loadAnalytics();
            if (tabName === 'export') {
                updateExportStats();
                loadUsersForPaste();
            }
            if (tabName === 'admin' && currentUser.role === 'admin') {
                loadUsers();
                loadUsersForImport();
            }
        }

        // Enregistrer les données
        document.getElementById('dailyForm').addEventListener('submit', async function(e) {
            e.preventDefault();

            const data = {
                timestamp: new Date().toISOString(),
                setterName: document.getElementById('setterName').value,
                date: document.getElementById('date').value,
                heuresTravaillees: parseFloat(document.getElementById('heuresTravaillees').value),
                outbounds: parseInt(document.getElementById('outbounds').value),
                inbounds: parseInt(document.getElementById('inbounds').value),
                conversations: parseInt(document.getElementById('conversations').value),
                followups: parseInt(document.getElementById('followups').value),
                leadsQualifies: parseInt(document.getElementById('leadsQualifies').value),
                qualiteMoyenne: parseFloat(document.getElementById('qualiteMoyenne').value),
                objectionPrincipale: document.getElementById('objectionPrincipale').value,
                sourcePrincipale: document.getElementById('sourcePrincipale').value,
                personnesInteressees: parseInt(document.getElementById('personnesInteressees').value),
                ventesReelles: parseInt(document.getElementById('ventesReelles').value),
                montantGenere: parseInt(document.getElementById('ventesReelles').value) * 150,
                callsEnvoyes: parseInt(document.getElementById('callsEnvoyes').value),
                callsQualifies: document.querySelector('input[name="callsQualifies"]:checked').value,
                retourCloser: parseFloat(document.getElementById('retourCloser').value),
                scriptRespecte: document.querySelector('input[name="scriptRespecte"]:checked').value,
                objectionBloquante: document.getElementById('objectionBloquante').value,
                winDuJour: document.getElementById('winDuJour').value,
                failDuJour: document.getElementById('failDuJour').value,
                liensConversations: document.getElementById('liensConversations').value
            };

            try {
                const response = await fetch(`${API_URL}/api/data`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': `Bearer ${authToken}`
                    },
                    body: JSON.stringify(data)
                });

                if (response.ok) {
                    alert('✅ Données enregistrées avec succès !');
                    this.reset();
                    document.getElementById('date').valueAsDate = new Date();
                } else {
                    const error = await response.json();
                    alert('❌ Erreur: ' + (error.error || 'Erreur inconnue'));
                }
            } catch (error) {
                alert('❌ Erreur de connexion au serveur');
            }
        });

        // Charger analytics
        async function loadAnalytics() {
            document.getElementById('analyticsLoading').style.display = 'block';
            
            try {
                const response = await fetch(`${API_URL}/api/data`, {
                    headers: { 'Authorization': `Bearer ${authToken}` }
                });

                if (!response.ok) throw new Error('Erreur chargement');

                const allData = await response.json();
                document.getElementById('analyticsLoading').style.display = 'none';

                if (allData.length === 0) {
                    document.getElementById('globalStats').innerHTML = '<div class="empty-state"><h3>Aucune donnée</h3></div>';
                    document.getElementById('insights').innerHTML = '';
                    document.getElementById('setterList').innerHTML = '';
                    return;
                }

                const totalCA = allData.reduce((s, d) => s + d.montantGenere, 0);
                const totalVentes = allData.reduce((s, d) => s + d.ventesReelles, 0);
                const totalHeures = allData.reduce((s, d) => s + d.heuresTravaillees, 0);
                const totalLeads = allData.reduce((s, d) => s + d.leadsQualifies, 0);
                const avgQualite = (allData.reduce((s, d) => s + d.qualiteMoyenne, 0) / allData.length).toFixed(1);
                const caParHeure = totalHeures > 0 ? (totalCA / totalHeures).toFixed(0) : 0;

                document.getElementById('globalStats').innerHTML = `
                    <div class="stat-card"><h3>CA Total</h3><div class="value">${totalCA.toLocaleString()} €</div><div class="subtitle">${allData.length} journées</div></div>
                    <div class="stat-card"><h3>Ventes</h3><div class="value">${totalVentes}</div><div class="subtitle">${totalLeads} leads</div></div>
                    <div class="stat-card"><h3>CA/Heure</h3><div class="value">${caParHeure} €</div><div class="subtitle">${totalHeures}h</div></div>
                    <div class="stat-card"><h3>Qualité</h3><div class="value">${avgQualite}/10</div><div class="subtitle">Moyenne</div></div>
                `;

                const setterPerf = {};
                allData.forEach(d => {
                    if (!setterPerf[d.setterName]) setterPerf[d.setterName] = { ca: 0 };
                    setterPerf[d.setterName].ca += d.montantGenere;
                });

                const topSetter = Object.entries(setterPerf).sort((a, b) => b[1].ca - a[1].ca)[0];
                const objections = {};
                allData.forEach(d => objections[d.objectionPrincipale] = (objections[d.objectionPrincipale] || 0) + 1);
                const topObjection = Object.entries(objections).sort((a, b) => b[1] - a[1])[0];
                const totalInteresses = allData.reduce((s, d) => s + d.personnesInteressees, 0);
                const tauxConv = totalInteresses > 0 ? ((totalVentes / totalInteresses) * 100).toFixed(1) : 0;

                let html = '<h2>💡 Insights</h2>';
                if (topSetter) html += `<div class="insight-item top-performer">🏆 <strong>${topSetter[0]}</strong> : ${topSetter[1].ca.toLocaleString()} € générés</div>`;
                if (topObjection) html += `<div class="insight-item warning">⚠️ Objection fréquente : <strong>"${topObjection[0]}"</strong> (${topObjection[1]}x)</div>`;
                html += `<div class="insight-item">🎯 Taux conversion : <strong>${tauxConv}%</strong></div>`;
                document.getElementById('insights').innerHTML = html;

                const setterPerf2 = {};
                allData.forEach(d => {
                    if (!setterPerf2[d.setterName]) setterPerf2[d.setterName] = { ca: 0, ventes: 0, heures: 0, leadsQualifies: 0, qualite: [] };
                    setterPerf2[d.setterName].ca += d.montantGenere;
                    setterPerf2[d.setterName].ventes += d.ventesReelles;
                    setterPerf2[d.setterName].heures += d.heuresTravaillees;
                    setterPerf2[d.setterName].leadsQualifies += d.leadsQualifies;
                    setterPerf2[d.setterName].qualite.push(d.qualiteMoyenne);
                });

                const setterArray = Object.entries(setterPerf2).sort((a, b) => b[1].ca - a[1].ca);
                let listHtml = '<h2>👥 Performance par Setter</h2>';
                setterArray.forEach(([name, perf]) => {
                    const avgQ = (perf.qualite.reduce((a, b) => a + b, 0) / perf.qualite.length).toFixed(1);
                    const caH = perf.heures > 0 ? (perf.ca / perf.heures).toFixed(0) : 0;
                    const taux = perf.leadsQualifies > 0 ? ((perf.ventes / perf.leadsQualifies) * 100).toFixed(1) : 0;
                    listHtml += `
                        <div class="setter-item">
                            <div class="setter-header">
                                <div class="setter-name">${name}</div>
                                <div class="setter-ca">${perf.ca.toLocaleString()} €</div>
                            </div>
                            <div class="setter-metrics">
                                <div class="metric"><div class="metric-label">Ventes</div><div class="metric-value">${perf.ventes}</div></div>
                                <div class="metric"><div class="metric-label">CA/Heure</div><div class="metric-value">${caH} €</div></div>
                                <div class="metric"><div class="metric-label">Qualité</div><div class="metric-value">${avgQ}/10</div></div>
                                <div class="metric"><div class="metric-label">Taux Conv.</div><div class="metric-value">${taux}%</div></div>
                            </div>
                        </div>
                    `;
                });
                document.getElementById('setterList').innerHTML = listHtml;
            } catch (error) {
                document.getElementById('analyticsLoading').innerHTML = '<div class="error-message">Erreur de chargement des données</div>';
            }
        }

        // Export CSV
        async function exportToCSV() {
            try {
                const response = await fetch(`${API_URL}/api/data`, {
                    headers: { 'Authorization': `Bearer ${authToken}` }
                });
                const allData = await response.json();
                
                if (allData.length === 0) { alert('❌ Aucune donnée'); return; }

                const headers = ['Timestamp','Setter','Date','Heures','Outbounds','Inbounds','Conversations','Follow-ups','Leads','Qualité','Objection','Source','Intéressés','Ventes','CA','Calls','Calls OK','Retour','Script','Obj Bloquante','Win','Fail','Liens'];
                let csv = headers.join(',') + '\n';
                allData.forEach(d => {
                    csv += [d.timestamp,d.setterName,d.date,d.heuresTravaillees,d.outbounds,d.inbounds,d.conversations,d.followups,d.leadsQualifies,d.qualiteMoyenne,d.objectionPrincipale,d.sourcePrincipale,d.personnesInteressees,d.ventesReelles,d.montantGenere,d.callsEnvoyes,d.callsQualifies,d.retourCloser,d.scriptRespecte,`"${(d.objectionBloquante||'').replace(/"/g,'""')}"`, `"${(d.winDuJour||'').replace(/"/g,'""')}"`,'\"'+(d.failDuJour||'').replace(/"/g,'""')+'\"',`"${(d.liensConversations||'').replace(/"/g,'""')}"`].join(',') + '\n';
                });

                const blob = new Blob([csv], { type: 'text/csv' });
                const link = document.createElement('a');
                link.href = URL.createObjectURL(blob);
                link.download = `setter-data-${new Date().toISOString().split('T')[0]}.csv`;
                link.click();
            } catch (error) {
                alert('❌ Erreur lors de l\'export');
            }
        }

        // Export JSON
        async function exportToJSON() {
            try {
                const response = await fetch(`${API_URL}/api/data`, {
                    headers: { 'Authorization': `Bearer ${authToken}` }
                });
                const allData = await response.json();
                
                if (allData.length === 0) { alert('❌ Aucune donnée'); return; }

                const blob = new Blob([JSON.stringify(allData, null, 2)], { type: 'application/json' });
                const link = document.createElement('a');
                link.href = URL.createObjectURL(blob);
                link.download = `setter-data-${new Date().toISOString().split('T')[0]}.json`;
                link.click();
            } catch (error) {
                alert('❌ Erreur lors de l\'export');
            }
        }

        // Supprimer toutes les données
        async function deleteAllData() {
            if (!confirm('⚠️ Supprimer TOUTES les données ?')) return;
            if (!confirm('🚨 DERNIÈRE CONFIRMATION !')) return;

            try {
                const response = await fetch(`${API_URL}/api/data`, {
                    method: 'DELETE',
                    headers: { 'Authorization': `Bearer ${authToken}` }
                });

                if (response.ok) {
                    alert('✅ Données supprimées');
                    updateExportStats();
                    loadAnalytics();
                } else {
                    alert('❌ Erreur lors de la suppression');
                }
            } catch (error) {
                alert('❌ Erreur de connexion');
            }
        }

        // Mettre à jour les stats d'export
        async function updateExportStats() {
            try {
                const response = await fetch(`${API_URL}/api/data`, {
                    headers: { 'Authorization': `Bearer ${authToken}` }
                });
                const allData = await response.json();
                document.getElementById('totalEntries').textContent = `${allData.length} entrées enregistrées`;
            } catch (error) {
                document.getElementById('totalEntries').textContent = 'Erreur de chargement';
            }
        }

        // Copier les données dans le presse-papiers
        async function copyToClipboard() {
            try {
                const response = await fetch(`${API_URL}/api/data`, {
                    headers: { 'Authorization': `Bearer ${authToken}` }
                });
                const allData = await response.json();
                
                if (allData.length === 0) {
                    alert('❌ Aucune donnée à copier');
                    return;
                }

                const jsonString = JSON.stringify(allData, null, 2);
                
                // Utiliser l'API Clipboard moderne
                if (navigator.clipboard && navigator.clipboard.writeText) {
                    await navigator.clipboard.writeText(jsonString);
                    alert('✅ Données copiées dans le presse-papiers !');
                } else {
                    // Fallback pour les navigateurs plus anciens
                    const textarea = document.createElement('textarea');
                    textarea.value = jsonString;
                    textarea.style.position = 'fixed';
                    textarea.style.opacity = '0';
                    document.body.appendChild(textarea);
                    textarea.select();
                    document.execCommand('copy');
                    document.body.removeChild(textarea);
                    alert('✅ Données copiées dans le presse-papiers !');
                }
            } catch (error) {
                alert('❌ Erreur lors de la copie: ' + error.message);
            }
        }

        // Charger les utilisateurs pour le paste
        async function loadUsersForPaste() {
            if (currentUser.role !== 'admin') {
                document.getElementById('pasteUserId').style.display = 'none';
                return;
            }

            try {
                const response = await fetch(`${API_URL}/api/users`, {
                    headers: { 'Authorization': `Bearer ${authToken}` }
                });
                if (!response.ok) return;
                
                const users = await response.json();
                const select = document.getElementById('pasteUserId');
                select.innerHTML = '<option value="">Utilisateur actuel</option>';
                users.forEach(user => {
                    const option = document.createElement('option');
                    option.value = user.id;
                    option.textContent = `${user.username} (${user.role})`;
                    select.appendChild(option);
                });
            } catch (error) {
                console.error('Erreur chargement utilisateurs:', error);
            }
        }

        // Importer depuis le presse-papiers collé
        async function importFromPaste() {
            const pasteText = document.getElementById('pasteData').value.trim();
            
            if (!pasteText) {
                alert('❌ Veuillez coller des données dans la zone de texte');
                return;
            }

            try {
                let data = [];
                
                // Essayer de parser comme JSON
                try {
                    const parsed = JSON.parse(pasteText);
                    if (Array.isArray(parsed)) {
                        data = parsed;
                    } else if (typeof parsed === 'object') {
                        // Si c'est un seul objet, le mettre dans un tableau
                        data = [parsed];
                    } else {
                        throw new Error('Format invalide');
                    }
                } catch (e) {
                    // Essayer de parser comme CSV
                    data = parseCSV(pasteText);
                }

                if (data.length === 0) {
                    alert('❌ Aucune donnée valide trouvée');
                    return;
                }

                // Convertir les données au bon format
                const formattedData = data.map(row => ({
                    timestamp: row.timestamp || row.Timestamp || new Date().toISOString(),
                    setterName: row.setterName || row.Setter || row.setter_name || currentUser.username,
                    date: row.date || row.Date || new Date().toISOString().split('T')[0],
                    heuresTravaillees: parseFloat(row.heuresTravaillees || row.Heures || row.heures_travaillees || 0),
                    outbounds: parseInt(row.outbounds || row.Outbounds || 0),
                    inbounds: parseInt(row.inbounds || row.Inbounds || 0),
                    conversations: parseInt(row.conversations || row.Conversations || 0),
                    followups: parseInt(row.followups || row['Follow-ups'] || row.follow_ups || 0),
                    leadsQualifies: parseInt(row.leadsQualifies || row.Leads || row.leads_qualifies || 0),
                    qualiteMoyenne: parseFloat(row.qualiteMoyenne || row.Qualité || row.qualite_moyenne || 0),
                    objectionPrincipale: row.objectionPrincipale || row.Objection || row.objection_principale || '',
                    sourcePrincipale: row.sourcePrincipale || row.Source || row.source_principale || '',
                    personnesInteressees: parseInt(row.personnesInteressees || row.Intéressés || row.personnes_interessees || 0),
                    ventesReelles: parseInt(row.ventesReelles || row.Ventes || row.ventes_reelles || 0),
                    montantGenere: parseInt(row.montantGenere || row.CA || row.montant_genere || (parseInt(row.ventesReelles || row.Ventes || 0) * 150)),
                    callsEnvoyes: parseInt(row.callsEnvoyes || row.Calls || row.calls_envoyes || 0),
                    callsQualifies: row.callsQualifies || row['Calls OK'] || row.calls_qualifies || 'Non',
                    retourCloser: parseFloat(row.retourCloser || row.Retour || row.retour_closer || 0),
                    scriptRespecte: row.scriptRespecte || row.Script || row.script_respecte || 'Non',
                    objectionBloquante: row.objectionBloquante || row['Obj Bloquante'] || row.objection_bloquante || '',
                    winDuJour: row.winDuJour || row.Win || row.win_du_jour || '',
                    failDuJour: row.failDuJour || row.Fail || row.fail_du_jour || '',
                    liensConversations: row.liensConversations || row.Liens || row.liens_conversations || ''
                }));

                const userId = document.getElementById('pasteUserId').value || null;

                const response = await fetch(`${API_URL}/api/data/import`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': `Bearer ${authToken}`
                    },
                    body: JSON.stringify({ 
                        data: formattedData,
                        userId: userId ? parseInt(userId) : null
                    })
                });

                const result = await response.json();
                if (response.ok) {
                    document.getElementById('pasteResult').innerHTML = `
                        <div style="background: #0a0a0a; padding: 15px; border-radius: 8px; border-left: 4px solid #00ff00;">
                            <p style="color: #00ff00;">✅ Import réussi !</p>
                            <p style="color: #fff;">${result.inserted} / ${result.total} entrées importées</p>
                            ${result.errors.length > 0 ? `<p style="color: #ffc107;">⚠️ ${result.errors.length} erreurs</p>` : ''}
                        </div>
                    `;
                    document.getElementById('pasteData').value = '';
                    loadAnalytics();
                    updateExportStats();
                } else {
                    document.getElementById('pasteResult').innerHTML = `
                        <div style="background: #0a0a0a; padding: 15px; border-radius: 8px; border-left: 4px solid #ff0000;">
                            <p style="color: #ff0000;">❌ Erreur: ${result.error || 'Erreur inconnue'}</p>
                        </div>
                    `;
                }
            } catch (error) {
                document.getElementById('pasteResult').innerHTML = `
                    <div style="background: #0a0a0a; padding: 15px; border-radius: 8px; border-left: 4px solid #ff0000;">
                        <p style="color: #ff0000;">❌ Erreur: ${error.message}</p>
                    </div>
                `;
            }
        }

        // Détecter le collage dans la zone de texte
        document.addEventListener('DOMContentLoaded', function() {
            const pasteArea = document.getElementById('pasteData');
            if (pasteArea) {
                pasteArea.addEventListener('paste', async function(e) {
                    // Laisser le navigateur coller normalement, puis on peut traiter
                    setTimeout(() => {
                        // Optionnel: auto-import si le format est valide
                    }, 100);
                });
            }
        });

        // Gestion des utilisateurs (Admin)
        let selectedFile = null;

        async function loadUsers() {
            try {
                const response = await fetch(`${API_URL}/api/users`, {
                    headers: { 'Authorization': `Bearer ${authToken}` }
                });
                if (!response.ok) return;
                
                const users = await response.json();
                let html = '<h3 style="color: #FF0000; margin-bottom: 15px;">Liste des utilisateurs</h3>';
                html += '<div style="display: grid; gap: 10px;">';
                users.forEach(user => {
                    html += `
                        <div style="background: #0a0a0a; padding: 15px; border-radius: 8px; border-left: 4px solid #FF0000; display: flex; justify-content: space-between; align-items: center;">
                            <div>
                                <strong style="color: #fff;">${user.username}</strong>
                                <span style="color: #999; margin-left: 15px;">Rôle: ${user.role}</span>
                                <span style="color: #666; margin-left: 15px; font-size: 0.9em;">Créé: ${new Date(user.created_at).toLocaleDateString('fr-FR')}</span>
                            </div>
                            ${user.id !== currentUser.id ? `<button class="delete-btn" onclick="deleteUser(${user.id})" style="padding: 8px 15px; font-size: 0.9em;">🗑️ Supprimer</button>` : ''}
                        </div>
                    `;
                });
                html += '</div>';
                document.getElementById('userList').innerHTML = html;
            } catch (error) {
                console.error('Erreur chargement utilisateurs:', error);
            }
        }

        async function loadUsersForImport() {
            try {
                const response = await fetch(`${API_URL}/api/users`, {
                    headers: { 'Authorization': `Bearer ${authToken}` }
                });
                if (!response.ok) return;
                
                const users = await response.json();
                const select = document.getElementById('importUserId');
                select.innerHTML = '<option value="">Utilisateur actuel</option>';
                users.forEach(user => {
                    const option = document.createElement('option');
                    option.value = user.id;
                    option.textContent = `${user.username} (${user.role})`;
                    select.appendChild(option);
                });
            } catch (error) {
                console.error('Erreur chargement utilisateurs:', error);
            }
        }

        async function createUser() {
            const username = document.getElementById('newUsername').value;
            const password = document.getElementById('newPassword').value;
            const role = document.getElementById('newRole').value;

            if (!username || !password) {
                alert('❌ Veuillez remplir tous les champs');
                return;
            }

            try {
                const response = await fetch(`${API_URL}/api/auth/register`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': `Bearer ${authToken}`
                    },
                    body: JSON.stringify({ username, password, role })
                });

                const data = await response.json();
                if (response.ok) {
                    alert('✅ Utilisateur créé avec succès !');
                    document.getElementById('newUsername').value = '';
                    document.getElementById('newPassword').value = '';
                    loadUsers();
                    loadUsersForImport();
                } else {
                    alert('❌ Erreur: ' + (data.error || 'Erreur inconnue'));
                }
            } catch (error) {
                alert('❌ Erreur de connexion');
            }
        }

        async function deleteUser(userId) {
            if (!confirm('⚠️ Supprimer cet utilisateur ?')) return;

            try {
                const response = await fetch(`${API_URL}/api/users/${userId}`, {
                    method: 'DELETE',
                    headers: { 'Authorization': `Bearer ${authToken}` }
                });

                if (response.ok) {
                    alert('✅ Utilisateur supprimé');
                    loadUsers();
                    loadUsersForImport();
                } else {
                    const data = await response.json();
                    alert('❌ Erreur: ' + (data.error || 'Erreur inconnue'));
                }
            } catch (error) {
                alert('❌ Erreur de connexion');
            }
        }

        // Import de données
        function handleFileSelect(event) {
            const file = event.target.files[0];
            if (!file) {
                selectedFile = null;
                document.getElementById('importBtn').disabled = true;
                return;
            }

            selectedFile = file;
            document.getElementById('importBtn').disabled = false;
            document.getElementById('importResult').innerHTML = `<p style="color: #999;">Fichier sélectionné: ${file.name}</p>`;
        }

        async function importData() {
            if (!selectedFile) {
                alert('❌ Veuillez sélectionner un fichier');
                return;
            }

            const fileType = selectedFile.name.split('.').pop().toLowerCase();
            const userId = document.getElementById('importUserId').value || null;

            try {
                const fileContent = await selectedFile.text();
                let data = [];

                if (fileType === 'json') {
                    data = JSON.parse(fileContent);
                    if (!Array.isArray(data)) {
                        alert('❌ Le fichier JSON doit contenir un tableau');
                        return;
                    }
                } else if (fileType === 'csv') {
                    data = parseCSV(fileContent);
                } else {
                    alert('❌ Format de fichier non supporté (CSV ou JSON uniquement)');
                    return;
                }

                if (data.length === 0) {
                    alert('❌ Aucune donnée à importer');
                    return;
                }

                // Convertir les données au bon format
                const formattedData = data.map(row => ({
                    timestamp: row.timestamp || row.Timestamp || new Date().toISOString(),
                    setterName: row.setterName || row.Setter || row.setter_name,
                    date: row.date || row.Date,
                    heuresTravaillees: parseFloat(row.heuresTravaillees || row.Heures || row.heures_travaillees || 0),
                    outbounds: parseInt(row.outbounds || row.Outbounds || 0),
                    inbounds: parseInt(row.inbounds || row.Inbounds || 0),
                    conversations: parseInt(row.conversations || row.Conversations || 0),
                    followups: parseInt(row.followups || row['Follow-ups'] || row.follow_ups || 0),
                    leadsQualifies: parseInt(row.leadsQualifies || row.Leads || row.leads_qualifies || 0),
                    qualiteMoyenne: parseFloat(row.qualiteMoyenne || row.Qualité || row.qualite_moyenne || 0),
                    objectionPrincipale: row.objectionPrincipale || row.Objection || row.objection_principale || '',
                    sourcePrincipale: row.sourcePrincipale || row.Source || row.source_principale || '',
                    personnesInteressees: parseInt(row.personnesInteressees || row.Intéressés || row.personnes_interessees || 0),
                    ventesReelles: parseInt(row.ventesReelles || row.Ventes || row.ventes_reelles || 0),
                    montantGenere: parseInt(row.montantGenere || row.CA || row.montant_genere || (parseInt(row.ventesReelles || row.Ventes || 0) * 150)),
                    callsEnvoyes: parseInt(row.callsEnvoyes || row.Calls || row.calls_envoyes || 0),
                    callsQualifies: row.callsQualifies || row['Calls OK'] || row.calls_qualifies || 'Non',
                    retourCloser: parseFloat(row.retourCloser || row.Retour || row.retour_closer || 0),
                    scriptRespecte: row.scriptRespecte || row.Script || row.script_respecte || 'Non',
                    objectionBloquante: row.objectionBloquante || row['Obj Bloquante'] || row.objection_bloquante || '',
                    winDuJour: row.winDuJour || row.Win || row.win_du_jour || '',
                    failDuJour: row.failDuJour || row.Fail || row.fail_du_jour || '',
                    liensConversations: row.liensConversations || row.Liens || row.liens_conversations || ''
                }));

                const response = await fetch(`${API_URL}/api/data/import`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': `Bearer ${authToken}`
                    },
                    body: JSON.stringify({ 
                        data: formattedData,
                        userId: userId ? parseInt(userId) : null
                    })
                });

                const result = await response.json();
                if (response.ok) {
                    document.getElementById('importResult').innerHTML = `
                        <div style="background: #0a0a0a; padding: 15px; border-radius: 8px; border-left: 4px solid #00ff00;">
                            <p style="color: #00ff00;">✅ Import réussi !</p>
                            <p style="color: #fff;">${result.inserted} / ${result.total} entrées importées</p>
                            ${result.errors.length > 0 ? `<p style="color: #ffc107;">⚠️ ${result.errors.length} erreurs</p>` : ''}
                        </div>
                    `;
                    selectedFile = null;
                    document.getElementById('importFile').value = '';
                    document.getElementById('importBtn').disabled = true;
                    loadAnalytics();
                } else {
                    alert('❌ Erreur: ' + (result.error || 'Erreur inconnue'));
                }
            } catch (error) {
                alert('❌ Erreur lors de l\'import: ' + error.message);
            }
        }

        function parseCSV(csvText) {
            const lines = csvText.split('\n').filter(line => line.trim());
            if (lines.length < 2) return [];

            const headers = lines[0].split(',').map(h => h.trim().replace(/"/g, ''));
            const data = [];

            for (let i = 1; i < lines.length; i++) {
                const values = lines[i].split(',').map(v => v.trim().replace(/^"|"$/g, ''));
                const row = {};
                headers.forEach((header, index) => {
                    row[header] = values[index] || '';
                });
                data.push(row);
            }

            return data;
        }

        // Initialiser
        checkAuth();
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard Comercial Brave - Versão Editável</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@10..48,400;10..48,600;10..48,700&family=Montserrat:wght@400;500;600;700&family=Red+Hat+Display:wght@400;500;700&display=swap');
        
        :root {
            --dark-blue: #2b2d42;
            --darker-blue: #0f1c2f;
            --light-blue: #2b3272;
            --bluish-gray: #8d99ae;
            --darker-gray: #505168;
            --light-gray: #edf2f4;
            --yellow: #eaca2d;
            --darker-yellow: #d59f07;
            --success: #28a745;
            --warning: #ffc107;
            --danger: #dc3545;
            --info: #17a2b8;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Red Hat Display', sans-serif;
        }
        
        body {
            background-color: var(--light-gray);
            color: var(--dark-blue);
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background-color: var(--dark-blue);
            color: white;
            padding: 20px 0;
            margin-bottom: 20px;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        .logo {
            display: flex;
            align-items: center;
        }
        
        .logo-symbol {
            width: 40px;
            height: 40px;
            background-color: var(--yellow);
            transform: rotate(45deg);
            margin-right: 15px;
            position: relative;
        }
        
        .logo-symbol:before {
            content: "";
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) rotate(-45deg);
            width: 20px;
            height: 20px;
            background-color: var(--dark-blue);
            clip-path: polygon(0 0, 100% 0, 50% 100%);
        }
        
        .brand-name {
            font-family: 'Bricolage Grotesque', sans-serif;
            font-weight: 700;
            font-size: 20px;
        }
        
        .app-name {
            font-family: 'Montserrat', sans-serif;
            font-size: 12px;
            font-weight: 500;
        }
        
        .date-picker {
            display: flex;
            align-items: center;
        }
        
        .date-input {
            padding: 8px;
            border: none;
            border-radius: 4px;
            margin-right: 10px;
        }
        
        .btn {
            padding: 8px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-family: 'Montserrat', sans-serif;
            font-weight: 600;
            transition: background-color 0.3s;
        }
        
        .btn-primary {
            background-color: var(--yellow);
            color: var(--dark-blue);
        }
        
        .btn-primary:hover {
            background-color: var(--darker-yellow);
        }
        
        .btn-secondary {
            background-color: var(--bluish-gray);
            color: white;
        }
        
        .btn-secondary:hover {
            background-color: var(--darker-gray);
        }
        
        .section-title {
            font-family: 'Bricolage Grotesque', sans-serif;
            font-size: 24px;
            font-weight: 700;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 3px solid var(--yellow);
        }
        
        .card {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            padding: 20px;
            margin-bottom: 20px;
        }
        
        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .card-title {
            font-family: 'Bricolage Grotesque', sans-serif;
            font-size: 18px;
            font-weight: 700;
        }
        
        .tabs {
            display: flex;
            border-bottom: 1px solid var(--light-gray);
            margin-bottom: 15px;
        }
        
        .tab {
            padding: 10px 15px;
            cursor: pointer;
            font-family: 'Montserrat', sans-serif;
            font-weight: 600;
            font-size: 14px;
            color: var(--bluish-gray);
        }
        
        .tab.active {
            color: var(--dark-blue);
            border-bottom: 3px solid var(--yellow);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .table-container {
            overflow-x: auto;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid var(--light-gray);
        }
        
        th {
            background-color: var(--light-gray);
            color: var(--dark-blue);
            font-family: 'Montserrat', sans-serif;
            font-weight: 600;
            font-size: 12px;
            text-transform: uppercase;
        }
        
        tr:last-child td {
            border-bottom: none;
        }
        
        tr:nth-child(even) {
            background-color: rgba(237, 242, 244, 0.3);
        }
        
        .editable {
            background-color: transparent;
            border: none;
            width: 100%;
            font-family: inherit;
            font-size: inherit;
            color: inherit;
            padding: 0;
        }
        
        .editable:focus {
            outline: none;
            border-bottom: 1px solid var(--yellow);
        }
        
        .status-pill {
            display: inline-block;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
        }
        
        .badge-success {
            background-color: rgba(40, 167, 69, 0.2);
            color: var(--success);
        }
        
        .badge-warning {
            background-color: rgba(255, 193, 7, 0.2);
            color: #856404;
        }
        
        .badge-danger {
            background-color: rgba(220, 53, 69, 0.2);
            color: var(--danger);
        }
        
        .metrics-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .metric-card {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
            padding: 15px;
            text-align: center;
        }
        
        .metric-title {
            font-family: 'Montserrat', sans-serif;
            font-size: 12px;
            font-weight: 600;
            color: var(--bluish-gray);
            margin-bottom: 10px;
            text-transform: uppercase;
        }
        
        .metric-value {
            font-family: 'Bricolage Grotesque', sans-serif;
            font-size: 28px;
            font-weight: 700;
            margin-bottom: 5px;
        }
        
        .metric-trend {
            font-size: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .trend-up {
            color: var(--success);
        }
        
        .trend-down {
            color: var(--danger);
        }
        
        .trend-neutral {
            color: var(--bluish-gray);
        }
        
        .funnel-container {
            display: flex;
            justify-content: space-evenly;
            align-items: flex-end;
            height: 220px;
            margin: 30px 0;
            padding: 0 20px;
        }
        
        .funnel-stage {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100px;
        }
        
        .funnel-bar {
            width: 60px;
            border-radius: 4px 4px 0 0;
            position: relative;
            transition: height 0.5s ease;
        }
        
        .funnel-value {
            position: absolute;
            top: -25px;
            width: 100%;
            text-align: center;
            font-weight: 700;
        }
        
        .funnel-percent {
            position: absolute;
            bottom: 5px;
            width: 100%;
            text-align: center;
            color: white;
            font-size: 12px;
            font-weight: 600;
        }
        
        .funnel-label {
            margin-top: 10px;
            text-align: center;
            font-family: 'Montserrat', sans-serif;
            font-size: 12px;
            font-weight: 600;
        }
        
        .editable-container {
            position: relative;
        }
        
        .edit-icon {
            position: absolute;
            right: 5px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--bluish-gray);
            cursor: pointer;
            opacity: 0;
            transition: opacity 0.3s;
        }
        
        .editable-container:hover .edit-icon {
            opacity: 1;
        }
        
        .action-bar {
            display: flex;
            justify-content: flex-end;
            margin-bottom: 20px;
            gap: 10px;
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background-color: white;
            border-radius: 8px;
            max-width: 600px;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .modal-header {
            padding: 15px 20px;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .modal-title {
            font-family: 'Bricolage Grotesque', sans-serif;
            font-size: 18px;
            font-weight: 700;
        }
        
        .modal-close {
            cursor: pointer;
            font-size: 20px;
            color: var(--bluish-gray);
        }
        
        .modal-body {
            padding: 20px;
        }
        
        .modal-footer {
            padding: 15px 20px;
            border-top: 1px solid var(--light-gray);
            display: flex;
            justify-content: flex-end;
            gap: 10px;
        }
        
        .form-group {
            margin-bottom: 15px;
        }
        
        .form-row {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .form-col {
            flex: 1;
        }
        
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
        }
        
        input, select, textarea {
            width: 100%;
            padding: 8px 12px;
            border: 1px solid var(--bluish-gray);
            border-radius: 4px;
            font-family: 'Red Hat Display', sans-serif;
        }
        
        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: var(--yellow);
            box-shadow: 0 0 0 2px rgba(234, 202, 45, 0.2);
        }
        
        .report-preview {
            font-family: monospace;
            white-space: pre-wrap;
            padding: 15px;
            background-color: var(--light-gray);
            border-radius: 4px;
            max-height: 400px;
            overflow-y: auto;
        }
        
        .save-notification {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: var(--success);
            color: white;
            padding: 10px 20px;
            border-radius: 4px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
            display: none;
            z-index: 1000;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .metrics-grid {
                grid-template-columns: 1fr 1fr;
            }
            
            .form-row {
                flex-direction: column;
                gap: 0;
            }
            
            .funnel-container {
                flex-wrap: wrap;
                height: auto;
                gap: 20px;
            }
            
            .funnel-stage {
                height: 200px;
                margin-bottom: 20px;
            }
        }
        
        @media (max-width: 480px) {
            .metrics-grid {
                grid-template-columns: 1fr;
            }
            
            .header-content {
                flex-direction: column;
                align-items: flex-start;
                gap: 10px;
            }
            
            .date-picker {
                width: 100%;
                justify-content: space-between;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="header-content">
            <div class="logo">
                <div class="logo-symbol"></div>
                <div>
                    <div class="brand-name">BRAVE</div>
                    <div class="app-name">EDUCAÇÃO EMPRESARIAL</div>
                </div>
            </div>
            <div class="date-picker">
                <input type="date" id="current-date" class="date-input" value="2025-03-10">
                <button id="save-all-data" class="btn btn-primary">
                    <i class="fas fa-save"></i> Salvar Tudo
                </button>
            </div>
        </div>
    </header>
    
    <div class="container">
        <h1 class="section-title">Dashboard Comercial</h1>
        
        <div class="action-bar">
            <button id="generate-report-btn" class="btn btn-primary">
                <i class="fas fa-file-alt"></i> Gerar Relatório
            </button>
            <button id="export-data-btn" class="btn btn-secondary">
                <i class="fas fa-download"></i> Exportar Dados
            </button>
        </div>
        
        <div class="card">
            <div class="card-header">
                <h2 class="card-title">Visão Geral - Métricas do Dia</h2>
                <button id="edit-metrics-btn" class="btn btn-secondary">
                    <i class="fas fa-edit"></i> Editar
                </button>
            </div>
            <div class="metrics-grid" id="metrics-overview">
                <div class="metric-card">
                    <div class="metric-title">Leads Gerados</div>
                    <div class="metric-value" id="total-leads">21</div>
                    <div class="metric-trend trend-up">
                        <i class="fas fa-arrow-up"></i> 15%
                    </div>
                </div>
                <div class="metric-card">
                    <div class="metric-title">Reuniões Agendadas</div>
                    <div class="metric-value" id="total-appointments">12</div>
                    <div class="metric-trend trend-up">
                        <i class="fas fa-arrow-up"></i> 8%
                    </div>
                </div>
                <div class="metric-card">
                    <div class="metric-title">Reuniões Realizadas</div>
                    <div class="metric-value" id="total-meetings">9</div>
                    <div class="metric-trend trend-neutral">
                        <i class="fas fa-equals"></i> 0%
                    </div>
                </div>
                <div class="metric-card">
                    <div class="metric-title">No-Shows</div>
                    <div class="metric-value" id="total-noshows">3</div>
                    <div class="metric-trend trend-down">
                        <i class="fas fa-arrow-down"></i> 25%
                    </div>
                </div>
                <div class="metric-card">
                    <div class="metric-title">Taxa de Conversão</div>
                    <div class="metric-value" id="conversion-rate">43%</div>
                    <div class="metric-trend trend-up">
                        <i class="fas fa-arrow-up"></i> 5%
                    </div>
                </div>
                <div class="metric-card">
                    <div class="metric-title">Propostas Enviadas</div>
                    <div class="metric-value" id="total-proposals">5</div>
                    <div class="metric-trend trend-up">
                        <i class="fas fa-arrow-up"></i> 20%
                    </div>
                </div>
                <div class="metric-card">
                    <div class="metric-title">Negociações Ativas</div>
                    <div class="metric-value" id="active-negotiations">14</div>
                    <div class="metric-trend trend-up">
                        <i class="fas fa-arrow-up"></i> 27%
                    </div>
                </div>
                <div class="metric-card">
                    <div class="metric-title">Fechamentos</div>
                    <div class="metric-value" id="total-closings">2</div>
                    <div class="metric-trend trend-up">
                        <i class="fas fa-arrow-up"></i> 100%
                    </div>
                </div>
            </div>
        </div>
        
        <div class="card">
            <div class="card-header">
                <h2 class="card-title">Funil de Vendas</h2>
                <span class="status-pill badge-success">Saudável</span>
            </div>
            <div class="funnel-container" id="sales-funnel">
                <div class="funnel-stage">
                    <div class="funnel-bar" style="height: 180px; background-color: var(--dark-blue);">
                        <div class="funnel-value">21</div>
                        <div class="funnel-percent">100%</div>
                    </div>
                    <div class="funnel-label">Leads</div>
                </div>
                <div class="funnel-stage">
                    <div class="funnel-bar" style="height: 162px; background-color: var(--light-blue);">
                        <div class="funnel-value">19</div>
                        <div class="funnel-percent">90%</div>
                    </div>
                    <div class="funnel-label">Qualificados</div>
                </div>
                <div class="funnel-stage">
                    <div class="funnel-bar" style="height: 103px; background-color: var(--bluish-gray);">
                        <div class="funnel-value">12</div>
                        <div class="funnel-percent">57%</div>
                    </div>
                    <div class="funnel-label">Agendados</div>
                </div>
                <div class="funnel-stage">
                    <div class="funnel-bar" style="height: 77px; background-color: var(--darker-gray);">
                        <div class="funnel-value">9</div>
                        <div class="funnel-percent">43%</div>
                    </div>
                    <div class="funnel-label">Diagnóstico</div>
                </div>
                <div class="funnel-stage">
                    <div class="funnel-bar" style="height: 43px; background-color: var(--yellow);">
                        <div class="funnel-value">5</div>
                        <div class="funnel-percent">24%</div>
                    </div>
                    <div class="funnel-label">Apresentação</div>
                </div>
                <div class="funnel-stage">
                    <div class="funnel-bar" style="height: 17px; background-color: var(--darker-yellow);">
                        <div class="funnel-value">2</div>
                        <div class="funnel-percent">10%</div>
                    </div>
                    <div class="funnel-label">Fechados</div>
                </div>
            </div>
            <div class="action-bar">
                <button id="edit-funnel-btn" class="btn btn-secondary">
                    <i class="fas fa-edit"></i> Editar Funil
                </button>
            </div>
        </div>
        
        <div class="card">
            <div class="card-header">
                <h2 class="card-title">Desempenho SDRs</h2>
            </div>
            <div class="tabs">
                <div class="tab active" data-tab="sdr-daily">Diário</div>
                <div class="tab" data-tab="sdr-weekly">Semanal</div>
                <div class="tab" data-tab="sdr-monthly">Mensal</div>
            </div>
            <div class="tab-content active" id="sdr-daily">
                <div class="table-container">
                    <table id="sdr-daily-table">
                        <thead>
                            <tr>
                                <th>SDR</th>
                                <th>Leads</th>
                                <th>Agendamentos</th>
                                <th>No-Shows</th>
                                <th>Conv. %</th>
                                <th>Status</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Emily</td>
                                <td contenteditable="true" class="editable">12</td>
                                <td contenteditable="true" class="editable">7</td>
                                <td contenteditable="true" class="editable">1</td>
                                <td>58%</td>
                                <td><span class="badge-success status-pill">Meta Batida</span></td>
                            </tr>
                            <tr>
                                <td>Erima</td>
                                <td contenteditable="true" class="editable">9</td>
                                <td contenteditable="true" class="editable">5</td>
                                <td contenteditable="true" class="editable">2</td>
                                <td>56%</td>
                                <td><span class="badge-success status-pill">Meta Batida</span></td>
                            </tr>
                            <tr>
                                <td><strong>Total</strong></td>
                                <td><strong>21</strong></td>
                                <td><strong>12</strong></td>
                                <td><strong>3</strong></td>
                                <td><strong>57%</strong></td>
                                <td></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            <div class="tab-content" id="sdr-weekly">
                <div class="table-container">
                    <table id="sdr-weekly-table">
                        <thead>
                            <tr>
                                <th>SDR</th>
                                <th>Leads</th>
                                <th>Agendamentos</th>
                                <th>No-Shows</th>
                                <th>Conv. %</th>
                                <th>Status</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Emily</td>
                                <td contenteditable="true" class="editable">48</td>
                                <td contenteditable="true" class="editable">28</td>
                                <td contenteditable="true" class="editable">4</td>
                                <td>58%</td>
                                <td><span class="badge-success status-pill">Meta Batida</span></td>
                            </tr>
                            <tr>
                                <td>Erima</td>
                                <td contenteditable="true" class="editable">42</td>
                                <td contenteditable="true" class="editable">24</td>
                                <td contenteditable="true" class="editable">5</td>
                                <td>57%</td>
                                <td><span class="badge-success status-pill">Meta Batida</span></td>
                            </tr>
                            <tr>
                                <td><strong>Total</strong></td>
                                <td><strong>90</strong></td>
                                <td><strong>52</strong></td>
                                <td><strong>9</strong></td>
                                <td><strong>58%</strong></td>
                                <td></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            <div class="tab-content" id="sdr-monthly">
                <div class="table-container">
                    <table id="sdr-monthly-table">
                        <thead>
                            <tr>
                                <th>SDR</th>
                                <th>Leads</th>
                                <th>Agendamentos</th>
                                <th>No-Shows</th>
                                <th>Conv. %</th>
                                <th>Status</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Emily</td>
                                <td contenteditable="true" class="editable">135</td>
                                <td contenteditable="true" class="editable">78</td>
                                <td contenteditable="true" class="editable">12</td>
                                <td>58%</td>
                                <td><span class="badge-success status-pill">Meta Batida</span></td>
                            </tr>
                            <tr>
                                <td>Erima</td>
                                <td contenteditable="true" class="editable">115</td>
                                <td contenteditable="true" class="editable">60</td>
                                <td contenteditable="true" class="editable">15</td>
                                <td>52%</td>
                                <td><span class="badge-warning status-pill">Próximo</span></td>
                            </tr>
                            <tr>
                                <td><strong>Total</strong></td>
                                <td><strong>250</strong></td>
                                <td><strong>138</strong></td>
                                <td><strong>27</strong></td>
                                <td><strong>55%</strong></td>
                                <td></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
        
        <div class="card">
            <div class="card-header">
                <h2 class="card-title">Desempenho Executivos</h2>
            </div>
            <div class="tabs">
                <div class="tab active" data-tab="exec-daily">Diário</div>
                <div class="tab" data-tab="exec-weekly">Semanal</div>
                <div class="tab" data-tab="exec-monthly">Mensal</div>
            </div>
            <div class="tab-content active" id="exec-daily">
                <div class="table-container">
                    <table id="exec-daily-table">
                        <thead>
                            <tr>
                                <th>Executivo</th>
                                <th>Diagnóstico</th>
                                <th>Apresentação</th>
                                <th>Propostas</th>
                                <th>Fechamentos</th>
                                <th>Valor (R$)</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Elias</td>
                                <td contenteditable="true" class="editable">5</td>
                                <td contenteditable="true" class="editable">3</td>
                                <td contenteditable="true" class="editable">2</td>
                                <td contenteditable="true" class="editable">1</td>
                                <td contenteditable="true" class="editable">35.000</td>
                            </tr>
                            <tr>
                                <td>Jessé</td>
                                <td contenteditable="true" class="editable">4</td>
                                <td contenteditable="true" class="editable">2</td>
                                <td contenteditable="true" class="editable">3</td>
                                <td contenteditable="true" class="editable">1</td>
                                <td contenteditable="true" class="editable">28.500</td>
                            </tr>
                            <tr>
                                <td><strong>Total</strong></td>
                                <td><strong>9</strong></td>
                                <td><strong>5</strong></td>
                                <td><strong>5</strong></td>
                                <td><strong>2</strong></td>
                                <td><strong>63.500</strong></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            <div class="tab-content" id="exec-weekly">
                <div class="table-container">
                    <table id="exec-weekly-table">
                        <thead>
                            <tr>
                                <th>Executivo</th>
                                <th>Diagnóstico</th>
                                <th>Apresentação</th>
                                <th>Propostas</th>
                                <th>Fechamentos</th>
                                <th>Valor (R$)</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Elias</td>
                                <td contenteditable="true" class="editable">21</td>
                                <td contenteditable="true" class="editable">15</td>
                                <td contenteditable="true" class="editable">8</td>
                                <td contenteditable="true" class="editable">3</td>
                                <td contenteditable="true" class="editable">125.000</td>
                            </tr>
                            <tr>
                                <td>Jessé</td>
                                <td contenteditable="true" class="editable">19</td>
                                <td contenteditable="true" class="editable">12</td>
                                <td contenteditable="true" class="editable">7</td>
                                <td contenteditable="true" class="editable">2</td>
                                <td contenteditable="true" class="editable">85.000</td>
                            </tr>
                            <tr>
                                <td><strong>Total</strong></td>
                                <td><strong>40</strong></td>
                                <td><strong>27</strong></td>
                                <td><strong>15</strong></td>
                                <td><strong>5</strong></td>
                                <td><strong>210.000</strong></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            <div class="tab-content" id="exec-monthly">
                <div class="table-container">
                    <table id="exec-monthly-table">
                        <thead>
                            <tr>
                                <th>Executivo</th>
                                <th>Diagnóstico</th>
                                <th>Apresentação</th>
                                <th>Propostas</th>
                                <th>Fechamentos</th>
                                <th>Valor (R$)</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Elias</td>
                                <td contenteditable="true" class="editable">72</td>
                                <td contenteditable="true" class="editable">45</td>
                                <td contenteditable="true" class="editable">38</td>
                                <td contenteditable="true" class="editable">10</td>
                                <td contenteditable="true" class="editable">235.000</td>
                            </tr>
                            <tr>
                                <td>Jessé</td>
                                <td contenteditable="true" class="editable">66</td>
                                <td contenteditable="true" class="editable">42</td>
                                <td contenteditable="true" class="editable">34</td>
                                <td contenteditable="true" class="editable">8</td>
                                <td contenteditable="true" class="editable">170.000</td>
                            </tr>
                            <tr>
                                <td><strong>Total</strong></td>
                                <td><strong>138</strong></td>
                                <td><strong>87</strong></td>
                                <td><strong>72</strong></td>
                                <td><strong>18</strong></td>
                                <td><strong>405.000</strong></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
        
        <div class="card">
            <div class="card-header">
                <h2 class="card-title">Reuniões de Hoje</h2>
                <button id="add-meeting-btn" class="btn btn-primary">
                    <i class="fas fa-plus"></i> Adicionar
                </button>
            </div>
            <div class="table-container">
                <table id="meetings-table">
                    <thead>
                        <tr>
                            <th>Horário</th>
                            <th>Cliente</th>
                            <th>Executivo</th>
                            <th>Tipo</th>
                            <th>Status</th>
                            <th>Ações</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr data-id="1">
                            <td contenteditable="true" class="editable">09:00</td>
                            <td contenteditable="true" class="editable">Empresa ABC Ltda.</td>
                            <td contenteditable="true" class="editable">Elias</td>
                            <td contenteditable="true" class="editable">Diagnóstico</td>
                            <td>
                                <select class="meeting-status">
                                    <option value="Realizada" selected>Realizada</option>
                                    <option value="No-Show">No-Show</option>
                                    <option value="Reagendada">Reagendada</option>
                                    <option value="Cancelada">Cancelada</option>
                                </select>
                            </td>
                            <td>
                                <button class="btn-delete-meeting" data-id="1">
                                    <i class="fas fa-trash"></i>
                                </button>
                            </td>
                        </tr>
                        <tr data-id="2">
                            <td contenteditable="true" class="editable">10:30</td>
                            <td contenteditable="true" class="editable">Empresa XYZ S.A.</td>
                            <td contenteditable="true" class="editable">Jessé</td>
                            <td contenteditable="true" class="editable">Apresentação</td>
                            <td>
                                <select class="meeting-status">
                                    <option value="Realizada" selected>Realizada</option>
                                    <option value="No-Show">No-Show</option>
                                    <option value="Reagendada">Reagendada</option>
                                    <option value="Cancelada">Cancelada</option>
                                </select>
                            </td>
                            <td>
                                <button class="btn-delete-meeting" data-id="2">
                                    <i class="fas fa-trash"></i>
                                </button>
                            </td>
                        </tr>
                        <tr data-id="3">
                            <td contenteditable="true" class="editable">13:00</td>
                            <td contenteditable="true" class="editable">Empresa 123 Ltda.</td>
                            <td contenteditable="true" class="editable">Elias</td>
                            <td contenteditable="true" class="editable">Batida de Martelo</td>
                            <td>
                                <select class="meeting-status">
                                    <option value="Realizada">Realizada</option>
                                    <option value="No-Show" selected>No-Show</option>
                                    <option value="Reagendada">Reagendada</option>
                                    <option value="Cancelada">Cancelada</option>
                                </select>
                            </td>
                            <td>
                                <button class="btn-delete-meeting" data-id="3">
                                    <i class="fas fa-trash"></i>
                                </button>
                            </td>
                        </tr>
                        <tr data-id="4">
                            <td contenteditable="true" class="editable">14:30</td>
                            <td contenteditable="true" class="editable">Empresa DEF Inc.</td>
                            <td contenteditable="true" class="editable">Jessé</td>
                            <td contenteditable="true" class="editable">Diagnóstico</td>
                            <td>
                                <select class="meeting-status">
                                    <option value="Realizada" selected>Realizada</option>
                                    <option value="No-Show">No-Show</option>
                                    <option value="Reagendada">Reagendada</option>
                                    <option value="Cancelada">Cancelada</option>
                                </select>
                            </td>
                            <td>
                                <button class="btn-delete-meeting" data-id="4">
                                    <i class="fas fa-trash"></i>
                                </button>
                            </td>
                        </tr>
                        <tr data-id="5">
                            <td contenteditable="true" class="editable">16:00</td>
                            <td contenteditable="true" class="editable">Empresa GHI Corp.</td>
                            <td contenteditable="true" class="editable">Elias</td>
                            <td contenteditable="true" class="editable">Apresentação</td>
                            <td>
                                <select class="meeting-status">
                                    <option value="Realizada">Realizada</option>
                                    <option value="No-Show" selected>No-Show</option>
                                    <option value="Reagendada">Reagendada</option>
                                    <option value="Cancelada">Cancelada</option>
                                </select>
                            </td>
                            <td>
                                <button class="btn-delete-meeting" data-id="5">
                                    <i class="fas fa-trash"></i>
                                </button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
    
    <!-- Modals -->
    <div class="modal" id="edit-metrics-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Editar Métricas</h3>
                <span class="modal-close">&times;</span>
            </div>
            <div class="modal-body">
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label for="metric-leads">Leads Gerados</label>
                            <input type="number" id="metric-leads" min="0" value="21">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label for="metric-appointments">Reuniões Agendadas</label>
                            <input type="number" id="metric-appointments" min="0" value="12">
                        </div>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label for="metric-meetings">Reuniões Realizadas</label>
                            <input type="number" id="metric-meetings" min="0" value="9">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label for="metric-noshows">No-Shows</label>
                            <input type="number" id="metric-noshows" min="0" value="3">
                        </div>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label for="metric-proposals">Propostas Enviadas</label>
                            <input type="number" id="metric-proposals" min="0" value="5">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label for="metric-negotiations">Negociações Ativas</label>
                            <input type="number" id="metric-negotiations" min="0" value="14">
                        </div>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label for="metric-closings">Fechamentos</label>
                            <input type="number" id="metric-closings" min="0" value="2">
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label for="metric-conversion">Taxa de Conversão (%)</label>
                            <input type="number" id="metric-conversion" min="0" max="100" value="43">
                        </div>
                    </div>
                </div>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary modal-close-btn">Cancelar</button>
                <button class="btn btn-primary" id="save-metrics-btn">Salvar</button>
            </div>
        </div>
    </div>
    
    <div class="modal" id="edit-funnel-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Editar Funil de Vendas</h3>
                <span class="modal-close">&times;</span>
            </div>
            <div class="modal-body">
                <div class="form-group">
                    <label for="funnel-leads">Leads</label>
                    <input type="number" id="funnel-leads" min="0" value="21">
                </div>
                <div class="form-group">
                    <label for="funnel-qualified">Leads Qualificados</label>
                    <input type="number" id="funnel-qualified" min="0" value="19">
                </div>
                <div class="form-group">
                    <label for="funnel-scheduled">Agendados</label>
                    <input type="number" id="funnel-scheduled" min="0" value="12">
                </div>
                <div class="form-group">
                    <label for="funnel-diagnostic">Diagnóstico</label>
                    <input type="number" id="funnel-diagnostic" min="0" value="9">
                </div>
                <div class="form-group">
                    <label for="funnel-presentation">Apresentação</label>
                    <input type="number" id="funnel-presentation" min="0" value="5">
                </div>
                <div class="form-group">
                    <label for="funnel-closed">Fechados</label>
                    <input type="number" id="funnel-closed" min="0" value="2">
                </div>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary modal-close-btn">Cancelar</button>
                <button class="btn btn-primary" id="save-funnel-btn">Salvar</button>
            </div>
        </div>
    </div>
    
    <div class="modal" id="add-meeting-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Adicionar Reunião</h3>
                <span class="modal-close">&times;</span>
            </div>
            <div class="modal-body">
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label for="new-meeting-time">Horário</label>
                            <input type="time" id="new-meeting-time" required>
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label for="new-meeting-client">Cliente</label>
                            <input type="text" id="new-meeting-client" placeholder="Nome da Empresa" required>
                        </div>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-col">
                        <div class="form-group">
                            <label for="new-meeting-executive">Executivo</label>
                            <select id="new-meeting-executive" required>
                                <option value="">Selecione</option>
                                <option value="Elias">Elias</option>
                                <option value="Jessé">Jessé</option>
                            </select>
                        </div>
                    </div>
                    <div class="form-col">
                        <div class="form-group">
                            <label for="new-meeting-type">Tipo</label>
                            <select id="new-meeting-type" required>
                                <option value="">Selecione</option>
                                <option value="Diagnóstico">Diagnóstico</option>
                                <option value="Apresentação">Apresentação</option>
                                <option value="Batida de Martelo">Batida de Martelo</option>
                            </select>
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <label for="new-meeting-status">Status</label>
                    <select id="new-meeting-status" required>
                        <option value="">Selecione</option>
                        <option value="Agendada">Agendada</option>
                        <option value="Confirmada">Confirmada</option>
                        <option value="Realizada">Realizada</option>
                        <option value="No-Show">No-Show</option>
                        <option value="Reagendada">Reagendada</option>
                        <option value="Cancelada">Cancelada</option>
                    </select>
                </div>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary modal-close-btn">Cancelar</button>
                <button class="btn btn-primary" id="save-meeting-btn">Salvar</button>
            </div>
        </div>
    </div>
    
    <div class="modal" id="report-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Relatório Diário</h3>
                <span class="modal-close">&times;</span>
            </div>
            <div class="modal-body">
                <div class="report-preview" id="report-preview">
# 📊 REPORT DIÁRIO DE VENDAS | BRAVE EDUCAÇÃO
**Data:** 10/03/2025

## 🎯 PERFORMANCE SDRs
| SDR | Leads Gerados | Agendamentos | No-Shows | Taxa de Conversão |
|-----|---------------|--------------|----------|------------------|
| Emily | 12 | 7 | 1 | 58% |
| Erima | 9 | 5 | 2 | 56% |
| **TOTAL** | **21** | **12** | **3** | **57%** |

## 🤝 REUNIÕES DO DIA
| Executivo | Diagnóstico | Apresentação | Batida de Martelo | Total |
|-----------|-------------|--------------|-------------------|-------|
| Elias | 5 | 3 | 1 | 9 |
| Jessé | 4 | 2 | 1 | 7 |
| **TOTAL** | **9** | **5** | **2** | **16** |

## 📈 CONVERSÃO SDR → CLOSER
* Leads qualificados passados: **19**
* Reuniões realizadas: **9**
* Taxa de conversão: **47%**

## 📝 PROPOSTAS
* Propostas enviadas hoje: **5**
* Negociações em andamento: **14**
* Prazo médio de resposta: **3 dias**

## 🏆 FECHAMENTOS
* Contratos fechados hoje: **2**
* Valor total: **R$ 63.500,00**
* Clientes: Empresa ABC Ltda., Empresa XYZ S.A.

## ⚠️ DESAFIOS
1. Cliente Empresa 123 Ltda. solicitou revisão de proposta com desconto adicional
2. No-show de cliente potencial de alto valor (Empresa GHI Corp.)
3. Delay na assinatura do contrato da Empresa DEF Inc. (questões jurídicas)

## 🔍 INSIGHTS
* Maior interesse em treinamentos corporativos customizados
* Objeção recorrente: preço alto para o orçamento atual (32%)
* Oportunidade: aumentar cross-sell em clientes da base

---
*Relatório gerado automaticamente pelo Dashboard Comercial Brave Educação*
                </div>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary modal-close-btn">Fechar</button>
                <button class="btn btn-primary" id="copy-report-btn">Copiar Relatório</button>
                <button class="btn btn-primary" id="download-report-btn">Download</button>
            </div>
        </div>
    </div>
    
    <div class="save-notification" id="save-notification">
        Dados salvos com sucesso!
    </div>
    
    <script>
        // Global variables
        let nextMeetingId = 6; // Starting ID for new meetings
        
        // Initialize the dashboard
        document.addEventListener('DOMContentLoaded', function() {
            // Set the current date
            const today = new Date();
            document.getElementById('current-date').value = today.toISOString().split('T')[0];
            
            // Initialize data from localStorage if available
            loadDataFromStorage();
            
            // Add event listeners for tabs
            setupTabs();
            
            // Add event listeners for buttons
            setupButtonListeners();
            
            // Calculate totals for tables
            calculateTableTotals();
            
            // Setup editable fields
            setupEditableFields();
        });
        
        // Setup tab switching
        function setupTabs() {
            document.querySelectorAll('.tab').forEach(tab => {
                tab.addEventListener('click', function() {
                    const tabGroup = this.parentElement;
                    const tabContentId = this.getAttribute('data-tab');
                    
                    // Remove active class from all tabs in this group
                    tabGroup.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
                    
                    // Add active class to clicked tab
                    this.classList.add('active');
                    
                    // Hide all tab content
                    const tabContents = document.querySelectorAll('.tab-content');
                    tabContents.forEach(content => {
                        if (content.id === tabContentId) {
                            content.classList.add('active');
                        } else if (content.id.split('-')[0] === tabContentId.split('-')[0]) {
                            content.classList.remove('active');
                        }
                    });
                    
                    // Calculate totals for the active table
                    calculateTableTotals();
                });
            });
        }
        
        // Setup button listeners
        function setupButtonListeners() {
            // Edit metrics button
            document.getElementById('edit-metrics-btn').addEventListener('click', function() {
                openModal('edit-metrics-modal');
            });
            
            // Save metrics button
            document.getElementById('save-metrics-btn').addEventListener('click', function() {
                saveMetrics();
                closeModal('edit-metrics-modal');
                showSaveNotification();
            });
            
            // Edit funnel button
            document.getElementById('edit-funnel-btn').addEventListener('click', function() {
                openModal('edit-funnel-modal');
            });
            
            // Save funnel button
            document.getElementById('save-funnel-btn').addEventListener('click', function() {
                saveFunnel();
                closeModal('edit-funnel-modal');
                showSaveNotification();
            });
            
            // Add meeting button
            document.getElementById('add-meeting-btn').addEventListener('click', function() {
                openModal('add-meeting-modal');
            });
            
            // Save meeting button
            document.getElementById('save-meeting-btn').addEventListener('click', function() {
                if (addNewMeeting()) {
                    closeModal('add-meeting-modal');
                    showSaveNotification();
                }
            });
            
            // Delete meeting buttons
            setupDeleteMeetingButtons();
            
            // Generate report button
            document.getElementById('generate-report-btn').addEventListener('click', function() {
                generateReport();
                openModal('report-modal');
            });
            
            // Copy report button
            document.getElementById('copy-report-btn').addEventListener('click', function() {
                const reportText = document.getElementById('report-preview').textContent;
                copyToClipboard(reportText);
                showSaveNotification('Relatório copiado!');
            });
            
            // Download report button
            document.getElementById('download-report-btn').addEventListener('click', function() {
                const reportText = document.getElementById('report-preview').textContent;
                downloadTextFile(reportText, 'relatorio-diario-brave.txt');
            });
            
            // Export data button
            document.getElementById('export-data-btn').addEventListener('click', function() {
                exportData();
            });
            
            // Save all data button
            document.getElementById('save-all-data').addEventListener('click', function() {
                saveAllData();
                showSaveNotification();
            });
            
            // Close modals
            document.querySelectorAll('.modal-close, .modal-close-btn').forEach(element => {
                element.addEventListener('click', function() {
                    const modal = this.closest('.modal');
                    closeModal(modal.id);
                });
            });
            
            // Close modal when clicking outside
            document.querySelectorAll('.modal').forEach(modal => {
                modal.addEventListener('click', function(e) {
                    if (e.target === this) {
                        closeModal(this.id);
                    }
                });
            });
        }
        
        // Setup editable fields
        function setupEditableFields() {
            document.querySelectorAll('.editable').forEach(field => {
                field.addEventListener('blur', function() {
                    // Recalculate totals when an editable field is changed
                    calculateTableTotals();
                    
                    // Update overview metrics
                    updateOverviewMetrics();
                });
                
                field.addEventListener('keydown', function(e) {
                    if (e.key === 'Enter') {
                        e.preventDefault();
                        this.blur();
                    }
                });
            });
            
            document.querySelectorAll('.meeting-status').forEach(select => {
                select.addEventListener('change', function() {
                    updateOverviewMetrics();
                });
            });
        }
        
        // Setup delete meeting buttons
        function setupDeleteMeetingButtons() {
            document.querySelectorAll('.btn-delete-meeting').forEach(button => {
                button.addEventListener('click', function() {
                    const row = this.closest('tr');
                    if (confirm('Tem certeza que deseja excluir esta reunião?')) {
                        row.remove();
                        updateOverviewMetrics();
                        showSaveNotification('Reunião excluída!');
                    }
                });
            });
        }
        
        // Calculate table totals
        function calculateTableTotals() {
            // Calculate SDR daily totals
            calculateSDRTableTotals('sdr-daily-table');
            calculateSDRTableTotals('sdr-weekly-table');
            calculateSDRTableTotals('sdr-monthly-table');
            
            // Calculate Executive daily totals
            calculateExecTableTotals('exec-daily-table');
            calculateExecTableTotals('exec-weekly-table');
            calculateExecTableTotals('exec-monthly-table');
        }
        
        // Calculate SDR table totals
        function calculateSDRTableTotals(tableId) {
            const table = document.getElementById(tableId);
            if (!table) return;
            
            const rows = table.querySelectorAll('tbody tr:not(:last-child)');
            let totalLeads = 0;
            let totalAppointments = 0;
            let totalNoShows = 0;
            
            rows.forEach(row => {
                const leads = parseInt(row.cells[1].textContent) || 0;
                const appointments = parseInt(row.cells[2].textContent) || 0;
                const noShows = parseInt(row.cells[3].textContent) || 0;
                
                totalLeads += leads;
                totalAppointments += appointments;
                totalNoShows += noShows;
                
                // Calculate conversion rate for this row
                const conversionRate = leads > 0 ? Math.round((appointments / leads) * 100) : 0;
                row.cells[4].textContent = conversionRate + '%';
            });
            
            // Update totals row
            const totalsRow = table.querySelector('tbody tr:last-child');
            totalsRow.cells[1].textContent = totalLeads;
            totalsRow.cells[2].textContent = totalAppointments;
            totalsRow.cells[3].textContent = totalNoShows;
            
            // Calculate total conversion rate
            const totalConversionRate = totalLeads > 0 ? Math.round((totalAppointments / totalLeads) * 100) : 0;
            totalsRow.cells[4].textContent = totalConversionRate + '%';
        }
        
        // Calculate Executive table totals
        function calculateExecTableTotals(tableId) {
            const table = document.getElementById(tableId);
            if (!table) return;
            
            const rows = table.querySelectorAll('tbody tr:not(:last-child)');
            let totalDiagnostic = 0;
            let totalPresentation = 0;
            let totalProposals = 0;
            let totalClosings = 0;
            let totalValue = 0;
            
            rows.forEach(row => {
                const diagnostic = parseInt(row.cells[1].textContent) || 0;
                const presentation = parseInt(row.cells[2].textContent) || 0;
                const proposals = parseInt(row.cells[3].textContent) || 0;
                const closings = parseInt(row.cells[4].textContent) || 0;
                const value = parseFloat(row.cells[5].textContent.replace(/[^\d.-]/g, '')) || 0;
                
                totalDiagnostic += diagnostic;
                totalPresentation += presentation;
                totalProposals += proposals;
                totalClosings += closings;
                totalValue += value;
            });
            
            // Update totals row
            const totalsRow = table.querySelector('tbody tr:last-child');
            totalsRow.cells[1].textContent = totalDiagnostic;
            totalsRow.cells[2].textContent = totalPresentation;
            totalsRow.cells[3].textContent = totalProposals;
            totalsRow.cells[4].textContent = totalClosings;
            totalsRow.cells[5].textContent = totalValue.toLocaleString('pt-BR');
        }
        
        // Update overview metrics based on table data
        function updateOverviewMetrics() {
            // Get SDR data from daily table
            const sdrTable = document.getElementById('sdr-daily-table');
            const sdrTotalsRow = sdrTable.querySelector('tbody tr:last-child');
            
            const totalLeads = parseInt(sdrTotalsRow.cells[1].textContent) || 0;
            const totalAppointments = parseInt(sdrTotalsRow.cells[2].textContent) || 0;
            const totalNoShows = parseInt(sdrTotalsRow.cells[3].textContent) || 0;
            const conversionRate = sdrTotalsRow.cells[4].textContent;
            
            // Get Executive data from daily table
            const execTable = document.getElementById('exec-daily-table');
            const execTotalsRow = execTable.querySelector('tbody tr:last-child');
            
            const totalMeetings = parseInt(execTotalsRow.cells[1].textContent) || 0;
            const totalProposals = parseInt(execTotalsRow.cells[3].textContent) || 0;
            const totalClosings = parseInt(execTotalsRow.cells[4].textContent) || 0;
            
            // Count active negotiations
            const meetingsTable = document.getElementById('meetings-table');
            const meetingRows = meetingsTable.querySelectorAll('tbody tr');
            let activeNegotiations = 0;
            
            meetingRows.forEach(row => {
                const type = row.cells[3].textContent;
                const status = row.querySelector('.meeting-status').value;
                
                if (type === 'Batida de Martelo' && status !== 'Cancelada') {
                    activeNegotiations++;
                }
            });
            
            // Update the metrics
            document.getElementById('total-leads').textContent = totalLeads;
            document.getElementById('total-appointments').textContent = totalAppointments;
            document.getElementById('total-meetings').textContent = totalMeetings;
            document.getElementById('total-noshows').textContent = totalNoShows;
            document.getElementById('conversion-rate').textContent = conversionRate;
            document.getElementById('total-proposals').textContent = totalProposals;
            document.getElementById('active-negotiations').textContent = activeNegotiations;
            document.getElementById('total-closings').textContent = totalClosings;
        }
        
        // Save metrics from modal
        function saveMetrics() {
            const leads = document.getElementById('metric-leads').value;
            const appointments = document.getElementById('metric-appointments').value;
            const meetings = document.getElementById('metric-meetings').value;
            const noshows = document.getElementById('metric-noshows').value;
            const proposals = document.getElementById('metric-proposals').value;
            const negotiations = document.getElementById('metric-negotiations').value;
            const closings = document.getElementById('metric-closings').value;
            const conversion = document.getElementById('metric-conversion').value;
            
            // Update overview metrics
            document.getElementById('total-leads').textContent = leads;
            document.getElementById('total-appointments').textContent = appointments;
            document.getElementById('total-meetings').textContent = meetings;
            document.getElementById('total-noshows').textContent = noshows;
            document.getElementById('total-proposals').textContent = proposals;
            document.getElementById('active-negotiations').textContent = negotiations;
            document.getElementById('total-closings').textContent = closings;
            document.getElementById('conversion-rate').textContent = conversion + '%';
            
            // Update SDR table
            const sdrTable = document.getElementById('sdr-daily-table');
            const sdrRows = sdrTable.querySelectorAll('tbody tr:not(:last-child)');
            
            if (sdrRows.length === 2) {
                // Assuming Emily is first, Erima is second
                const emilyLeads = Math.round(leads * 0.57); // Just an example distribution
                const emilyAppointments = Math.round(appointments * 0.58);
                const emilyNoShows = Math.round(noshows * 0.33);
                
                const erimaLeads = leads - emilyLeads;
                const erimaAppointments = appointments - emilyAppointments;
                const erimaNoShows = noshows - emilyNoShows;
                
                sdrRows[0].cells[1].textContent = emilyLeads;
                sdrRows[0].cells[2].textContent = emilyAppointments;
                sdrRows[0].cells[3].textContent = emilyNoShows;
                
                sdrRows[1].cells[1].textContent = erimaLeads;
                sdrRows[1].cells[2].textContent = erimaAppointments;
                sdrRows[1].cells[3].textContent = erimaNoShows;
                
                calculateSDRTableTotals('sdr-daily-table');
            }
            
            // Update Executive table
            const execTable = document.getElementById('exec-daily-table');
            const execRows = execTable.querySelectorAll('tbody tr:not(:last-child)');
            
            if (execRows.length === 2) {
                // Assuming Elias is first, Jessé is second
                const eliasDiagnostic = Math.round(meetings * 0.56);
                const eliasPresentation = Math.round(proposals * 0.6);
                const eliasProposals = Math.round(proposals * 0.4);
                const eliasClosings = Math.round(closings * 0.5);
                
                const jesseDiagnostic = meetings - eliasDiagnostic;
                const jessePresentation = proposals - eliasPresentation;
                const jesseProposals = proposals - eliasProposals;
                const jesseClosings = closings - eliasClosings;
                
                execRows[0].cells[1].textContent = eliasDiagnostic;
                execRows[0].cells[2].textContent = eliasPresentation;
                execRows[0].cells[3].textContent = eliasProposals;
                execRows[0].cells[4].textContent = eliasClosings;
                
                execRows[1].cells[1].textContent = jesseDiagnostic;
                execRows[1].cells[2].textContent = jessePresentation;
                execRows[1].cells[3].textContent = jesseProposals;
                execRows[1].cells[4].textContent = jesseClosings;
                
                calculateExecTableTotals('exec-daily-table');
            }
            
            // Save data to localStorage
            saveAllData();
        }
        
        // Save funnel data
        function saveFunnel() {
            const leads = document.getElementById('funnel-leads').value;
            const qualified = document.getElementById('funnel-qualified').value;
            const scheduled = document.getElementById('funnel-scheduled').value;
            const diagnostic = document.getElementById('funnel-diagnostic').value;
            const presentation = document.getElementById('funnel-presentation').value;
            const closed = document.getElementById('funnel-closed').value;
            
            // Calculate percentages and heights
            const maxHeight = 180; // Maximum height in pixels for the funnel bars
            const maxLeads = Math.max(leads, 1); // Avoid division by zero
            
            const qualifiedPercent = Math.round((qualified / maxLeads) * 100);
            const scheduledPercent = Math.round((scheduled / maxLeads) * 100);
            const diagnosticPercent = Math.round((diagnostic / maxLeads) * 100);
            const presentationPercent = Math.round((presentation / maxLeads) * 100);
            const closedPercent = Math.round((closed / maxLeads) * 100);
            
            const qualifiedHeight = Math.round((qualified / maxLeads) * maxHeight);
            const scheduledHeight = Math.round((scheduled / maxLeads) * maxHeight);
            const diagnosticHeight = Math.round((diagnostic / maxLeads) * maxHeight);
            const presentationHeight = Math.round((presentation / maxLeads) * maxHeight);
            const closedHeight = Math.round((closed / maxLeads) * maxHeight);
            
            // Update funnel bars
            const funnel = document.getElementById('sales-funnel');
            const stages = funnel.querySelectorAll('.funnel-stage');
            
            // Update leads stage
            stages[0].querySelector('.funnel-bar').style.height = maxHeight + 'px';
            stages[0].querySelector('.funnel-value').textContent = leads;
            stages[0].querySelector('.funnel-percent').textContent = '100%';
            
            // Update qualified stage
            stages[1].querySelector('.funnel-bar').style.height = qualifiedHeight + 'px';
            stages[1].querySelector('.funnel-value').textContent = qualified;
            stages[1].querySelector('.funnel-percent').textContent = qualifiedPercent + '%';
            
            // Update scheduled stage
            stages[2].querySelector('.funnel-bar').style.height = scheduledHeight + 'px';
            stages[2].querySelector('.funnel-value').textContent = scheduled;
            stages[2].querySelector('.funnel-percent').textContent = scheduledPercent + '%';
            
            // Update diagnostic stage
            stages[3].querySelector('.funnel-bar').style.height = diagnosticHeight + 'px';
            stages[3].querySelector('.funnel-value').textContent = diagnostic;
            stages[3].querySelector('.funnel-percent').textContent = diagnosticPercent + '%';
            
            // Update presentation stage
            stages[4].querySelector('.funnel-bar').style.height = presentationHeight + 'px';
            stages[4].querySelector('.funnel-value').textContent = presentation;
            stages[4].querySelector('.funnel-percent').textContent = presentationPercent + '%';
            
            // Update closed stage
            stages[5].querySelector('.funnel-bar').style.height = closedHeight + 'px';
            stages[5].querySelector('.funnel-value').textContent = closed;
            stages[5].querySelector('.funnel-percent').textContent = closedPercent + '%';
            
            // Save data to localStorage
            saveAllData();
        }
        
        // Add new meeting
        function addNewMeeting() {
            const time = document.getElementById('new-meeting-time').value;
            const client = document.getElementById('new-meeting-client').value;
            const executive = document.getElementById('new-meeting-executive').value;
            const type = document.getElementById('new-meeting-type').value;
            const status = document.getElementById('new-meeting-status').value;
            
            // Validate required fields
            if (!time || !client || !executive || !type || !status) {
                alert('Por favor, preencha todos os campos!');
                return false;
            }
            
            // Create new meeting row
            const table = document.getElementById('meetings-table').querySelector('tbody');
            const newRow = document.createElement('tr');
            newRow.setAttribute('data-id', nextMeetingId);
            
            newRow.innerHTML = `
                <td contenteditable="true" class="editable">${time}</td>
                <td contenteditable="true" class="editable">${client}</td>
                <td contenteditable="true" class="editable">${executive}</td>
                <td contenteditable="true" class="editable">${type}</td>
                <td>
                    <select class="meeting-status">
                        <option value="Realizada" ${status === 'Realizada' ? 'selected' : ''}>Realizada</option>
                        <option value="No-Show" ${status === 'No-Show' ? 'selected' : ''}>No-Show</option>
                        <option value="Reagendada" ${status === 'Reagendada' ? 'selected' : ''}>Reagendada</option>
                        <option value="Cancelada" ${status === 'Cancelada' ? 'selected' : ''}>Cancelada</option>
                    </select>
                </td>
                <td>
                    <button class="btn-delete-meeting" data-id="${nextMeetingId}">
                        <i class="fas fa-trash"></i>
                    </button>
                </td>
            `;
            
            table.appendChild(newRow);
            nextMeetingId++;
            
            // Add event listener to the status select
            const statusSelect = newRow.querySelector('.meeting-status');
            statusSelect.addEventListener('change', function() {
                updateOverviewMetrics();
            });
            
            // Add event listener to the delete button
            const deleteButton = newRow.querySelector('.btn-delete-meeting');
            deleteButton.addEventListener('click', function() {
                if (confirm('Tem certeza que deseja excluir esta reunião?')) {
                    newRow.remove();
                    updateOverviewMetrics();
                    showSaveNotification('Reunião excluída!');
                }
            });
            
            // Add event listeners to editable fields
            newRow.querySelectorAll('.editable').forEach(field => {
                field.addEventListener('blur', function() {
                    updateOverviewMetrics();
                });
                
                field.addEventListener('keydown', function(e) {
                    if (e.key === 'Enter') {
                        e.preventDefault();
                        this.blur();
                    }
                });
            });
            
            // Reset form
            document.getElementById('new-meeting-time').value = '';
            document.getElementById('new-meeting-client').value = '';
            document.getElementById('new-meeting-executive').value = '';
            document.getElementById('new-meeting-type').value = '';
            document.getElementById('new-meeting-status').value = '';
            
            // Update metrics
            updateOverviewMetrics();
            
            // Save data to localStorage
            saveAllData();
            
            return true;
        }
        
        // Generate report
        function generateReport() {
            const date = new Date(document.getElementById('current-date').value);
            const formattedDate = date.toLocaleDateString('pt-BR');
            
            // Get SDR data
            const sdrTable = document.getElementById('sdr-daily-table');
            const sdrRows = sdrTable.querySelectorAll('tbody tr');
            
            // Get Executive data
            const execTable = document.getElementById('exec-daily-table');
            const execRows = execTable.querySelectorAll('tbody tr');
            
            // Get meeting data
            const meetingsTable = document.getElementById('meetings-table');
            const meetingRows = meetingsTable.querySelectorAll('tbody tr');
            
            // Format SDR data
            let sdrData = '';
            sdrRows.forEach((row, index) => {
                if (index < sdrRows.length - 1) {
                    const name = row.cells[0].textContent;
                    const leads = row.cells[1].textContent;
                    const appointments = row.cells[2].textContent;
                    const noShows = row.cells[3].textContent;
                    const conversion = row.cells[4].textContent;
                    
                    sdrData += `| ${name} | ${leads} | ${appointments} | ${noShows} | ${conversion} |\n`;
                } else {
                    const leads = row.cells[1].textContent;
                    const appointments = row.cells[2].textContent;
                    const noShows = row.cells[3].textContent;
                    const conversion = row.cells[4].textContent;
                    
                    sdrData += `| **TOTAL** | **${leads}** | **${appointments}** | **${noShows}** | **${conversion}** |\n`;
                }
            });
            
            // Format Executive data
            let execData = '';
            let totalDiagnostic = 0;
            let totalPresentation = 0;
            let totalClosing = 0;
            let totalExecMeetings = 0;
            let totalValue = 0;
            let closedClients = [];
            
            execRows.forEach((row, index) => {
                if (index < execRows.length - 1) {
                    const name = row.cells[0].textContent;
                    const diagnostic = parseInt(row.cells[1].textContent) || 0;
                    const presentation = parseInt(row.cells[2].textContent) || 0;
                    const closing = parseInt(row.cells[4].textContent) || 0;
                    const total = diagnostic + presentation + closing;
                    
                    totalDiagnostic += diagnostic;
                    totalPresentation += presentation;
                    totalClosing += closing;
                    totalExecMeetings += total;
                    totalValue += parseFloat(row.cells[5].textContent.replace(/[^\d.-]/g, '')) || 0;
                    
                    execData += `| ${name} | ${diagnostic} | ${presentation} | ${closing} | ${total} |\n`;
                }
            });
            
            execData += `| **TOTAL** | **${totalDiagnostic}** | **${totalPresentation}** | **${totalClosing}** | **${totalExecMeetings}** |\n`;
            
            // Get closed clients
            meetingRows.forEach(row => {
                const client = row.cells[1].textContent;
                const type = row.cells[3].textContent;
                const status = row.querySelector('.meeting-status').value;
                
                if (type === 'Batida de Martelo' && status === 'Realizada') {
                    closedClients.push(client);
                }
            });
            
            // Get challenges and no-shows
            let challenges = [];
            meetingRows.forEach(row => {
                const client = row.cells[1].textContent;
                const type = row.cells[3].textContent;
                const status = row.querySelector('.meeting-status').value;
                
                if (status === 'No-Show') {
                    challenges.push(`No-show de cliente potencial de alto valor (${client})`);
                }
            });
            
            // Add some dummy challenges for demonstration
            if (challenges.length < 2) {
                challenges.push('Cliente Empresa 123 Ltda. solicitou revisão de proposta com desconto adicional');
                challenges.push('Delay na assinatura do contrato da Empresa DEF Inc. (questões jurídicas)');
            }
            
            // Format challenges
            let challengesData = '';
            challenges.forEach((challenge, index) => {
                challengesData += `${index + 1}. ${challenge}\n`;
            });
            
            // Build the report
            let report = `# 📊 REPORT DIÁRIO DE VENDAS | BRAVE EDUCAÇÃO
**Data:** ${formattedDate}

## 🎯 PERFORMANCE SDRs
| SDR | Leads Gerados | Agendamentos | No-Shows | Taxa de Conversão |
|-----|---------------|--------------|----------|------------------|
${sdrData}

## 🤝 REUNIÕES DO DIA
| Executivo | Diagnóstico | Apresentação | Batida de Martelo | Total |
|-----------|-------------|--------------|-------------------|-------|
${execData}

## 📈 CONVERSÃO SDR → CLOSER
* Leads qualificados passados: **${document.getElementById('funnel-qualified').value || '19'}**
* Reuniões realizadas: **${totalDiagnostic}**
* Taxa de conversão: **${Math.round((totalDiagnostic / (document.getElementById('funnel-qualified').value || 19)) * 100)}%**

## 📝 PROPOSTAS
* Propostas enviadas hoje: **${document.getElementById('total-proposals').textContent}**
* Negociações em andamento: **${document.getElementById('active-negotiations').textContent}**
* Prazo médio de resposta: **3 dias**

## 🏆 FECHAMENTOS
* Contratos fechados hoje: **${totalClosing}**
* Valor total: **R$ ${totalValue.toLocaleString('pt-BR')}**
* Clientes: ${closedClients.join(', ') || 'Nenhum fechamento hoje'}

## ⚠️ DESAFIOS
${challengesData}

## 🔍 INSIGHTS
* Maior interesse em treinamentos corporativos customizados
* Objeção recorrente: preço alto para o orçamento atual (32%)
* Oportunidade: aumentar cross-sell em clientes da base

---
*Relatório gerado automaticamente pelo Dashboard Comercial Brave Educação*`;
            
            // Update the report preview
            document.getElementById('report-preview').textContent = report;
        }
        
        // Save all data to localStorage
        function saveAllData() {
            const data = {
                date: document.getElementById('current-date').value,
                metrics: {
                    leads: document.getElementById('total-leads').textContent,
                    appointments: document.getElementById('total-appointments').textContent,
                    meetings: document.getElementById('total-meetings').textContent,
                    noshows: document.getElementById('total-noshows').textContent,
                    conversion: document.getElementById('conversion-rate').textContent,
                    proposals: document.getElementById('total-proposals').textContent,
                    negotiations: document.getElementById('active-negotiations').textContent,
                    closings: document.getElementById('total-closings').textContent
                },
                funnel: {
                    leads: document.getElementById('funnel-leads') ? document.getElementById('funnel-leads').value : 21,
                    qualified: document.getElementById('funnel-qualified') ? document.getElementById('funnel-qualified').value : 19,
                    scheduled: document.getElementById('funnel-scheduled') ? document.getElementById('funnel-scheduled').value : 12,
                    diagnostic: document.getElementById('funnel-diagnostic') ? document.getElementById('funnel-diagnostic').value : 9,
                    presentation: document.getElementById('funnel-presentation') ? document.getElementById('funnel-presentation').value : 5,
                    closed: document.getElementById('funnel-closed') ? document.getElementById('funnel-closed').value : 2
                },
                sdrDaily: getSdrTableData('sdr-daily-table'),
                sdrWeekly: getSdrTableData('sdr-weekly-table'),
                sdrMonthly: getSdrTableData('sdr-monthly-table'),
                execDaily: getExecTableData('exec-daily-table'),
                execWeekly: getExecTableData('exec-weekly-table'),
                execMonthly: getExecTableData('exec-monthly-table'),
                meetings: getMeetingsData()
            };
            
            localStorage.setItem('braveCommercialDashboard', JSON.stringify(data));
        }
        
        // Load data from localStorage
        function loadDataFromStorage() {
            const savedData = localStorage.getItem('braveCommercialDashboard');
            if (!savedData) return;
            
            const data = JSON.parse(savedData);
            
            // Set date
            if (data.date) {
                document.getElementById('current-date').value = data.date;
            }
            
            // Set metrics
            if (data.metrics) {
                document.getElementById('total-leads').textContent = data.metrics.leads;
                document.getElementById('total-appointments').textContent = data.metrics.appointments;
                document.getElementById('total-meetings').textContent = data.metrics.meetings;
                document.getElementById('total-noshows').textContent = data.metrics.noshows;
                document.getElementById('conversion-rate').textContent = data.metrics.conversion;
                document.getElementById('total-proposals').textContent = data.metrics.proposals;
                document.getElementById('active-negotiations').textContent = data.metrics.negotiations;
                document.getElementById('total-closings').textContent = data.metrics.closings;
                
                // Set funnel modal values
                if (document.getElementById('metric-leads')) {
                    document.getElementById('metric-leads').value = data.metrics.leads;
                    document.getElementById('metric-appointments').value = data.metrics.appointments;
                    document.getElementById('metric-meetings').value = data.metrics.meetings;
                    document.getElementById('metric-noshows').value = data.metrics.noshows;
                    document.getElementById('metric-proposals').value = data.metrics.proposals;
                    document.getElementById('metric-negotiations').value = data.metrics.negotiations;
                    document.getElementById('metric-closings').value = data.metrics.closings;
                    document.getElementById('metric-conversion').value = data.metrics.conversion.replace('%', '');
                }
            }
            
            // Set funnel
            if (data.funnel) {
                document.getElementById('funnel-leads').value = data.funnel.leads;
                document.getElementById('funnel-qualified').value = data.funnel.qualified;
                document.getElementById('funnel-scheduled').value = data.funnel.scheduled;
                document.getElementById('funnel-diagnostic').value = data.funnel.diagnostic;
                document.getElementById('funnel-presentation').value = data.funnel.presentation;
                document.getElementById('funnel-closed').value = data.funnel.closed;
                
                // Update funnel visualization
                saveFunnel();
            }
            
            // Set tables data
            if (data.sdrDaily) {
                setSdrTableData('sdr-daily-table', data.sdrDaily);
            }
            
            if (data.sdrWeekly) {
                setSdrTableData('sdr-weekly-table', data.sdrWeekly);
            }
            
            if (data.sdrMonthly) {
                setSdrTableData('sdr-monthly-table', data.sdrMonthly);
            }
            
            if (data.execDaily) {
                setExecTableData('exec-daily-table', data.execDaily);
            }
            
            if (data.execWeekly) {
                setExecTableData('exec-weekly-table', data.execWeekly);
            }
            
            if (data.execMonthly) {
                setExecTableData('exec-monthly-table', data.execMonthly);
            }
            
            // Set meetings
            if (data.meetings) {
                setMeetingsData(data.meetings);
            }
            
            // Calculate totals
            calculateTableTotals();
        }
        
        // Get SDR table data
        function getSdrTableData(tableId) {
            const table = document.getElementById(tableId);
            if (!table) return [];
            
            const rows = table.querySelectorAll('tbody tr:not(:last-child)');
            const data = [];
            
            rows.forEach(row => {
                data.push({
                    name: row.cells[0].textContent,
                    leads: row.cells[1].textContent,
                    appointments: row.cells[2].textContent,
                    noshows: row.cells[3].textContent
                });
            });
            
            return data;
        }
        
        // Set SDR table data
        function setSdrTableData(tableId, data) {
            const table = document.getElementById(tableId);
            if (!table) return;
            
            const rows = table.querySelectorAll('tbody tr:not(:last-child)');
            
            data.forEach((item, index) => {
                if (index < rows.length) {
                    rows[index].cells[1].textContent = item.leads;
                    rows[index].cells[2].textContent = item.appointments;
                    rows[index].cells[3].textContent = item.noshows;
                }
            });
        }
        
        // Get Executive table data
        function getExecTableData(tableId) {
            const table = document.getElementById(tableId);
            if (!table) return [];
            
            const rows = table.querySelectorAll('tbody tr:not(:last-child)');
            const data = [];
            
            rows.forEach(row => {
                data.push({
                    name: row.cells[0].textContent,
                    diagnostic: row.cells[1].textContent,
                    presentation: row.cells[2].textContent,
                    proposals: row.cells[3].textContent,
                    closings: row.cells[4].textContent,
                    value: row.cells[5].textContent
                });
            });
            
            return data;
        }
        
        // Set Executive table data
        function setExecTableData(tableId, data) {
            const table = document.getElementById(tableId);
            if (!table) return;
            
            const rows = table.querySelectorAll('tbody tr:not(:last-child)');
            
            data.forEach((item, index) => {
                if (index < rows.length) {
                    rows[

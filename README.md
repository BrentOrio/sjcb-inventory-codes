<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SJCB Equipment & Inventory Management System</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* Base Styles */
        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --accent: #e74c3c;
            --success: #27ae60;
            --warning: #f39c12;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --gray: #95a5a6;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f8f9fa;
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header & Navigation */
        header {
            background-color: var(--primary);
            color: white;
            padding: 1rem 0;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .logo h1 {
            font-size: 1.5rem;
            font-weight: 600;
        }
        
        .logo i {
            color: var(--secondary);
        }
        
        /* Global Navigation */
        nav ul {
            display: flex;
            list-style: none;
            gap: 20px;
        }
        
        nav a {
            color: white;
            text-decoration: none;
            padding: 8px 15px;
            border-radius: 4px;
            transition: background-color 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        nav a:hover, nav a.active {
            background-color: rgba(255, 255, 255, 0.1);
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        /* Breadcrumb Navigation */
        .breadcrumb {
            background-color: var(--light);
            padding: 10px 20px;
            border-radius: 4px;
            margin: 15px 0;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .breadcrumb a {
            color: var(--secondary);
            text-decoration: none;
        }
        
        .breadcrumb a:hover {
            text-decoration: underline;
        }
        
        .breadcrumb span {
            color: var(--gray);
        }
        
        /* Main Content */
        main {
            padding: 2rem 0;
        }
        
        .page-title {
            margin-bottom: 1.5rem;
            color: var(--primary);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        /* Dashboard Section */
        .dashboard {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .dashboard-card {
            background-color: white;
            border-radius: 8px;
            padding: 1.5rem;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s;
        }
        
        .dashboard-card:hover {
            transform: translateY(-5px);
        }
        
        .card-title {
            color: var(--gray);
            font-size: 0.9rem;
            margin-bottom: 10px;
        }
        
        .card-value {
            font-size: 2rem;
            font-weight: 700;
            color: var(--primary);
        }
        
        .card-trend {
            display: flex;
            align-items: center;
            gap: 5px;
            margin-top: 10px;
            font-size: 0.9rem;
        }
        
        .trend-up {
            color: var(--success);
        }
        
        .trend-down {
            color: var(--accent);
        }
        
        /* Inventory Table */
        .inventory-section {
            background-color: white;
            border-radius: 8px;
            padding: 1.5rem;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            margin-bottom: 30px;
        }
        
        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th {
            background-color: var(--light);
            padding: 12px 15px;
            text-align: left;
            font-weight: 600;
            color: var(--primary);
        }
        
        td {
            padding: 12px 15px;
            border-bottom: 1px solid #eee;
        }
        
        tr:hover {
            background-color: #f9f9f9;
        }
        
        .status {
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
        }
        
        .status-available {
            background-color: #d4edda;
            color: #155724;
        }
        
        .status-checked-out {
            background-color: #fff3cd;
            color: #856404;
        }
        
        .status-maintenance {
            background-color: #f8d7da;
            color: #721c24;
        }
        
        /* Form Styles */
        .form-section {
            background-color: white;
            border-radius: 8px;
            padding: 1.5rem;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            max-width: 800px;
            margin: 0 auto;
        }
        
        .form-group {
            margin-bottom: 1.5rem;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--primary);
        }
        
        input, select, textarea {
            width: 100%;
            padding: 10px 15px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
        }
        
        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: var(--secondary);
            box-shadow: 0 0 0 2px rgba(52, 152, 219, 0.2);
        }
        
        .form-hint {
            font-size: 0.85rem;
            color: var(--gray);
            margin-top: 5px;
        }
        
        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        
        .btn-primary {
            background-color: var(--secondary);
            color: white;
        }
        
        .btn-primary:hover {
            background-color: #2980b9;
        }
        
        .btn-success {
            background-color: var(--success);
            color: white;
        }
        
        .btn-success:hover {
            background-color: #219653;
        }
        
        .btn-warning {
            background-color: var(--warning);
            color: white;
        }
        
        .btn-warning:hover {
            background-color: #e67e22;
        }
        
        .btn-danger {
            background-color: var(--accent);
            color: white;
        }
        
        .btn-danger:hover {
            background-color: #c0392b;
        }
        
        /* Feedback Elements */
        .feedback-message {
            padding: 12px 15px;
            border-radius: 4px;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .feedback-success {
            background-color: #d4edda;
            color: #155724;
            border-left: 4px solid var(--success);
        }
        
        .feedback-error {
            background-color: #f8d7da;
            color: #721c24;
            border-left: 4px solid var(--accent);
        }
        
        .feedback-warning {
            background-color: #fff3cd;
            color: #856404;
            border-left: 4px solid var(--warning);
        }
        
        .feedback-info {
            background-color: #d1ecf1;
            color: #0c5460;
            border-left: 4px solid var(--secondary);
        }
        
        /* Toast Notifications */
        .toast-container {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 1000;
        }
        
        .toast {
            background-color: white;
            border-radius: 4px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
            padding: 15px;
            margin-top: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
            min-width: 300px;
            transform: translateX(100%);
            opacity: 0;
            transition: transform 0.3s, opacity 0.3s;
        }
        
        .toast.show {
            transform: translateX(0);
            opacity: 1;
        }
        
        .toast-success {
            border-left: 4px solid var(--success);
        }
        
        .toast-error {
            border-left: 4px solid var(--accent);
        }
        
        .toast-warning {
            border-left: 4px solid var(--warning);
        }
        
        .toast-info {
            border-left: 4px solid var(--secondary);
        }
        
        /* Progress Indicators */
        .progress-container {
            margin: 1rem 0;
        }
        
        .progress-bar {
            height: 8px;
            background-color: #eee;
            border-radius: 4px;
            overflow: hidden;
            margin-bottom: 5px;
        }
        
        .progress-fill {
            height: 100%;
            background-color: var(--secondary);
            width: 0%;
            transition: width 0.5s;
        }
        
        /* Tooltips */
        .tooltip {
            position: relative;
            display: inline-block;
        }
        
        .tooltip .tooltip-text {
            visibility: hidden;
            width: 200px;
            background-color: var(--primary);
            color: white;
            text-align: center;
            border-radius: 4px;
            padding: 8px;
            position: absolute;
            z-index: 1;
            bottom: 125%;
            left: 50%;
            transform: translateX(-50%);
            opacity: 0;
            transition: opacity 0.3s;
            font-size: 0.85rem;
        }
        
        .tooltip:hover .tooltip-text {
            visibility: visible;
            opacity: 1;
        }
        
        /* Loading Spinner */
        .spinner {
            border: 3px solid #f3f3f3;
            border-top: 3px solid var(--secondary);
            border-radius: 50%;
            width: 30px;
            height: 30px;
            animation: spin 1s linear infinite;
            margin: 0 auto;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 1001;
            align-items: center;
            justify-content: center;
        }
        
        .modal-content {
            background-color: white;
            border-radius: 8px;
            padding: 2rem;
            max-width: 500px;
            width: 90%;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
        }
        
        /* Scroll Behavior */
        .scroll-progress {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background-color: #eee;
            z-index: 1002;
        }
        
        .scroll-progress-bar {
            height: 100%;
            background-color: var(--secondary);
            width: 0%;
            transition: width 0.1s;
        }
        
        /* Footer */
        footer {
            background-color: var(--primary);
            color: white;
            padding: 2rem 0;
            margin-top: 3rem;
        }
        
        .footer-content {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 2rem;
        }
        
        .footer-section {
            flex: 1;
            min-width: 250px;
        }
        
        .footer-section h3 {
            margin-bottom: 1rem;
            color: var(--secondary);
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }
            
            nav ul {
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .dashboard {
                grid-template-columns: 1fr;
            }
            
            .table-container {
                overflow-x: auto;
            }
        }
    </style>
</head>
<body>
    <!-- Scroll Progress Indicator -->
    <div class="scroll-progress">
        <div class="scroll-progress-bar" id="scrollProgress"></div>
    </div>
    
    <!-- Header with Global Navigation -->
    <header>
        <div class="container header-content">
            <div class="logo">
                <i class="fas fa-boxes"></i>
                <h1>SJCB Equipment & Inventory System</h1>
            </div>
            
            <nav>
                <ul>
                    <li><a href="#home" class="active"><i class="fas fa-home"></i> Dashboard</a></li>
                    <li><a href="#inventory"><i class="fas fa-box"></i> Inventory</a></li>
                    <li><a href="#checkout"><i class="fas fa-sign-out-alt"></i> Check Out</a></li>
                    <li><a href="#reports"><i class="fas fa-chart-bar"></i> Reports</a></li>
                    <li><a href="#settings"><i class="fas fa-cog"></i> Settings</a></li>
                </ul>
            </nav>
            
            <div class="user-info">
                <div class="status status-available">Online</div>
                <div>Welcome, Admin</div>
                <i class="fas fa-user-circle" style="font-size: 1.5rem;"></i>
            </div>
        </div>
    </header>
    
    <!-- Breadcrumb Navigation -->
    <div class="container">
        <div class="breadcrumb">
            <a href="#home">Home</a> <i class="fas fa-chevron-right"></i>
            <a href="#inventory">Inventory</a> <i class="fas fa-chevron-right"></i>
            <span>Manage Equipment</span>
        </div>
    </div>
    
    <!-- Main Content -->
    <main class="container">
        <!-- Page Title -->
        <h1 class="page-title"><i class="fas fa-tachometer-alt"></i> Dashboard Overview</h1>
        
        <!-- Informational Feedback: Dashboard Stats -->
        <div class="dashboard">
            <div class="dashboard-card">
                <div class="card-title">Total Equipment</div>
                <div class="card-value">247</div>
                <div class="card-trend trend-up">
                    <i class="fas fa-arrow-up"></i> 12% from last month
                </div>
            </div>
            
            <div class="dashboard-card">
                <div class="card-title">Checked Out</div>
                <div class="card-value">38</div>
                <div class="card-trend trend-down">
                    <i class="fas fa-arrow-down"></i> 5% from last week
                </div>
            </div>
            
            <div class="dashboard-card">
                <div class="card-title">Under Maintenance</div>
                <div class="card-value">14</div>
                <div class="status status-maintenance" style="display: inline-block; margin-top: 10px;">Requires Attention</div>
            </div>
            
            <div class="dashboard-card">
                <div class="card-title">Available</div>
                <div class="card-value">195</div>
                <div class="card-trend trend-up">
                    <i class="fas fa-arrow-up"></i> 8% from last month
                </div>
            </div>
        </div>
        
        <!-- Confirmation Feedback Example -->
        <div id="successMessage" class="feedback-message feedback-success" style="display: none;">
            <i class="fas fa-check-circle"></i>
            <div>Equipment item added successfully! The inventory has been updated.</div>
        </div>
        
        <!-- Error Feedback Example -->
        <div id="errorMessage" class="feedback-message feedback-error" style="display: none;">
            <i class="fas fa-exclamation-circle"></i>
            <div>Error: Please fill in all required fields marked with *</div>
        </div>
        
        <!-- Inventory Section with Tabbed Navigation -->
        <div class="inventory-section">
            <div class="section-header">
                <h2><i class="fas fa-boxes"></i> Equipment Inventory</h2>
                <div>
                    <button class="btn btn-primary" id="addEquipmentBtn">
                        <i class="fas fa-plus"></i> Add Equipment
                    </button>
                    <button class="btn btn-warning" id="exportBtn">
                        <i class="fas fa-file-export"></i> Export
                    </button>
                </div>
            </div>
            
            <!-- Tabbed Navigation -->
            <div style="display: flex; border-bottom: 2px solid #eee; margin-bottom: 1.5rem;">
                <div class="tab active" style="padding: 10px 20px; border-bottom: 2px solid var(--secondary); font-weight: 600; color: var(--secondary); cursor: pointer;">All Equipment</div>
                <div class="tab" style="padding: 10px 20px; cursor: pointer;">Available</div>
                <div class="tab" style="padding: 10px 20px; cursor: pointer;">Checked Out</div>
                <div class="tab" style="padding: 10px 20px; cursor: pointer;">Maintenance</div>
            </div>
            
            <!-- Search and Filter System -->
            <div style="display: flex; gap: 15px; margin-bottom: 1.5rem; flex-wrap: wrap;">
                <input type="text" placeholder="Search equipment..." style="flex: 2; min-width: 250px;">
                <select style="flex: 1; min-width: 150px;">
                    <option>All Categories</option>
                    <option>Electronics</option>
                    <option>Lab Equipment</option>
                    <option>Office Supplies</option>
                    <option>Sports Equipment</option>
                </select>
                <select style="flex: 1; min-width: 150px;">
                    <option>All Locations</option>
                    <option>Main Building</option>
                    <option>Science Lab</option>
                    <option>Gymnasium</option>
                    <option>Library</option>
                </select>
                <button class="btn btn-primary">Apply Filters</button>
            </div>
            
            <!-- Instructional Feedback -->
            <div class="feedback-message feedback-info">
                <i class="fas fa-info-circle"></i>
                <div>Click on any equipment row to view details. Use the action buttons to check out, return, or mark for maintenance.</div>
            </div>
            
            <!-- Inventory Table -->
            <div class="table-container">
                <table>
                    <thead>
                        <tr>
                            <th>ID</th>
                            <th>Equipment Name</th>
                            <th>Category</th>
                            <th>Location</th>
                            <th>Status</th>
                            <th>Last Checked</th>
                            <th>Actions</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>EQ-1001</td>
                            <td>Projector Epson 1020</td>
                            <td>Electronics</td>
                            <td>Room 201</td>
                            <td><span class="status status-available">Available</span></td>
                            <td>2023-10-15</td>
                            <td>
                                <button class="btn btn-success btn-sm" onclick="checkoutItem('EQ-1001')">
                                    <i class="fas fa-sign-out-alt"></i> Check Out
                                </button>
                            </td>
                        </tr>
                        <tr>
                            <td>EQ-1002</td>
                            <td>Microscope Binocular</td>
                            <td>Lab Equipment</td>
                            <td>Science Lab</td>
                            <td><span class="status status-checked-out">Checked Out</span></td>
                            <td>2023-10-20</td>
                            <td>
                                <button class="btn btn-primary btn-sm" onclick="returnItem('EQ-1002')">
                                    <i class="fas fa-sign-in-alt"></i> Return
                                </button>
                            </td>
                        </tr>
                        <tr>
                            <td>EQ-1003</td>
                            <td>Laptop Dell XPS 15</td>
                            <td>Electronics</td>
                            <td>IT Department</td>
                            <td><span class="status status-maintenance">Maintenance</span></td>
                            <td>2023-10-10</td>
                            <td>
                                <button class="btn btn-warning btn-sm tooltip">
                                    <i class="fas fa-wrench"></i> Repair
                                    <span class="tooltip-text">Mark this item as repaired and return to inventory</span>
                                </button>
                            </td>
                        </tr>
                        <tr>
                            <td>EQ-1004</td>
                            <td>Basketball (Official Size)</td>
                            <td>Sports Equipment</td>
                            <td>Gym Storage</td>
                            <td><span class="status status-available">Available</span></td>
                            <td>2023-10-18</td>
                            <td>
                                <button class="btn btn-success btn-sm" onclick="checkoutItem('EQ-1004')">
                                    <i class="fas fa-sign-out-alt"></i> Check Out
                                </button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
            
            <!-- Progress Feedback: Loading More Items -->
            <div id="loadingMore" style="text-align: center; margin-top: 20px; display: none;">
                <div class="spinner"></div>
                <p>Loading more equipment items...</p>
            </div>
            
            <!-- Infinite Scroll/Load More Button -->
            <div style="text-align: center; margin-top: 20px;">
                <button class="btn btn-primary" id="loadMoreBtn">
                    <i class="fas fa-sync-alt"></i> Load More Equipment
                </button>
            </div>
        </div>
        
        <!-- Form Section for Adding Equipment -->
        <div class="form-section" id="addEquipmentForm" style="display: none;">
            <h2 class="page-title"><i class="fas fa-plus-circle"></i> Add New Equipment</h2>
            
            <!-- Progress Feedback: Form Steps -->
            <div class="progress-container">
                <div class="progress-bar">
                    <div class="progress-fill" id="formProgress" style="width: 33%"></div>
                </div>
                <div style="display: flex; justify-content: space-between; font-size: 0.9rem;">
                    <span>Step 1: Basic Info</span>
                    <span>Step 2: Details</span>
                    <span>Step 3: Confirmation</span>
                </div>
            </div>
            
            <form id="equipmentForm">
                <div class="form-group">
                    <label for="equipmentName">Equipment Name *</label>
                    <input type="text" id="equipmentName" placeholder="e.g., Projector Epson 1020">
                    <div class="form-hint">Enter the full name of the equipment</div>
                </div>
                
                <div class="form-group">
                    <label for="category">Category *</label>
                    <select id="category">
                        <option value="">Select a category</option>
                        <option value="electronics">Electronics</option>
                        <option value="lab">Lab Equipment</option>
                        <option value="office">Office Supplies</option>
                        <option value="sports">Sports Equipment</option>
                        <option value="other">Other</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="location">Location *</label>
                    <select id="location">
                        <option value="">Select a location</option>
                        <option value="main">Main Building</option>
                        <option value="science">Science Lab</option>
                        <option value="gym">Gymnasium</option>
                        <option value="library">Library</option>
                        <option value="it">IT Department</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="quantity">Quantity *</label>
                    <input type="number" id="quantity" min="1" value="1">
                    <div class="form-hint">Enter the number of identical items</div>
                </div>
                
                <div class="form-group">
                    <label for="condition">Condition *</label>
                    <select id="condition">
                        <option value="excellent">Excellent</option>
                        <option value="good">Good</option>
                        <option value="fair">Fair</option>
                        <option value="poor">Poor (Needs Maintenance)</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="notes">Notes</label>
                    <textarea id="notes" rows="3" placeholder="Any additional information about this equipment..."></textarea>
                </div>
                
                <div style="display: flex; gap: 15px; margin-top: 2rem;">
                    <button type="button" class="btn btn-secondary" id="cancelForm">Cancel</button>
                    <button type="submit" class="btn btn-success">
                        <i class="fas fa-save"></i> Add Equipment
                    </button>
                </div>
            </form>
        </div>
        
        <!-- About/Documentation Section -->
        <div class="inventory-section">
            <h2 class="page-title"><i class="fas fa-info-circle"></i> About SJCB Inventory System</h2>
            
            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 2rem; margin-top: 1.5rem;">
                <div>
                    <h3 style="color: var(--primary); margin-bottom: 1rem;">System Purpose</h3>
                    <p>The SJCB Equipment & Inventory Management System is designed to track, manage, and optimize the use of all equipment across SJCB campuses. It provides real-time visibility into equipment availability, condition, and location.</p>
                </div>
                
                <div>
                    <h3 style="color: var(--primary); margin-bottom: 1rem;">Key Features</h3>
                    <ul style="padding-left: 1.5rem;">
                        <li>Real-time inventory tracking</li>
                        <li>Check-out/return management</li>
                        <li>Maintenance scheduling</li>
                        <li>Reporting and analytics</li>
                        <li>Multi-user access control</li>
                    </ul>
                </div>
                
                <div>
                    <h3 style="color: var(--primary); margin-bottom: 1rem;">Contact & Support</h3>
                    <p>For technical support or system issues, contact the IT Department:</p>
                    <p><i class="fas fa-envelope"></i> it-support@sjcb.edu</p>
                    <p><i class="fas fa-phone"></i> (123) 456-7890 ext. 555</p>
                </div>
            </div>
        </div>
    </main>
    
    <!-- Toast Container -->
    <div class="toast-container" id="toastContainer"></div>
    
    <!-- Modal for Confirmation -->
    <div class="modal" id="confirmationModal">
        <div class="modal-content">
            <h3><i class="fas fa-exclamation-triangle"></i> Confirm Action</h3>
            <p id="modalMessage">Are you sure you want to perform this action?</p>
            <div style="display: flex; gap: 15px; margin-top: 2rem;">
                <button class="btn btn-secondary" id="modalCancel">Cancel</button>
                <button class="btn btn-danger" id="modalConfirm">Confirm</button>
            </div>
        </div>
    </div>
    
    <!-- Footer -->
    <footer>
        <div class="container footer-content">
            <div class="footer-section">
                <h3>SJCB Equipment System</h3>
                <p>St. John's College of Business Inventory Management System</p>
                <p>Version 2.1.4 | Last updated: October 2023</p>
            </div>
            
            <div class="footer-section">
                <h3>Quick Links</h3>
                <ul style="list-style: none; padding: 0;">
                    <li><a href="#home" style="color: white;">Dashboard</a></li>
                    <li><a href="#inventory" style="color: white;">Inventory</a></li>
                    <li><a href="#reports" style="color: white;">Reports</a></li>
                    <li><a href="#help" style="color: white;">Help & Support</a></li>
                </ul>
            </div>
            
            <div class="footer-section">
                <h3>System Status</h3>
                <div class="status status-available" style="background-color: rgba(255,255,255,0.1);">All Systems Operational</div>
                <p style="margin-top: 10px;">Uptime: 99.8% this month</p>
            </div>
        </div>
    </footer>
    
    <script>
        // Toast Notification System
        function showToast(message, type = 'info') {
            const toastContainer = document.getElementById('toastContainer');
            const toast = document.createElement('div');
            toast.className = `toast toast-${type}`;
            
            let icon = 'fa-info-circle';
            if (type === 'success') icon = 'fa-check-circle';
            if (type === 'error') icon = 'fa-exclamation-circle';
            if (type === 'warning') icon = 'fa-exclamation-triangle';
            
            toast.innerHTML = `
                <i class="fas ${icon}"></i>
                <div>${message}</div>
            `;
            
            toastContainer.appendChild(toast);
            
            // Show toast
            setTimeout(() => {
                toast.classList.add('show');
            }, 10);
            
            // Hide and remove toast after 4 seconds
            setTimeout(() => {
                toast.classList.remove('show');
                setTimeout(() => {
                    if (toast.parentNode) {
                        toast.parentNode.removeChild(toast);
                    }
                }, 300);
            }, 4000);
        }
        
        // Scroll Progress Indicator
        window.addEventListener('scroll', function() {
            const scrollProgress = document.getElementById('scrollProgress');
            const windowHeight = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const scrolled = (window.pageYOffset / windowHeight) * 100;
            scrollProgress.style.width = `${scrolled}%`;
        });
        
        // Form Submission with Validation
        document.getElementById('equipmentForm')?.addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Get form values
            const name = document.getElementById('equipmentName').value;
            const category = document.getElementById('category').value;
            const location = document.getElementById('location').value;
            const quantity = document.getElementById('quantity').value;
            
            // Validation
            if (!name || !category || !location || !quantity) {
                // Show error feedback
                document.getElementById('errorMessage').style.display = 'flex';
                showToast('Please fill in all required fields', 'error');
                
                // Shake animation for empty required fields
                if (!name) document.getElementById('equipmentName').style.borderColor = 'var(--accent)';
                if (!category) document.getElementById('category').style.borderColor = 'var(--accent)';
                if (!location) document.getElementById('location').style.borderColor = 'var(--accent)';
                if (!quantity) document.getElementById('quantity').style.borderColor = 'var(--accent)';
                
                return;
            }
            
            // Show loading/processing feedback
            document.getElementById('formProgress').style.width = '100%';
            showToast('Processing your request...', 'info');
            
            // Simulate API call delay
            setTimeout(() => {
                // Show success feedback
                document.getElementById('successMessage').style.display = 'flex';
                showToast('Equipment added successfully to inventory!', 'success');
                
                // Reset form
                document.getElementById('equipmentForm').reset();
                document.getElementById('formProgress').style.width = '33%';
                
                // Hide form after success
                setTimeout(() => {
                    document.getElementById('addEquipmentForm').style.display = 'none';
                    document.getElementById('successMessage').style.display = 'none';
                }, 3000);
            }, 1500);
        });
        
        // Add Equipment Button
        document.getElementById('addEquipmentBtn')?.addEventListener('click', function() {
            document.getElementById('addEquipmentForm').style.display = 'block';
            document.getElementById('errorMessage').style.display = 'none';
            
            // Scroll to form
            document.getElementById('addEquipmentForm').scrollIntoView({ behavior: 'smooth' });
        });
        
        // Cancel Form Button
        document.getElementById('cancelForm')?.addEventListener('click', function() {
            document.getElementById('addEquipmentForm').style.display = 'none';
            document.getElementById('equipmentForm').reset();
            document.getElementById('formProgress').style.width = '33%';
            showToast('Form cancelled', 'info');
        });
        
        // Check Out Item Function
        function checkoutItem(itemId) {
            document.getElementById('modalMessage').textContent = `Are you sure you want to check out item ${itemId}?`;
            document.getElementById('confirmationModal').style.display = 'flex';
            
            // Set up confirmation action
            document.getElementById('modalConfirm').onclick = function() {
                // Simulate processing
                showToast(`Checking out item ${itemId}...`, 'info');
                
                setTimeout(() => {
                    showToast(`Item ${itemId} checked out successfully!`, 'success');
                    document.getElementById('confirmationModal').style.display = 'none';
                    
                    // In a real app, update the UI here
                }, 1000);
            };
        }
        
        // Return Item Function
        function returnItem(itemId) {
            // Show progress feedback
            showToast(`Processing return for item ${itemId}...`, 'info');
            
            setTimeout(() => {
                showToast(`Item ${itemId} returned successfully!`, 'success');
                
                // Show instructional feedback for next steps
                setTimeout(() => {
                    showToast('Please inspect the equipment and update its condition if needed.', 'info');
                }, 1000);
            }, 1500);
        }
        
        // Load More Button (Infinite Scroll simulation)
        document.getElementById('loadMoreBtn')?.addEventListener('click', function() {
            const btn = this;
            const loadingDiv = document.getElementById('loadingMore');
            
            btn.style.display = 'none';
            loadingDiv.style.display = 'block';
            
            // Simulate loading delay
            setTimeout(() => {
                showToast('5 more equipment items loaded', 'info');
                loadingDiv.style.display = 'none';
                btn.style.display = 'inline-block';
            }, 2000);
        });
        
        // Export Button
        document.getElementById('exportBtn')?.addEventListener('click', function() {
            // Show progress feedback
            showToast('Preparing export file...', 'info');
            
            // Simulate processing
            setTimeout(() => {
                // Show success with download prompt (simulated)
                showToast('Export completed! Download will start automatically.', 'success');
                
                // In a real app, trigger file download here
            }, 2000);
        });
        
        // Modal Cancel Button
        document.getElementById('modalCancel')?.addEventListener('click', function() {
            document.getElementById('confirmationModal').style.display = 'none';
            showToast('Action cancelled', 'info');
        });
        
        // Tab Navigation
        document.querySelectorAll('.tab').forEach(tab => {
            tab.addEventListener('click', function() {
                // Remove active class from all tabs
                document.querySelectorAll('.tab').forEach(t => {
                    t.style.borderBottom = 'none';
                    t.style.color = '';
                    t.style.fontWeight = 'normal';
                });
                
                // Add active class to clicked tab
                this.style.borderBottom = '2px solid var(--secondary)';
                this.style.color = 'var(--secondary)';
                this.style.fontWeight = '600';
                
                // In a real app, load content for this tab
                showToast(`Loading ${this.textContent} items...`, 'info');
            });
        });
        
        // Form field focus effects
        document.querySelectorAll('input, select, textarea').forEach(field => {
            field.addEventListener('focus', function() {
                this.parentElement.style.backgroundColor = 'rgba(52, 152, 219, 0.05)';
                this.parentElement.style.padding = '15px';
                this.parentElement.style.borderRadius = '4px';
                this.parentElement.style.transition = 'all 0.3s';
            });
            
            field.addEventListener('blur', function() {
                this.parentElement.style.backgroundColor = '';
                this.parentElement.style.padding = '';
            });
        });
        
        // Initialize with a welcome toast
        window.addEventListener('load', function() {
            setTimeout(() => {
                showToast('Welcome to SJCB Equipment Management System!', 'info');
            }, 500);
        });
        
        // Keyboard navigation support
        document.addEventListener('keydown', function(e) {
            // Enter key submits form when focus is on submit button
            if (e.key === 'Enter' && e.target.type === 'submit') {
                e.target.click();
            }
            
            // Escape key closes modal
            if (e.key === 'Escape' && document.getElementById('confirmationModal').style.display === 'flex') {
                document.getElementById('confirmationModal').style.display = 'none';
            }
        });
    </script>
</body>
</html>

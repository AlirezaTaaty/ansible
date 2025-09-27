<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ansible Ubuntu Baseline Configuration</title>
    <style>
        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --success: #27ae60;
            --warning: #f39c12;
            --danger: #e74c3c;
            --light: #ecf0f1;
            --dark: #34495e;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .header {
            background: white;
            border-radius: 15px;
            padding: 40px;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            text-align: center;
        }
        
        .logo {
            font-size: 3rem;
            margin-bottom: 20px;
        }
        
        h1 {
            color: var(--primary);
            margin-bottom: 15px;
            font-size: 2.5rem;
        }
        
        .subtitle {
            color: var(--dark);
            font-size: 1.2rem;
            margin-bottom: 20px;
        }
        
        .badge {
            display: inline-block;
            background: var(--secondary);
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
            margin: 0 5px;
        }
        
        .content {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 30px;
            margin-bottom: 30px;
        }
        
        .main-content {
            background: white;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }
        
        .sidebar {
            background: white;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }
        
        h2 {
            color: var(--primary);
            margin: 25px 0 15px 0;
            padding-bottom: 10px;
            border-bottom: 2px solid var(--light);
        }
        
        h3 {
            color: var(--secondary);
            margin: 20px 0 10px 0;
        }
        
        .role-card {
            background: var(--light);
            border-left: 4px solid var(--secondary);
            padding: 20px;
            margin: 15px 0;
            border-radius: 8px;
        }
        
        .role-title {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }
        
        .role-name {
            font-weight: bold;
            color: var(--primary);
        }
        
        .role-tag {
            background: var(--success);
            color: white;
            padding: 3px 10px;
            border-radius: 12px;
            font-size: 0.8rem;
        }
        
        .code-block {
            background: #2d2d2d;
            color: #f8f8f2;
            padding: 15px;
            border-radius: 8px;
            margin: 15px 0;
            overflow-x: auto;
            font-family: 'Courier New', monospace;
        }
        
        .command {
            color: #50fa7b;
        }
        
        .comment {
            color: #6272a4;
        }
        
        .btn {
            display: inline-block;
            background: var(--secondary);
            color: white;
            padding: 10px 20px;
            border-radius: 5px;
            text-decoration: none;
            margin: 10px 5px;
            transition: all 0.3s ease;
        }
        
        .btn:hover {
            background: var(--primary);
            transform: translateY(-2px);
        }
        
        .feature-list {
            list-style-type: none;
        }
        
        .feature-list li {
            padding: 8px 0;
            border-bottom: 1px solid #eee;
        }
        
        .feature-list li:before {
            content: "✓";
            color: var(--success);
            margin-right: 10px;
            font-weight: bold;
        }
        
        .footer {
            text-align: center;
            color: white;
            padding: 20px;
            margin-top: 30px;
        }
        
        @media (max-width: 768px) {
            .content {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="logo">⚙️</div>
            <h1>Ansible Ubuntu Baseline Configuration</h1>
            <p class="subtitle">Automated server provisioning and configuration for Ubuntu servers</p>
            <div>
                <span class="badge">Ansible</span>
                <span class="badge">Ubuntu</span>
                <span class="badge">DevOps</span>
                <span class="badge">Automation</span>
            </div>
        </div>
        
        <div class="content">
            <div class="main-content">
                <h2>Overview</h2>
                <p>This Ansible project provides a baseline configuration for Ubuntu servers that I use when first accessing new servers. It automates the essential setup tasks to ensure consistency, security, and proper configuration across all environments.</p>
                
                <h2>Project Structure</h2>
                <div class="code-block">
<pre>ansible-ubuntu-baseline/
├── inventories/
│   ├── production/
│   └── staging/
├── roles/
│   ├── <span class="command">common/</span>          # Basic system configuration
│   ├── <span class="command">docker/</span>         # Docker installation & setup
│   └── <span class="command">nginx/</span>          # Nginx status checking
├── site.yml
├── ansible.cfg
└── README.md</pre>
                </div>
                
                <h2>Roles</h2>
                
                <div class="role-card">
                    <div class="role-title">
                        <span class="role-name">Common</span>
                        <span class="role-tag">Base System</span>
                    </div>
                    <p>Essential baseline configuration for all Ubuntu servers including package updates, user management, and basic security settings.</p>
                    <ul class="feature-list">
                        <li>System package updates and upgrades</li>
                        <li>Essential package installation</li>
                        <li>User account management</li>
                        <li>Timezone and hostname configuration</li>
                        <li>Basic security hardening</li>
                    </ul>
                </div>
                
                <div class="role-card">
                    <div class="role-title">
                        <span class="role-name">Docker</span>
                        <span class="role-tag">Containerization</span>
                    </div>
                    <p>Docker installation and configuration with best practices for Ubuntu servers.</p>
                    <ul class="feature-list">
                        <li>Docker CE installation from official repositories</li>
                        <li>Docker Compose setup</li>
                        <li>User group configuration for Docker access</li>
                        <li>Service configuration and optimization</li>
                    </ul>
                </div>
                
                <div class="role-card">
                    <div class="role-title">
                        <span class="role-name">Nginx</span>
                        <span class="role-tag">Web Server</span>
                    </div>
                    <p>Nginx installation status checking and basic configuration verification.</p>
                    <ul class="feature-list">
                        <li>Nginx installation verification</li>
                        <li>Service status monitoring</li>
                        <li>Configuration validation</li>
                    </ul>
                </div>
                
                <h2>Quick Start</h2>
                <h3>Prerequisites</h3>
                <ul class="feature-list">
                    <li>Ansible installed on your control machine</li>
                    <li>SSH access to target Ubuntu servers</li>
                    <li>Python installed on target servers</li>
                </ul>
                
                <h3>Basic Usage</h3>
                <div class="code-block">
<pre><span class="comment"># Clone the repository</span>
<span class="command">git clone</span> https://github.com/yourusername/ansible-ubuntu-baseline.git
<span class="command">cd</span> ansible-ubuntu-baseline

<span class="comment"># Configure your inventory</span>
<span class="command">cp</span> inventories/production/sample inventories/production/hosts
<span class="comment"># Edit the hosts file with your server details</span>

<span class="comment"># Run the playbook</span>
<span class="command">ansible-playbook</span> -i inventories/production/hosts site.yml</pre>
                </div>
                
                <h3>Running Specific Roles</h3>
                <div class="code-block">
<pre><span class="comment"># Run only the common role</span>
<span class="command">ansible-playbook</span> -i inventories/production/hosts site.yml --tags "common"

<span class="comment"># Run only docker and nginx roles</span>
<span class="command">ansible-playbook</span> -i inventories/production/hosts site.yml --tags "docker,nginx"

<span class="comment"># Dry run to see what would change</span>
<span class="command">ansible-playbook</span> -i inventories/production/hosts site.yml --check --diff</pre>
                </div>
            </div>
            
            <div class="sidebar">
                <h2>Features</h2>
                <ul class="feature-list">
                    <li>Idempotent configuration</li>
                    <li>Environment-specific settings</li>
                    <li>Security best practices</li>
                    <li>Easy to extend and customize</li>
                    <li>Comprehensive documentation</li>
                </ul>
                
                <h2>Requirements</h2>
                <ul class="feature-list">
                    <li>Ansible >= 2.9</li>
                    <li>Ubuntu 18.04, 20.04, or 22.04</li>
                    <li>Python 3.6+</li>
                </ul>
                
                <h2>Links</h2>
                <a href="#" class="btn">View on GitHub</a>
                <a href="#" class="btn">Download ZIP</a>
                <a href="#" class="btn">Issue Tracker</a>
                
                <h2>Contributing</h2>
                <p>Feel free to submit issues, fork the repository, and create pull requests for any improvements.</p>
                
                <h2>License</h2>
                <p>This project is licensed under the MIT License.</p>
            </div>
        </div>
        
        <div class="footer">
            <p>Made with ❤️ for DevOps automation</p>
        </div>
    </div>
</body>
</html>

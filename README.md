# Web-Tools
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="Content-Security-Policy" content="default-src * 'unsafe-inline' 'unsafe-eval'; script-src * 'unsafe-inline' 'unsafe-eval'; connect-src * 'unsafe-inline'; img-src * data: 'unsafe-inline'; frame-src *;">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Free online tools collection including image compression, PDF tools, converters, and more. All tools work directly in your browser.">
    <meta name="keywords" content="online tools, image compressor, PDF tools, converters, calculators, web utilities">
    <meta name="author" content="WebTools Pro">
    <meta property="og:title" content="Free Online Tools Collection - 25+ Useful Web Utilities">
    <meta property="og:description" content="Collection of 25+ free online tools including image compression, PDF tools, converters, and more.">
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://yourwebsite.com/tools">
    <meta name="robots" content="index, follow">
    <link rel="canonical" href="https://yourwebsite.com/tools">
    <title>Free Online Tools Collection - 25+ Useful Web Utilities</title>
    <!-- PDF.js Library for PDF Merger -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/2.10.377/pdf.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/pdf-lib/1.16.0/pdf-lib.min.js"></script>
    <!-- QR Code Generator Library -->
    <script src="https://cdn.jsdelivr.net/npm/qrcode@1.5.1/build/qrcode.min.js"></script>
    <!-- Markdown Editor Library -->
    <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/dompurify@2.3.3/dist/purify.min.js"></script>
    <style>
        :root {
            --primary-color: #4285f4;
            --secondary-color: #34a853;
            --accent-color: #ea4335;
            --light-gray: #f5f5f5;
            --dark-gray: #333;
            --medium-gray: #757575;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            line-height: 1.6;
            color: var(--dark-gray);
            background-color: #f9f9f9;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        header {
            background-color: white;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            padding: 20px 0;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 24px;
            font-weight: bold;
            color: var(--primary-color);
            text-decoration: none;
        }
        
        .logo span {
            color: var(--accent-color);
        }
        
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav ul li {
            margin-left: 20px;
        }
        
        nav ul li a {
            text-decoration: none;
            color: var(--dark-gray);
            font-weight: 500;
            transition: color 0.3s;
        }
        
        nav ul li a:hover {
            color: var(--primary-color);
        }
        
        .hero {
            text-align: center;
            padding: 50px 0;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
        }
        
        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 20px;
            color: var(--dark-gray);
        }
        
        .hero p {
            font-size: 1.2rem;
            color: var(--medium-gray);
            max-width: 700px;
            margin: 0 auto 30px;
        }
        
        .tools-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin: 40px 0;
        }
        
        .tool-card {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            padding: 20px;
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
        }
        
        .tool-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 12px rgba(0,0,0,0.15);
        }
        
        .tool-icon {
            font-size: 36px;
            margin-bottom: 15px;
            color: var(--primary-color);
        }
        
        .tool-card h3 {
            margin-bottom: 10px;
        }
        
        .tool-card p {
            color: var(--medium-gray);
            margin-bottom: 15px;
            font-size: 14px;
        }
        
        .tool-btn {
            display: inline-block;
            background-color: var(--primary-color);
            color: white;
            padding: 8px 16px;
            border-radius: 4px;
            text-decoration: none;
            font-size: 14px;
            transition: background-color 0.3s;
        }
        
        .tool-btn:hover {
            background-color: #3367d6;
        }
        
        .tool-container {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            padding: 30px;
            margin-bottom: 40px;
            display: none;
        }
        
        .active-tool {
            display: block;
            animation: fadeIn 0.3s ease-in-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .upload-area {
            border: 2px dashed var(--medium-gray);
            border-radius: 8px;
            padding: 40px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            margin-bottom: 30px;
        }
        
        .upload-area:hover {
            border-color: var(--primary-color);
            background-color: rgba(66, 133, 244, 0.05);
        }
        
        .upload-area.active {
            border-color: var(--secondary-color);
            background-color: rgba(52, 168, 83, 0.05);
        }
        
        .upload-icon {
            font-size: 48px;
            color: var(--primary-color);
            margin-bottom: 15px;
        }
        
        .controls {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .control-group {
            flex: 1;
            min-width: 200px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--dark-gray);
        }
        
        select, input[type="range"], input[type="text"], input[type="number"], input[type="color"], input[type="date"], input[type="time"], input[type="url"], textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            background-color: white;
        }
        
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            height: 8px;
            background: #ddd;
            border-radius: 4px;
            padding: 0;
        }
        
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 20px;
            height: 20px;
            background: var(--primary-color);
            border-radius: 50%;
            cursor: pointer;
        }
        
        .range-value {
            display: inline-block;
            margin-left: 10px;
            font-weight: bold;
            color: var(--primary-color);
        }
        
        button, .btn {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: background-color 0.3s;
            margin-right: 10px;
            margin-bottom: 10px;
        }
        
        button:hover, .btn:hover {
            background-color: #3367d6;
        }
        
        button:disabled {
            background-color: #cccccc;
            cursor: not-allowed;
        }
        
        .btn-secondary {
            background-color: var(--medium-gray);
        }
        
        .btn-secondary:hover {
            background-color: #5d5d5d;
        }
        
        .btn-success {
            background-color: var(--secondary-color);
        }
        
        .btn-success:hover {
            background-color: #2d9249;
        }
        
        .btn-danger {
            background-color: var(--accent-color);
        }
        
        .btn-danger:hover {
            background-color: #d33426;
        }
        
        .results {
            display: none;
            margin-top: 30px;
        }
        
        .result-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        
        .result-card {
            border: 1px solid #eee;
            border-radius: 8px;
            padding: 20px;
            text-align: center;
        }
        
        .result-image {
            max-width: 100%;
            height: auto;
            border-radius: 4px;
            margin-bottom: 15px;
        }
        
        .result-stats {
            margin-top: 15px;
            font-size: 14px;
        }
        
        .stat {
            display: flex;
            justify-content: space-between;
            margin-bottom: 5px;
        }
        
        .download-btn {
            display: inline-block;
            margin-top: 15px;
            background-color: var(--secondary-color);
        }
        
        .download-btn:hover {
            background-color: #2d9249;
        }
        
        .ad-container {
            margin: 30px 0;
            background-color: var(--light-gray);
            padding: 20px;
            border-radius: 8px;
            text-align: center;
            min-height: 100px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        footer {
            background-color: var(--dark-gray);
            color: white;
            padding: 40px 0;
            text-align: center;
        }
        
        .footer-content {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .footer-links {
            display: flex;
            gap: 20px;
            margin: 20px 0;
        }
        
        .footer-links a {
            color: white;
            text-decoration: none;
        }
        
        .footer-links a:hover {
            text-decoration: underline;
        }
        
        .copyright {
            margin-top: 20px;
            color: #aaa;
            font-size: 14px;
        }
        
        /* Loading spinner */
        .spinner {
            display: none;
            margin: 20px auto;
            width: 50px;
            height: 50px;
            border: 5px solid rgba(66, 133, 244, 0.2);
            border-radius: 50%;
            border-top-color: var(--primary-color);
            animation: spin 1s ease-in-out infinite;
        }
        
        @keyframes spin {
            to { transform: rotate(360deg); }
        }
        
        /* Breadcrumb for SEO */
        .breadcrumb {
            padding: 15px 0;
            font-size: 14px;
            color: var(--medium-gray);
        }
        
        .breadcrumb a {
            color: var(--primary-color);
            text-decoration: none;
        }
        
        /* Tool specific styles */
        .color-preview {
            width: 100px;
            height: 100px;
            border-radius: 8px;
            margin: 10px auto;
            border: 1px solid #ddd;
        }
        
        .qr-code-container {
            text-align: center;
            margin: 20px 0;
        }
        
        #qrCode {
            max-width: 200px;
            margin: 0 auto;
        }
        
        .password-strength {
            height: 5px;
            background-color: #ddd;
            margin-top: 10px;
            border-radius: 3px;
            overflow: hidden;
        }
        
        .strength-meter {
            height: 100%;
            width: 0;
            transition: width 0.3s, background-color 0.3s;
        }
        
        .calculator-display {
            background-color: #f0f0f0;
            padding: 15px;
            text-align: right;
            font-size: 24px;
            margin-bottom: 10px;
            border-radius: 4px;
            min-height: 60px;
        }
        
        .calculator-buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }
        
        .calculator-btn {
            padding: 15px;
            font-size: 18px;
            border: none;
            background-color: #e0e0e0;
            border-radius: 4px;
            cursor: pointer;
        }
        
        .calculator-btn:hover {
            background-color: #d0d0d0;
        }
        
        .calculator-btn.operator {
            background-color: var(--primary-color);
            color: white;
        }
        
        .calculator-btn.operator:hover {
            background-color: #3367d6;
        }
        
        .calculator-btn.equals {
            background-color: var(--secondary-color);
            color: white;
            grid-column: span 2;
        }
        
        .calculator-btn.equals:hover {
            background-color: #2d9249;
        }
        
        /* PDF Merger styles */
        .pdf-list {
            margin: 20px 0;
            border: 1px solid #eee;
            border-radius: 8px;
            padding: 15px;
            max-height: 300px;
            overflow-y: auto;
        }
        
        .pdf-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 8px 0;
            border-bottom: 1px solid #f5f5f5;
        }
        
        .pdf-item:last-child {
            border-bottom: none;
        }
        
        .pdf-item-name {
            flex: 1;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            margin-right: 10px;
        }
        
        /* Markdown Editor styles */
        .markdown-container {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        
        @media (min-width: 768px) {
            .markdown-container {
                flex-direction: row;
            }
            
            .markdown-editor, .markdown-preview {
                flex: 1;
            }
        }
        
        .markdown-editor {
            min-height: 300px;
        }
        
        .markdown-preview {
            border: 1px solid #ddd;
            border-radius: 4px;
            padding: 15px;
            min-height: 300px;
            background-color: white;
        }
        
        /* JSON Formatter styles */
        #jsonInput, #jsonOutput {
            min-height: 200px;
            font-family: monospace;
        }
        
        /* Case Converter styles */
        .case-options {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .case-option {
            padding: 8px 12px;
            background-color: #f0f0f0;
            border-radius: 4px;
            cursor: pointer;
        }
        
        .case-option.active {
            background-color: var(--primary-color);
            color: white;
        }
        
        /* Age Calculator styles */
        .age-result {
            margin-top: 20px;
            padding: 15px;
            background-color: #f5f5f5;
            border-radius: 8px;
        }
        
        /* BMI Calculator styles */
        .bmi-result {
            margin-top: 20px;
            padding: 15px;
            background-color: #f5f5f5;
            border-radius: 8px;
            text-align: center;
        }
        
        .bmi-value {
            font-size: 24px;
            font-weight: bold;
            margin: 10px 0;
        }
        
        .bmi-category {
            padding: 8px;
            border-radius: 4px;
            color: white;
            font-weight: bold;
        }
        
        /* Random Number Generator styles */
        .random-number-result {
            font-size: 24px;
            font-weight: bold;
            text-align: center;
            margin: 20px 0;
            padding: 20px;
            background-color: #f5f5f5;
            border-radius: 8px;
        }
        
        /* New Tools styles */
        /* URL Shortener */
        .shortened-url-container {
            margin-top: 20px;
            padding: 15px;
            background-color: #f5f5f5;
            border-radius: 8px;
        }
        
        .shortened-url {
            word-break: break-all;
            font-weight: bold;
        }
        
        /* Image to Base64 */
        .base64-result {
            margin-top: 20px;
        }
        
        .base64-textarea {
            min-height: 100px;
            font-family: monospace;
        }
        
        /* HTML Escape */
        .html-escape-container {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        
        @media (min-width: 768px) {
            .html-escape-container {
                flex-direction: row;
            }
            
            .html-escape-input, .html-escape-output {
                flex: 1;
            }
        }
        
        /* Time Zone Converter */
        .timezone-result {
            margin-top: 20px;
            padding: 15px;
            background-color: #f5f5f5;
            border-radius: 8px;
            font-size: 18px;
            text-align: center;
        }
        
        /* Newly Added Tools */
        /* YouTube Thumbnail Downloader */
        .thumbnail-preview {
            max-width: 100%;
            margin: 20px 0;
            border-radius: 8px;
        }
        
        .thumbnail-options {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin: 15px 0;
        }
        
        /* Instagram Downloader */
        .instagram-result {
            margin-top: 20px;
        }
        
        /* Facebook Downloader */
        .facebook-result {
            margin-top: 20px;
        }
        
        /* Twitter Downloader */
        .twitter-result {
            margin-top: 20px;
        }
        
        /* TikTok Downloader */
        .tiktok-result {
            margin-top: 20px;
        }
        
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            nav ul {
                margin-top: 20px;
                justify-content: center;
            }
            
            nav ul li {
                margin: 0 10px;
            }
            
            .hero h1 {
                font-size: 2rem;
            }
            
            .controls {
                flex-direction: column;
            }
            
            .upload-area {
                padding: 30px 20px;
            }
            
            .tools-grid {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }
        }
        
        @media (max-width: 480px) {
            .hero {
                padding: 30px 0;
            }
            
            .hero h1 {
                font-size: 1.8rem;
            }
            
            .tool-container {
                padding: 20px 15px;
            }
            
            .result-grid {
                grid-template-columns: 1fr;
            }
            
            .tools-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container header-content">
            <a href="/" class="logo">Web<span>Tools</span></a>
            <nav>
                <ul>
                    <li><a href="/">Home</a></li>
                    <li><a href="#all-tools">All Tools</a></li>
                    <li><a href="#about">About</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <main class="container">
        <div class="breadcrumb">
            <a href="/">Home</a> &raquo; <span>Online Tools</span>
        </div>
        
        <section class="hero">
            <h1>Free Online Tools Collection</h1>
            <p>25+ useful web utilities that work directly in your browser. No installation required, no data uploaded to servers.</p>
        </section>

        <!-- Top Ad Banner -->
        <div class="ad-container">
            <!-- Replace with your Google AdSense code -->
            <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-YOUR_ADSENSE_ID"></script>
            <!-- Tools_Top -->
            <ins class="adsbygoogle"
                 style="display:block"
                 data-ad-client="ca-pub-YOUR_ADSENSE_ID"
                 data-ad-slot="YOUR_AD_SLOT_ID"
                 data-ad-format="auto"
                 data-full-width-responsive="true"></ins>
            <script>
                 (adsbygoogle = window.adsbygoogle || []).push({});
            </script>
        </div>

        <section id="all-tools">
            <h2>All Available Tools</h2>
            <div class="tools-grid">
                <!-- Tool 1: Image Compressor -->
                <div class="tool-card" data-tool="image-compressor">
                    <div class="tool-icon">🖼️</div>
                    <h3>Image Compressor</h3>
                    <p>Reduce image file size without losing quality. Supports JPG, PNG, and WebP formats.</p>
                    <a href="#image-compressor" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 2: PDF Merger -->
                <div class="tool-card" data-tool="pdf-merger">
                    <div class="tool-icon">📄</div>
                    <h3>PDF Merger</h3>
                    <p>Combine multiple PDF files into a single document in your browser.</p>
                    <a href="#pdf-merger" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 3: QR Code Generator -->
                <div class="tool-card" data-tool="qr-generator">
                    <div class="tool-icon">🔲</div>
                    <h3>QR Code Generator</h3>
                    <p>Create custom QR codes for URLs, text, contact info and more.</p>
                    <a href="#qr-generator" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 4: Color Picker -->
                <div class="tool-card" data-tool="color-picker">
                    <div class="tool-icon">🎨</div>
                    <h3>Color Picker</h3>
                    <p>Select colors and get HEX, RGB, HSL values. Create color palettes.</p>
                    <a href="#color-picker" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 5: Password Generator -->
                <div class="tool-card" data-tool="password-generator">
                    <div class="tool-icon">🔒</div>
                    <h3>Password Generator</h3>
                    <p>Create strong, secure passwords with customizable options.</p>
                    <a href="#password-generator" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 6: Text to Speech -->
                <div class="tool-card" data-tool="text-to-speech">
                    <div class="tool-icon">🗣️</div>
                    <h3>Text to Speech</h3>
                    <p>Convert text to natural sounding speech in multiple languages.</p>
                    <a href="#text-to-speech" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 7: Calculator -->
                <div class="tool-card" data-tool="calculator">
                    <div class="tool-icon">🧮</div>
                    <h3>Scientific Calculator</h3>
                    <p>Advanced calculator with scientific functions and history.</p>
                    <a href="#calculator" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 8: Base64 Encoder -->
                <div class="tool-card" data-tool="base64-encoder">
                    <div class="tool-icon">🔢</div>
                    <h3>Base64 Encoder/Decoder</h3>
                    <p>Convert text or files to Base64 and vice versa.</p>
                    <a href="#base64-encoder" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 9: URL Shortener -->
                <div class="tool-card" data-tool="url-shortener">
                    <div class="tool-icon">🔗</div>
                    <h3>URL Shortener</h3>
                    <p>Create short, memorable links from long URLs.</p>
                    <a href="#url-shortener" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 10: Markdown Editor -->
                <div class="tool-card" data-tool="markdown-editor">
                    <div class="tool-icon">✍️</div>
                    <h3>Markdown Editor</h3>
                    <p>Write and preview Markdown in real-time with live rendering.</p>
                    <a href="#markdown-editor" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 11: JSON Formatter -->
                <div class="tool-card" data-tool="json-formatter">
                    <div class="tool-icon">{} </div>
                    <h3>JSON Formatter</h3>
                    <p>Validate, format, and beautify JSON data with syntax highlighting.</p>
                    <a href="#json-formatter" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 12: Currency Converter -->
                <div class="tool-card" data-tool="currency-converter">
                    <div class="tool-icon">💱</div>
                    <h3>Currency Converter</h3>
                    <p>Convert between world currencies with up-to-date exchange rates.</p>
                    <a href="#currency-converter" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 13: Word Counter -->
                <div class="tool-card" data-tool="word-counter">
                    <div class="tool-icon">📝</div>
                    <h3>Word Counter</h3>
                    <p>Count words, characters, sentences and analyze text.</p>
                    <a href="#word-counter" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 14: Age Calculator -->
                <div class="tool-card" data-tool="age-calculator">
                    <div class="tool-icon">🎂</div>
                    <h3>Age Calculator</h3>
                    <p>Calculate age in years, months, days from birth date.</p>
                    <a href="#age-calculator" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 15: BMI Calculator -->
                <div class="tool-card" data-tool="bmi-calculator">
                    <div class="tool-icon">⚖️</div>
                    <h3>BMI Calculator</h3>
                    <p>Calculate Body Mass Index and get health recommendations.</p>
                    <a href="#bmi-calculator" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 16: Lorem Ipsum Generator -->
                <div class="tool-card" data-tool="lorem-ipsum">
                    <div class="tool-icon">✏️</div>
                    <h3>Lorem Ipsum Generator</h3>
                    <p>Generate placeholder text in various formats and lengths.</p>
                    <a href="#lorem-ipsum" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 17: Case Converter -->
                <div class="tool-card" data-tool="case-converter">
                    <div class="tool-icon">🔠</div>
                    <h3>Case Converter</h3>
                    <p>Change text between uppercase, lowercase, title case and more.</p>
                    <a href="#case-converter" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 18: Time Zone Converter -->
                <div class="tool-card" data-tool="timezone-converter">
                    <div class="tool-icon">⏰</div>
                    <h3>Time Zone Converter</h3>
                    <p>Convert times between different time zones worldwide.</p>
                    <a href="#timezone-converter" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 19: Image to Base64 -->
                <div class="tool-card" data-tool="image-to-base64">
                    <div class="tool-icon">🖼️➡️🔢</div>
                    <h3>Image to Base64</h3>
                    <p>Convert images to Base64 data URLs for web development.</p>
                    <a href="#image-to-base64" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 20: HTML Escape -->
                <div class="tool-card" data-tool="html-escape">
                    <div class="tool-icon">&lt;&gt;</div>
                    <h3>HTML Escape</h3>
                    <p>Escape and unescape HTML entities for web content.</p>
                    <a href="#html-escape" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 21: Random Number Generator -->
                <div class="tool-card" data-tool="random-number">
                    <div class="tool-icon">🎲</div>
                    <h3>Random Number Generator</h3>
                    <p>Generate random numbers within a specified range.</p>
                    <a href="#random-number" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 22: YouTube Thumbnail Downloader -->
                <div class="tool-card" data-tool="youtube-thumbnail">
                    <div class="tool-icon">📺</div>
                    <h3>YouTube Thumbnail</h3>
                    <p>Get high-quality thumbnails from YouTube videos.</p>
                    <a href="#youtube-thumbnail" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 23: Instagram Downloader -->
                <div class="tool-card" data-tool="instagram-downloader">
                    <div class="tool-icon">📷</div>
                    <h3>Instagram Downloader</h3>
                    <p>Download images and videos from Instagram posts.</p>
                    <a href="#instagram-downloader" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 24: Facebook Downloader -->
                <div class="tool-card" data-tool="facebook-downloader">
                    <div class="tool-icon">👍</div>
                    <h3>Facebook Downloader</h3>
                    <p>Download videos from Facebook posts.</p>
                    <a href="#facebook-downloader" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 25: Twitter Downloader -->
                <div class="tool-card" data-tool="twitter-downloader">
                    <div class="tool-icon">🐦</div>
                    <h3>Twitter Downloader</h3>
                    <p>Download videos from Twitter tweets.</p>
                    <a href="#twitter-downloader" class="tool-btn">Use Tool</a>
                </div>
                
                <!-- Tool 26: TikTok Downloader -->
                <div class="tool-card" data-tool="tiktok-downloader">
                    <div class="tool-icon">🎵</div>
                    <h3>TikTok Downloader</h3>
                    <p>Download videos from TikTok without watermark.</p>
                    <a href="#tiktok-downloader" class="tool-btn">Use Tool</a>
                </div>
            </div>
        </section>

        <!-- Middle Ad Banner -->
        <div class="ad-container">
            <!-- Replace with your Google AdSense code -->
            <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-YOUR_ADSENSE_ID"></script>
            <!-- Tools_Middle -->
            <ins class="adsbygoogle"
                 style="display:block"
                 data-ad-client="ca-pub-YOUR_ADSENSE_ID"
                 data-ad-slot="YOUR_AD_SLOT_ID"
                 data-ad-format="auto"
                 data-full-width-responsive="true"></ins>
            <script>
                 (adsbygoogle = window.adsbygoogle || []).push({});
            </script>
        </div>

        <!-- Tool Containers -->
        <!-- Image Compressor Tool -->
        <div id="image-compressor" class="tool-container">
            <h2>Image Compressor</h2>
            <div id="uploadArea" class="upload-area">
                <div class="upload-icon">📁</div>
                <h2>Drag & Drop Your Images Here</h2>
                <p>or click to browse files (JPG, PNG, WebP supported)</p>
                <input type="file" id="fileInput" accept="image/jpeg, image/png, image/webp" multiple style="display: none;">
            </div>

            <div class="controls">
                <div class="control-group">
                    <label for="format">Output Format</label>
                    <select id="format">
                        <option value="original">Keep Original</option>
                        <option value="jpeg">JPEG</option>
                        <option value="png">PNG</option>
                        <option value="webp" selected>WebP (Recommended)</option>
                    </select>
                </div>

                <div class="control-group">
                    <label for="quality">Quality: <span id="qualityValue" class="range-value">80</span>%</label>
                    <input type="range" id="quality" min="1" max="100" value="80">
                </div>

                <div class="control-group">
                    <label for="compression">Compression Level: <span id="compressionValue" class="range-value">5</span></label>
                    <input type="range" id="compression" min="1" max="9" value="5">
                </div>
            </div>

            <button id="compressBtn" disabled>Compress Images</button>
            <div id="spinner" class="spinner"></div>

            <div id="results" class="results">
                <h2>Compression Results</h2>
                <div id="resultGrid" class="result-grid"></div>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- PDF Merger Tool -->
        <div id="pdf-merger" class="tool-container">
            <h2>PDF Merger</h2>
            <div id="pdfUploadArea" class="upload-area">
                <div class="upload-icon">📁</div>
                <h2>Drag & Drop PDF Files Here</h2>
                <p>or click to browse files (PDF only)</p>
                <input type="file" id="pdfFileInput" accept=".pdf" multiple style="display: none;">
            </div>

            <div class="controls">
                <div class="control-group">
                    <label for="pdfOutputName">Output Filename</label>
                    <input type="text" id="pdfOutputName" placeholder="merged.pdf" value="merged.pdf">
                </div>
            </div>

            <div id="pdfList" class="pdf-list">
                <p>No PDF files selected yet</p>
            </div>

            <button id="mergePdfBtn" class="btn-success" disabled>Merge PDFs</button>
            <button id="clearPdfBtn" class="btn-danger">Clear All</button>
            <div id="pdfSpinner" class="spinner"></div>

            <div id="pdfResults" class="results">
                <h2>Merged PDF</h2>
                <div id="pdfDownloadContainer" style="text-align: center; margin-top: 20px;">
                    <a id="pdfDownloadBtn" class="download-btn">Download Merged PDF</a>
                </div>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- QR Code Generator Tool -->
        <div id="qr-generator" class="tool-container">
            <h2>QR Code Generator</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="qrText">Text or URL</label>
                    <input type="text" id="qrText" placeholder="Enter text or URL to encode">
                </div>
                <div class="control-group">
                    <label for="qrSize">Size (px): <span id="qrSizeValue" class="range-value">200</span></label>
                    <input type="range" id="qrSize" min="100" max="500" value="200">
                </div>
                <div class="control-group">
                    <label for="qrColor">Color</label>
                    <input type="color" id="qrColor" value="#000000">
                </div>
            </div>
            
            <button id="generateQRBtn">Generate QR Code</button>
            
            <div class="qr-code-container">
                <canvas id="qrCode"></canvas>
            </div>
            
            <button id="downloadQRBtn" class="download-btn" disabled>Download QR Code</button>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Password Generator Tool -->
        <div id="password-generator" class="tool-container">
            <h2>Password Generator</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="pwLength">Length: <span id="pwLengthValue" class="range-value">12</span></label>
                    <input type="range" id="pwLength" min="6" max="32" value="12">
                </div>
                <div class="control-group">
                    <label>
                        <input type="checkbox" id="pwUppercase" checked> Include Uppercase (A-Z)
                    </label>
                </div>
                <div class="control-group">
                    <label>
                        <input type="checkbox" id="pwLowercase" checked> Include Lowercase (a-z)
                    </label>
                </div>
                <div class="control-group">
                    <label>
                        <input type="checkbox" id="pwNumbers" checked> Include Numbers (0-9)
                    </label>
                </div>
                <div class="control-group">
                    <label>
                        <input type="checkbox" id="pwSymbols"> Include Symbols (!@#$%^&*)
                    </label>
                </div>
            </div>
            
            <button id="generatePwBtn">Generate Password</button>
            
            <div class="control-group" style="margin-top: 20px;">
                <label for="generatedPassword">Your Password</label>
                <div style="display: flex; gap: 10px;">
                    <input type="text" id="generatedPassword" readonly style="flex: 1;">
                    <button id="copyPwBtn">Copy</button>
                </div>
                <div class="password-strength">
                    <div id="pwStrengthMeter" class="strength-meter"></div>
                </div>
                <div id="pwStrengthText" style="font-size: 12px; color: var(--medium-gray);"></div>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Color Picker Tool -->
        <div id="color-picker" class="tool-container">
            <h2>Color Picker</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="colorPicker">Select Color</label>
                    <input type="color" id="colorPicker" value="#4285f4">
                </div>
                <div class="color-preview" id="colorPreview" style="background-color: #4285f4;"></div>
                <div class="control-group">
                    <label for="hexValue">HEX</label>
                    <input type="text" id="hexValue" value="#4285f4" readonly>
                </div>
                <div class="control-group">
                    <label for="rgbValue">RGB</label>
                    <input type="text" id="rgbValue" value="rgb(66, 133, 244)" readonly>
                </div>
                <div class="control-group">
                    <label for="hslValue">HSL</label>
                    <input type="text" id="hslValue" value="hsl(217, 90%, 61%)" readonly>
                </div>
            </div>
            
            <button id="copyHexBtn">Copy HEX</button>
            <button id="copyRgbBtn">Copy RGB</button>
            <button id="copyHslBtn">Copy HSL</button>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Calculator Tool -->
        <div id="calculator" class="tool-container">
            <h2>Scientific Calculator</h2>
            <div class="calculator-display" id="calcDisplay">0</div>
            <div class="calculator-buttons">
                <button class="calculator-btn" onclick="calcInput('(')">(</button>
                <button class="calculator-btn" onclick="calcInput(')')">)</button>
                <button class="calculator-btn" onclick="calcInput('%')">%</button>
                <button class="calculator-btn operator" onclick="calcClear()">C</button>
                
                <button class="calculator-btn" onclick="calcInput('7')">7</button>
                <button class="calculator-btn" onclick="calcInput('8')">8</button>
                <button class="calculator-btn" onclick="calcInput('9')">9</button>
                <button class="calculator-btn operator" onclick="calcInput('/')">÷</button>
                
                <button class="calculator-btn" onclick="calcInput('4')">4</button>
                <button class="calculator-btn" onclick="calcInput('5')">5</button>
                <button class="calculator-btn" onclick="calcInput('6')">6</button>
                <button class="calculator-btn operator" onclick="calcInput('*')">×</button>
                
                <button class="calculator-btn" onclick="calcInput('1')">1</button>
                <button class="calculator-btn" onclick="calcInput('2')">2</button>
                <button class="calculator-btn" onclick="calcInput('3')">3</button>
                <button class="calculator-btn operator" onclick="calcInput('-')">−</button>
                
                <button class="calculator-btn" onclick="calcInput('0')">0</button>
                <button class="calculator-btn" onclick="calcInput('.')">.</button>
                <button class="calculator-btn operator" onclick="calcCalculate()">=</button>
                <button class="calculator-btn operator" onclick="calcInput('+')">+</button>
                
                <button class="calculator-btn" onclick="calcInput('Math.sin(')">sin</button>
                <button class="calculator-btn" onclick="calcInput('Math.cos(')">cos</button>
                <button class="calculator-btn" onclick="calcInput('Math.tan(')">tan</button>
                <button class="calculator-btn" onclick="calcInput('Math.sqrt(')">√</button>
                
                <button class="calculator-btn" onclick="calcInput('Math.log(')">log</button>
                <button class="calculator-btn" onclick="calcInput('Math.PI')">π</button>
                <button class="calculator-btn" onclick="calcInput('Math.pow(')">x^y</button>
                <button class="calculator-btn" onclick="calcBackspace()">⌫</button>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Text to Speech Tool -->
        <div id="text-to-speech" class="tool-container">
            <h2>Text to Speech</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="ttsText">Enter Text</label>
                    <textarea id="ttsText" rows="5" placeholder="Type or paste text here to convert to speech"></textarea>
                </div>
                <div class="control-group">
                    <label for="ttsVoice">Voice</label>
                    <select id="ttsVoice">
                        <!-- Options will be populated by JavaScript -->
                    </select>
                </div>
                <div class="control-group">
                    <label for="ttsRate">Rate: <span id="ttsRateValue">1</span></label>
                    <input type="range" id="ttsRate" min="0.5" max="2" step="0.1" value="1">
                </div>
                <div class="control-group">
                    <label for="ttsPitch">Pitch: <span id="ttsPitchValue">1</span></label>
                    <input type="range" id="ttsPitch" min="0.5" max="2" step="0.1" value="1">
                </div>
            </div>
            
            <button id="speakBtn">Speak</button>
            <button id="stopBtn">Stop</button>
            <button id="downloadAudioBtn">Download as Audio</button>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Word Counter Tool -->
        <div id="word-counter" class="tool-container">
            <h2>Word Counter</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="wcText">Enter Text</label>
                    <textarea id="wcText" rows="10" placeholder="Type or paste your text here"></textarea>
                </div>
            </div>
            
            <div class="result-stats">
                <div class="stat">
                    <span>Words:</span>
                    <span id="wordCount">0</span>
                </div>
                <div class="stat">
                    <span>Characters:</span>
                    <span id="charCount">0</span>
                </div>
                <div class="stat">
                    <span>Characters (no spaces):</span>
                    <span id="charNoSpaceCount">0</span>
                </div>
                <div class="stat">
                    <span>Sentences:</span>
                    <span id="sentenceCount">0</span>
                </div>
                <div class="stat">
                    <span>Paragraphs:</span>
                    <span id="paragraphCount">0</span>
                </div>
                <div class="stat">
                    <span>Reading Time:</span>
                    <span id="readingTime">0</span>
                </div>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Markdown Editor Tool -->
        <div id="markdown-editor" class="tool-container">
            <h2>Markdown Editor</h2>
            <div class="markdown-container">
                <div class="markdown-editor">
                    <div class="control-group">
                        <label for="markdownInput">Markdown Input</label>
                        <textarea id="markdownInput" rows="15" placeholder="Type your Markdown here..."></textarea>
                    </div>
                </div>
                <div class="markdown-preview">
                    <label>Live Preview</label>
                    <div id="markdownPreview"></div>
                </div>
            </div>
            
            <button id="clearMarkdownBtn" class="btn-danger">Clear</button>
            <button id="downloadMarkdownBtn" class="download-btn">Download as HTML</button>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- JSON Formatter Tool -->
        <div id="json-formatter" class="tool-container">
            <h2>JSON Formatter</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="jsonInput">JSON Input</label>
                    <textarea id="jsonInput" rows="10" placeholder="Paste your JSON here"></textarea>
                </div>
            </div>
            
            <button id="formatJsonBtn">Format JSON</button>
            <button id="minifyJsonBtn">Minify JSON</button>
            <button id="validateJsonBtn">Validate JSON</button>
            <button id="clearJsonBtn" class="btn-danger">Clear</button>
            
            <div class="control-group" style="margin-top: 20px;">
                <label for="jsonOutput">Result</label>
                <textarea id="jsonOutput" rows="10" readonly></textarea>
            </div>
            
            <button id="copyJsonBtn" class="download-btn">Copy to Clipboard</button>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- URL Shortener Tool -->
        <div id="url-shortener" class="tool-container">
            <h2>URL Shortener</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="urlInput">Long URL</label>
                    <input type="url" id="urlInput" placeholder="Enter the URL you want to shorten">
                </div>
                <div class="control-group">
                    <label for="customAlias">Custom Alias (optional)</label>
                    <input type="text" id="customAlias" placeholder="my-custom-link">
                </div>
            </div>
            
            <button id="shortenUrlBtn">Shorten URL</button>
            <div id="urlSpinner" class="spinner"></div>
            
            <div id="shortenedUrlResult" class="shortened-url-container" style="display: none;">
                <h3>Your Shortened URL</h3>
                <div class="shortened-url" id="shortenedUrl"></div>
                <button id="copyUrlBtn" class="download-btn" style="margin-top: 10px;">Copy URL</button>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Age Calculator Tool -->
        <div id="age-calculator" class="tool-container">
            <h2>Age Calculator</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="birthDate">Date of Birth</label>
                    <input type="date" id="birthDate">
                </div>
                <div class="control-group">
                    <label for="ageAtDate">Age at Date (optional)</label>
                    <input type="date" id="ageAtDate">
                </div>
            </div>
            
            <button id="calculateAgeBtn">Calculate Age</button>
            
            <div id="ageResult" class="age-result" style="display: none;">
                <h3>Age Calculation Result</h3>
                <div class="stat">
                    <span>Years:</span>
                    <span id="ageYears">0</span>
                </div>
                <div class="stat">
                    <span>Months:</span>
                    <span id="ageMonths">0</span>
                </div>
                <div class="stat">
                    <span>Days:</span>
                    <span id="ageDays">0</span>
                </div>
                <div class="stat">
                    <span>Total Days:</span>
                    <span id="ageTotalDays">0</span>
                </div>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- BMI Calculator Tool -->
        <div id="bmi-calculator" class="tool-container">
            <h2>BMI Calculator</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="bmiHeight">Height (cm)</label>
                    <input type="number" id="bmiHeight" placeholder="Enter your height in cm">
                </div>
                <div class="control-group">
                    <label for="bmiWeight">Weight (kg)</label>
                    <input type="number" id="bmiWeight" placeholder="Enter your weight in kg">
                </div>
            </div>
            
            <button id="calculateBmiBtn">Calculate BMI</button>
            
            <div id="bmiResult" class="bmi-result" style="display: none;">
                <h3>Your BMI Result</h3>
                <div class="bmi-value" id="bmiValue">0</div>
                <div class="bmi-category" id="bmiCategory">Underweight</div>
                <p id="bmiDescription">Your BMI suggests you are underweight.</p>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Case Converter Tool -->
        <div id="case-converter" class="tool-container">
            <h2>Case Converter</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="caseInput">Text to Convert</label>
                    <textarea id="caseInput" rows="5" placeholder="Enter text to convert"></textarea>
                </div>
            </div>
            
            <div class="case-options">
                <div class="case-option active" data-case="lower">Lower Case</div>
                <div class="case-option" data-case="upper">UPPER CASE</div>
                <div class="case-option" data-case="title">Title Case</div>
                <div class="case-option" data-case="sentence">Sentence case</div>
                <div class="case-option" data-case="camel">camelCase</div>
                <div class="case-option" data-case="pascal">PascalCase</div>
                <div class="case-option" data-case="snake">snake_case</div>
                <div class="case-option" data-case="kebab">kebab-case</div>
            </div>
            
            <div class="control-group">
                <label for="caseOutput">Converted Text</label>
                <textarea id="caseOutput" rows="5" readonly></textarea>
            </div>
            
            <button id="copyCaseBtn" class="download-btn">Copy to Clipboard</button>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Time Zone Converter Tool -->
        <div id="timezone-converter" class="tool-container">
            <h2>Time Zone Converter</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="tzDate">Date</label>
                    <input type="date" id="tzDate">
                </div>
                <div class="control-group">
                    <label for="tzTime">Time</label>
                    <input type="time" id="tzTime" value="12:00">
                </div>
                <div class="control-group">
                    <label for="tzFrom">From Time Zone</label>
                    <select id="tzFrom">
                        <option value="UTC">UTC</option>
                        <option value="America/New_York">New York (EST/EDT)</option>
                        <option value="America/Chicago">Chicago (CST/CDT)</option>
                        <option value="America/Denver">Denver (MST/MDT)</option>
                        <option value="America/Los_Angeles">Los Angeles (PST/PDT)</option>
                        <option value="Europe/London">London (GMT/BST)</option>
                        <option value="Europe/Paris">Paris (CET/CEST)</option>
                        <option value="Asia/Tokyo">Tokyo (JST)</option>
                        <option value="Asia/Shanghai">Shanghai (CST)</option>
                        <option value="Australia/Sydney">Sydney (AEST/AEDT)</option>
                    </select>
                </div>
                <div class="control-group">
                    <label for="tzTo">To Time Zone</label>
                    <select id="tzTo">
                        <option value="UTC">UTC</option>
                        <option value="America/New_York">New York (EST/EDT)</option>
                        <option value="America/Chicago">Chicago (CST/CDT)</option>
                        <option value="America/Denver">Denver (MST/MDT)</option>
                        <option value="America/Los_Angeles">Los Angeles (PST/PDT)</option>
                        <option value="Europe/London">London (GMT/BST)</option>
                        <option value="Europe/Paris">Paris (CET/CEST)</option>
                        <option value="Asia/Tokyo">Tokyo (JST)</option>
                        <option value="Asia/Shanghai">Shanghai (CST)</option>
                        <option value="Australia/Sydney">Sydney (AEST/AEDT)</option>
                    </select>
                </div>
            </div>
            
            <button id="convertTimezoneBtn">Convert Time</button>
            
            <div id="timezoneResult" class="timezone-result" style="display: none;">
                <div id="convertedTimezone"></div>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Image to Base64 Tool -->
        <div id="image-to-base64" class="tool-container">
            <h2>Image to Base64 Converter</h2>
            <div id="base64UploadArea" class="upload-area">
                <div class="upload-icon">📁</div>
                <h2>Drag & Drop Image Here</h2>
                <p>or click to browse files (JPG, PNG, WebP supported)</p>
                <input type="file" id="base64FileInput" accept="image/jpeg, image/png, image/webp" style="display: none;">
            </div>
            
            <div class="base64-result" style="display: none;">
                <div class="control-group">
                    <label for="base64Output">Base64 Data URL</label>
                    <textarea id="base64Output" class="base64-textarea" readonly></textarea>
                </div>
                <button id="copyBase64Btn" class="download-btn">Copy to Clipboard</button>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- HTML Escape Tool -->
        <div id="html-escape" class="tool-container">
            <h2>HTML Escape/Unescape</h2>
            <div class="html-escape-container">
                <div class="html-escape-input">
                    <div class="control-group">
                        <label for="htmlInput">Input</label>
                        <textarea id="htmlInput" rows="10" placeholder="Enter HTML to escape or escaped HTML to unescape"></textarea>
                    </div>
                </div>
                <div class="html-escape-output">
                    <div class="control-group">
                        <label for="htmlOutput">Output</label>
                        <textarea id="htmlOutput" rows="10" readonly></textarea>
                    </div>
                </div>
            </div>
            
            <button id="escapeHtmlBtn">Escape HTML</button>
            <button id="unescapeHtmlBtn">Unescape HTML</button>
            <button id="copyHtmlBtn" class="download-btn">Copy to Clipboard</button>
            <button id="clearHtmlBtn" class="btn-danger">Clear</button>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Random Number Generator Tool -->
        <div id="random-number" class="tool-container">
            <h2>Random Number Generator</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="randomMin">Minimum Value</label>
                    <input type="number" id="randomMin" value="1">
                </div>
                <div class="control-group">
                    <label for="randomMax">Maximum Value</label>
                    <input type="number" id="randomMax" value="100">
                </div>
                <div class="control-group">
                    <label for="randomCount">How many numbers?</label>
                    <input type="number" id="randomCount" min="1" max="100" value="1">
                </div>
                <div class="control-group">
                    <label>
                        <input type="checkbox" id="randomUnique"> Generate unique numbers
                    </label>
                </div>
            </div>
            
            <button id="generateRandomBtn">Generate Random Numbers</button>
            
            <div id="randomResult" class="random-number-result" style="display: none;">
                <div id="randomNumbers"></div>
            </div>
            
            <button id="copyRandomBtn" class="download-btn" style="display: none;">Copy Numbers</button>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- YouTube Thumbnail Downloader Tool -->
        <div id="youtube-thumbnail" class="tool-container">
            <h2>YouTube Thumbnail Downloader</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="youtubeUrl">YouTube Video URL</label>
                    <input type="url" id="youtubeUrl" placeholder="https://www.youtube.com/watch?v=...">
                </div>
            </div>
            
            <button id="fetchThumbnailBtn">Get Thumbnails</button>
            <div id="thumbnailSpinner" class="spinner"></div>
            
            <div id="thumbnailResult" style="display: none;">
                <h3>Available Thumbnails</h3>
                <div class="thumbnail-options">
                    <button class="btn" data-quality="maxres">Max Resolution</button>
                    <button class="btn" data-quality="hq">High Quality</button>
                    <button class="btn" data-quality="mq">Medium Quality</button>
                    <button class="btn" data-quality="sd">Standard Quality</button>
                </div>
                <img id="thumbnailPreview" class="thumbnail-preview">
                <button id="downloadThumbnailBtn" class="download-btn">Download Thumbnail</button>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Instagram Downloader Tool -->
        <div id="instagram-downloader" class="tool-container">
            <h2>Instagram Downloader</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="instagramUrl">Instagram Post URL</label>
                    <input type="url" id="instagramUrl" placeholder="https://www.instagram.com/p/...">
                </div>
            </div>
            
            <button id="fetchInstagramBtn">Get Media</button>
            <div id="instagramSpinner" class="spinner"></div>
            
            <div id="instagramResult" class="instagram-result" style="display: none;">
                <h3>Download Options</h3>
                <div id="instagramMedia"></div>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Facebook Downloader Tool -->
        <div id="facebook-downloader" class="tool-container">
            <h2>Facebook Downloader</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="facebookUrl">Facebook Video URL</label>
                    <input type="url" id="facebookUrl" placeholder="https://www.facebook.com/.../videos/...">
                </div>
            </div>
            
            <button id="fetchFacebookBtn">Get Video</button>
            <div id="facebookSpinner" class="spinner"></div>
            
            <div id="facebookResult" class="facebook-result" style="display: none;">
                <h3>Download Options</h3>
                <div id="facebookVideo"></div>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Twitter Downloader Tool -->
        <div id="twitter-downloader" class="tool-container">
            <h2>Twitter Downloader</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="twitterUrl">Twitter Tweet URL</label>
                    <input type="url" id="twitterUrl" placeholder="https://twitter.com/.../status/...">
                </div>
            </div>
            
            <button id="fetchTwitterBtn">Get Media</button>
            <div id="twitterSpinner" class="spinner"></div>
            
            <div id="twitterResult" class="twitter-result" style="display: none;">
                <h3>Download Options</h3>
                <div id="twitterMedia"></div>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- TikTok Downloader Tool -->
        <div id="tiktok-downloader" class="tool-container">
            <h2>TikTok Downloader</h2>
            <div class="controls">
                <div class="control-group">
                    <label for="tiktokUrl">TikTok Video URL</label>
                    <input type="url" id="tiktokUrl" placeholder="https://www.tiktok.com/@.../video/...">
                </div>
            </div>
            
            <button id="fetchTiktokBtn">Get Video</button>
            <div id="tiktokSpinner" class="spinner"></div>
            
            <div id="tiktokResult" class="tiktok-result" style="display: none;">
                <h3>Download Options</h3>
                <div id="tiktokVideo"></div>
            </div>
            
            <button class="btn btn-secondary" onclick="showToolSelector()">Back to All Tools</button>
        </div>

        <!-- Bottom Ad Banner -->
        <div class="ad-container">
            <!-- Replace with your Google AdSense code -->
            <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-YOUR_ADSENSE_ID"></script>
            <!-- Tools_Bottom -->
            <ins class="adsbygoogle"
                 style="display:block"
                 data-ad-client="ca-pub-YOUR_ADSENSE_ID"
                 data-ad-slot="YOUR_AD_SLOT_ID"
                 data-ad-format="auto"
                 data-full-width-responsive="true"></ins>
            <script>
                 (adsbygoogle = window.adsbygoogle || []).push({});
            </script>
        </div>
    </main>

    <footer>
        <div class="container footer-content">
            <a href="/" class="logo" style="color: white;">Web<span style="color: #aaa;">Tools</span></a>
            <div class="footer-links">
                <a href="/privacy">Privacy Policy</a>
                <a href="/terms">Terms of Service</a>
                <a href="/faq">FAQ</a>
                <a href="/contact">Contact Us</a>
            </div>
            <div class="copyright">
                &copy; 2023 WebTools. All rights reserved.
            </div>
        </div>
    </footer>

    <script>
        // Global variables
        let currentTool = null;
        const speechSynthesis = window.speechSynthesis;
        
        // Initialize the page
        document.addEventListener('DOMContentLoaded', function() {
            // Set up tool navigation
            setupToolNavigation();
            
            // Initialize all tools
            initImageCompressor();
            initPdfMerger();
            initQRGenerator();
            initPasswordGenerator();
            initColorPicker();
            initCalculator();
            initTextToSpeech();
            initWordCounter();
            initMarkdownEditor();
            initJsonFormatter();
            initUrlShortener();
            initAgeCalculator();
            initBmiCalculator();
            initCaseConverter();
            initTimezoneConverter();
            initImageToBase64();
            initHtmlEscape();
            initRandomNumberGenerator();
            initYoutubeThumbnail();
            initInstagramDownloader();
            initFacebookDownloader();
            initTwitterDownloader();
            initTiktokDownloader();
        });
        
        // Tool navigation functions
        function setupToolNavigation() {
            // Show tool when clicking on tool card or "Use Tool" button
            document.querySelectorAll('.tool-card, .tool-btn').forEach(element => {
                element.addEventListener('click', function(e) {
                    e.preventDefault();
                    const toolId = this.getAttribute('data-tool') || 
                                  this.getAttribute('href').substring(1);
                    showTool(toolId);
                });
            });
            
            // Handle hash changes
            window.addEventListener('hashchange', function() {
                const toolId = window.location.hash.substring(1);
                if (toolId) showTool(toolId);
            });
            
            // Check initial hash
            if (window.location.hash) {
                const toolId = window.location.hash.substring(1);
                showTool(toolId);
            }
        }
        
        function showTool(toolId) {
            // Hide all tool containers
            document.querySelectorAll('.tool-container').forEach(container => {
                container.classList.remove('active-tool');
            });
            
            // Show selected tool
            const toolContainer = document.getElementById(toolId);
            if (toolContainer) {
                toolContainer.classList.add('active-tool');
                currentTool = toolId;
                // Update URL hash
                window.location.hash = toolId;
                // Smooth scroll to the tool
                toolContainer.scrollIntoView({ behavior: 'smooth' });
            } else {
                showToolSelector();
            }
        }
        
        function showToolSelector() {
            // Hide all tool containers
            document.querySelectorAll('.tool-container').forEach(container => {
                container.classList.remove('active-tool');
            });
            
            currentTool = null;
            window.location.hash = '';
            // Smooth scroll to the tools grid
            document.getElementById('all-tools').scrollIntoView({ behavior: 'smooth' });
        }

        // Image Compressor Tool
        function initImageCompressor() {
            const fileInput = document.getElementById('fileInput');
            const uploadArea = document.getElementById('uploadArea');
            const compressBtn = document.getElementById('compressBtn');
            const formatSelect = document.getElementById('format');
            const qualitySlider = document.getElementById('quality');
            const qualityValue = document.getElementById('qualityValue');
            const compressionSlider = document.getElementById('compression');
            const compressionValue = document.getElementById('compressionValue');
            const resultsSection = document.getElementById('results');
            const resultGrid = document.getElementById('resultGrid');
            const spinner = document.getElementById('spinner');
            
            let selectedFiles = [];
            
            // Update quality value display
            qualitySlider.addEventListener('input', function() {
                qualityValue.textContent = this.value;
            });
            
            // Update compression value display
            compressionSlider.addEventListener('input', function() {
                compressionValue.textContent = this.value;
            });
            
            // Handle drag and drop
            uploadArea.addEventListener('dragover', function(e) {
                e.preventDefault();
                this.classList.add('active');
            });
            
            uploadArea.addEventListener('dragleave', function() {
                this.classList.remove('active');
            });
            
            uploadArea.addEventListener('drop', function(e) {
                e.preventDefault();
                this.classList.remove('active');
                
                const files = e.dataTransfer.files;
                handleFiles(files);
            });
            
            // Handle click to browse
            uploadArea.addEventListener('click', function() {
                fileInput.click();
            });
            
            fileInput.addEventListener('change', function() {
                handleFiles(this.files);
            });
            
            // Handle file selection
            function handleFiles(files) {
                if (files.length === 0) return;
                
                selectedFiles = Array.from(files).filter(file => 
                    file.type.match('image/jpeg') || 
                    file.type.match('image/png') ||
                    file.type.match('image/webp')
                );
                
                if (selectedFiles.length > 0) {
                    compressBtn.disabled = false;
                    uploadArea.querySelector('h2').textContent = `${selectedFiles.length} file(s) selected`;
                    uploadArea.querySelector('p').textContent = 'Click "Compress Images" to proceed';
                } else {
                    alert('Please select valid image files (JPEG, PNG, or WebP)');
                }
            }
            
            // Handle compression
            compressBtn.addEventListener('click', function() {
                if (selectedFiles.length === 0) return;
                
                spinner.style.display = 'block';
                resultsSection.style.display = 'none';
                resultGrid.innerHTML = '';
                
                // Process each file
                selectedFiles.forEach(file => {
                    compressImage(file);
                });
            });
            
            function compressImage(file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const img = new Image();
                    img.onload = function() {
                        // Create canvas for image manipulation
                        const canvas = document.createElement('canvas');
                        const ctx = canvas.getContext('2d');
                        
                        // Calculate new dimensions if needed (optional)
                        const maxDimension = 2000;
                        let width = img.width;
                        let height = img.height;
                        
                        if (width > maxDimension || height > maxDimension) {
                            if (width > height) {
                                height *= maxDimension / width;
                                width = maxDimension;
                            } else {
                                width *= maxDimension / height;
                                height = maxDimension;
                            }
                        }
                        
                        canvas.width = width;
                        canvas.height = height;
                        
                        // Draw image to canvas
                        ctx.drawImage(img, 0, 0, width, height);
                        
                        // Get output format
                        let format = formatSelect.value;
                        if (format === 'original') {
                            format = file.type.split('/')[1];
                        }
                        
                        // Get quality (0-1)
                        const quality = qualitySlider.value / 100;
                        
                        // Compress image
                        canvas.toBlob(function(blob) {
                            displayResult(file, blob, format);
                        }, `image/${format}`, quality);
                    };
                    img.src = e.target.result;
                };
                reader.readAsDataURL(file);
            }
            
            function displayResult(originalFile, compressedBlob, format) {
                spinner.style.display = 'none';
                resultsSection.style.display = 'block';
                
                // Calculate savings
                const originalSize = originalFile.size;
                const compressedSize = compressedBlob.size;
                const savings = ((originalSize - compressedSize) / originalSize * 100).toFixed(2);
                
                // Create result card
                const card = document.createElement('div');
                card.className = 'result-card';
                
                // Create image preview
                const imgPreview = document.createElement('img');
                imgPreview.className = 'result-image';
                imgPreview.alt = 'Compressed image preview';
                
                const reader = new FileReader();
                reader.onload = function(e) {
                    imgPreview.src = e.target.result;
                };
                reader.readAsDataURL(compressedBlob);
                
                // Create stats
                const stats = document.createElement('div');
                stats.className = 'result-stats';
                
                stats.innerHTML = `
                    <div class="stat">
                        <span>Original Size:</span>
                        <span>${formatFileSize(originalSize)}</span>
                    </div>
                    <div class="stat">
                        <span>Compressed Size:</span>
                        <span>${formatFileSize(compressedSize)}</span>
                    </div>
                    <div class="stat">
                        <span>Savings:</span>
                        <span>${savings}%</span>
                    </div>
                `;
                
                // Create download button
                const downloadBtn = document.createElement('a');
                downloadBtn.className = 'download-btn button';
                downloadBtn.textContent = 'Download';
                downloadBtn.download = `compressed_${originalFile.name.split('.')[0]}.${format}`;
                downloadBtn.href = URL.createObjectURL(compressedBlob);
                
                // Put it all together
                card.appendChild(imgPreview);
                card.appendChild(stats);
                card.appendChild(downloadBtn);
                
                resultGrid.appendChild(card);
            }
            
            function formatFileSize(bytes) {
                if (bytes < 1024) return bytes + ' bytes';
                else if (bytes < 1048576) return (bytes / 1024).toFixed(2) + ' KB';
                else return (bytes / 1048576).toFixed(2) + ' MB';
            }
        }
        
        // PDF Merger Tool
        function initPdfMerger() {
            const pdfFileInput = document.getElementById('pdfFileInput');
            const pdfUploadArea = document.getElementById('pdfUploadArea');
            const pdfList = document.getElementById('pdfList');
            const mergePdfBtn = document.getElementById('mergePdfBtn');
            const clearPdfBtn = document.getElementById('clearPdfBtn');
            const pdfSpinner = document.getElementById('pdfSpinner');
            const pdfResults = document.getElementById('pdfResults');
            const pdfDownloadBtn = document.getElementById('pdfDownloadBtn');
            const pdfOutputName = document.getElementById('pdfOutputName');
            
            let pdfFiles = [];
            
            // Handle drag and drop
            pdfUploadArea.addEventListener('dragover', function(e) {
                e.preventDefault();
                this.classList.add('active');
            });
            
            pdfUploadArea.addEventListener('dragleave', function() {
                this.classList.remove('active');
            });
            
            pdfUploadArea.addEventListener('drop', function(e) {
                e.preventDefault();
                this.classList.remove('active');
                
                const files = e.dataTransfer.files;
                handlePdfFiles(files);
            });
            
            // Handle click to browse
            pdfUploadArea.addEventListener('click', function() {
                pdfFileInput.click();
            });
            
            pdfFileInput.addEventListener('change', function() {
                handlePdfFiles(this.files);
            });
            
            // Handle file selection
            function handlePdfFiles(files) {
                if (files.length === 0) return;
                
                const newPdfFiles = Array.from(files).filter(file => 
                    file.type === 'application/pdf' || file.name.endsWith('.pdf')
                );
                
                if (newPdfFiles.length > 0) {
                    pdfFiles = [...pdfFiles, ...newPdfFiles];
                    updatePdfList();
                    mergePdfBtn.disabled = pdfFiles.length < 2;
                } else {
                    alert('Please select valid PDF files');
                }
            }
            
            // Update PDF list display
            function updatePdfList() {
                if (pdfFiles.length === 0) {
                    pdfList.innerHTML = '<p>No PDF files selected yet</p>';
                    return;
                }
                
                pdfList.innerHTML = '';
                pdfFiles.forEach((file, index) => {
                    const pdfItem = document.createElement('div');
                    pdfItem.className = 'pdf-item';
                    
                    const pdfName = document.createElement('div');
                    pdfName.className = 'pdf-item-name';
                    pdfName.textContent = file.name;
                    
                    const pdfRemove = document.createElement('button');
                    pdfRemove.textContent = 'Remove';
                    pdfRemove.className = 'btn-danger';
                    pdfRemove.style.padding = '5px 10px';
                    pdfRemove.style.fontSize = '12px';
                    pdfRemove.addEventListener('click', () => {
                        pdfFiles.splice(index, 1);
                        updatePdfList();
                        mergePdfBtn.disabled = pdfFiles.length < 2;
                    });
                    
                    pdfItem.appendChild(pdfName);
                    pdfItem.appendChild(pdfRemove);
                    pdfList.appendChild(pdfItem);
                });
            }
            
            // Clear all PDFs
            clearPdfBtn.addEventListener('click', function() {
                pdfFiles = [];
                updatePdfList();
                mergePdfBtn.disabled = true;
                pdfResults.style.display = 'none';
            });
            
            // Merge PDFs
            mergePdfBtn.addEventListener('click', async function() {
                if (pdfFiles.length < 2) {
                    alert('Please select at least 2 PDF files to merge');
                    return;
                }
                
                pdfSpinner.style.display = 'block';
                pdfResults.style.display = 'none';
                
                try {
                    // Create a new PDF document
                    const { PDFDocument } = PDFLib;
                    const mergedPdf = await PDFDocument.create();
                    
                    // Merge all PDFs
                    for (const file of pdfFiles) {
                        const arrayBuffer = await file.arrayBuffer();
                        const pdfDoc = await PDFDocument.load(arrayBuffer);
                        const pages = await mergedPdf.copyPages(pdfDoc, pdfDoc.getPageIndices());
                        pages.forEach(page => mergedPdf.addPage(page));
                    }
                    
                    // Save the merged PDF
                    const mergedPdfBytes = await mergedPdf.save();
                    const mergedPdfBlob = new Blob([mergedPdfBytes], { type: 'application/pdf' });
                    const mergedPdfUrl = URL.createObjectURL(mergedPdfBlob);
                    
                    // Set download link
                    const outputFilename = pdfOutputName.value.trim() || 'merged.pdf';
                    if (!outputFilename.endsWith('.pdf')) {
                        pdfOutputName.value = outputFilename + '.pdf';
                    }
                    
                    pdfDownloadBtn.href = mergedPdfUrl;
                    pdfDownloadBtn.download = outputFilename.endsWith('.pdf') ? outputFilename : outputFilename + '.pdf';
                    
                    // Show results
                    pdfResults.style.display = 'block';
                } catch (error) {
                    console.error('Error merging PDFs:', error);
                    alert('Error merging PDFs. Please try again with valid PDF files.');
                } finally {
                    pdfSpinner.style.display = 'none';
                }
            });
        }
        
        // QR Code Generator Tool
        function initQRGenerator() {
            const qrText = document.getElementById('qrText');
            const qrSize = document.getElementById('qrSize');
            const qrSizeValue = document.getElementById('qrSizeValue');
            const qrColor = document.getElementById('qrColor');
            const generateQRBtn = document.getElementById('generateQRBtn');
            const downloadQRBtn = document.getElementById('downloadQRBtn');
            const qrCodeCanvas = document.getElementById('qrCode');
            
            // Update size value display
            qrSize.addEventListener('input', function() {
                qrSizeValue.textContent = this.value;
            });
            
            // Generate QR code
            generateQRBtn.addEventListener('click', function() {
                const text = qrText.value.trim();
                const size = parseInt(qrSize.value);
                const color = qrColor.value;
                
                if (!text) {
                    alert('Please enter text or URL to generate QR code');
                    return;
                }
                
                QRCode.toCanvas(qrCodeCanvas, text, {
                    width: size,
                    color: {
                        dark: color,
                        light: '#ffffff'
                    }
                }, function(error) {
                    if (error) {
                        console.error(error);
                        alert('Error generating QR code');
                    } else {
                        downloadQRBtn.disabled = false;
                    }
                });
            });
            
            // Download QR code
            downloadQRBtn.addEventListener('click', function() {
                const link = document.createElement('a');
                link.download = 'qrcode.png';
                link.href = qrCodeCanvas.toDataURL('image/png');
                link.click();
            });
        }
        
        // Password Generator Tool
        function initPasswordGenerator() {
            const pwLength = document.getElementById('pwLength');
            const pwLengthValue = document.getElementById('pwLengthValue');
            const pwUppercase = document.getElementById('pwUppercase');
            const pwLowercase = document.getElementById('pwLowercase');
            const pwNumbers = document.getElementById('pwNumbers');
            const pwSymbols = document.getElementById('pwSymbols');
            const generatePwBtn = document.getElementById('generatePwBtn');
            const generatedPassword = document.getElementById('generatedPassword');
            const copyPwBtn = document.getElementById('copyPwBtn');
            const pwStrengthMeter = document.getElementById('pwStrengthMeter');
            const pwStrengthText = document.getElementById('pwStrengthText');
            
            // Update length value display
            pwLength.addEventListener('input', function() {
                pwLengthValue.textContent = this.value;
            });
            
            // Generate password
            generatePwBtn.addEventListener('click', function() {
                const length = parseInt(pwLength.value);
                const uppercase = pwUppercase.checked;
                const lowercase = pwLowercase.checked;
                const numbers = pwNumbers.checked;
                const symbols = pwSymbols.checked;
                
                if (!uppercase && !lowercase && !numbers && !symbols) {
                    alert('Please select at least one character type');
                    return;
                }
                
                let charset = '';
                if (uppercase) charset += 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
                if (lowercase) charset += 'abcdefghijklmnopqrstuvwxyz';
                if (numbers) charset += '0123456789';
                if (symbols) charset += '!@#$%^&*()_+-=[]{}|;:,.<>?';
                
                let password = '';
                for (let i = 0; i < length; i++) {
                    const randomIndex = Math.floor(Math.random() * charset.length);
                    password += charset[randomIndex];
                }
                
                generatedPassword.value = password;
                checkPasswordStrength(password);
            });
            
            // Copy password
            copyPwBtn.addEventListener('click', function() {
                if (!generatedPassword.value) return;
                
                generatedPassword.select();
                document.execCommand('copy');
                
                // Show copied feedback
                const originalText = copyPwBtn.textContent;
                copyPwBtn.textContent = 'Copied!';
                setTimeout(() => {
                    copyPwBtn.textContent = originalText;
                }, 2000);
            });
            
            // Check password strength
            function checkPasswordStrength(password) {
                let strength = 0;
                
                // Length contributes up to 50% of strength
                strength += Math.min(password.length / 32 * 50, 50);
                
                // Character variety contributes up to 50% of strength
                let varietyScore = 0;
                if (/[A-Z]/.test(password)) varietyScore += 10;
                if (/[a-z]/.test(password)) varietyScore += 10;
                if (/[0-9]/.test(password)) varietyScore += 10;
                if (/[^A-Za-z0-9]/.test(password)) varietyScore += 20;
                
                strength += varietyScore;
                
                // Update meter
                pwStrengthMeter.style.width = `${strength}%`;
                
                // Update color and text
                if (strength < 30) {
                    pwStrengthMeter.style.backgroundColor = '#ff4444';
                    pwStrengthText.textContent = 'Weak';
                } else if (strength < 70) {
                    pwStrengthMeter.style.backgroundColor = '#ffbb33';
                    pwStrengthText.textContent = 'Moderate';
                } else {
                    pwStrengthMeter.style.backgroundColor = '#00C851';
                    pwStrengthText.textContent = 'Strong';
                }
            }
        }
        
        // Color Picker Tool
        function initColorPicker() {
            const colorPicker = document.getElementById('colorPicker');
            const colorPreview = document.getElementById('colorPreview');
            const hexValue = document.getElementById('hexValue');
            const rgbValue = document.getElementById('rgbValue');
            const hslValue = document.getElementById('hslValue');
            const copyHexBtn = document.getElementById('copyHexBtn');
            const copyRgbBtn = document.getElementById('copyRgbBtn');
            const copyHslBtn = document.getElementById('copyHslBtn');
            
            // Update color when picker changes
            colorPicker.addEventListener('input', function() {
                updateColor(this.value);
            });
            
            // Initial color update
            updateColor(colorPicker.value);
            
            // Copy functions
            copyHexBtn.addEventListener('click', function() {
                copyToClipboard(hexValue.value);
                showCopiedFeedback(this);
            });
            
            copyRgbBtn.addEventListener('click', function() {
                copyToClipboard(rgbValue.value);
                showCopiedFeedback(this);
            });
            
            copyHslBtn.addEventListener('click', function() {
                copyToClipboard(hslValue.value);
                showCopiedFeedback(this);
            });
            
            // Update color display
            function updateColor(hex) {
                colorPreview.style.backgroundColor = hex;
                hexValue.value = hex;
                
                // Convert to RGB
                const r = parseInt(hex.substr(1, 2), 16);
                const g = parseInt(hex.substr(3, 2), 16);
                const b = parseInt(hex.substr(5, 2), 16);
                rgbValue.value = `rgb(${r}, ${g}, ${b})`;
                
                // Convert to HSL
                const hsl = rgbToHsl(r, g, b);
                hslValue.value = `hsl(${Math.round(hsl[0])}, ${Math.round(hsl[1])}%, ${Math.round(hsl[2])}%)`;
            }
            
            // RGB to HSL conversion
            function rgbToHsl(r, g, b) {
                r /= 255, g /= 255, b /= 255;
                const max = Math.max(r, g, b), min = Math.min(r, g, b);
                let h, s, l = (max + min) / 2;
            
                if (max === min) {
                    h = s = 0; // achromatic
                } else {
                    const d = max - min;
                    s = l > 0.5 ? d / (2 - max - min) : d / (max + min);
                    switch (max) {
                        case r: h = (g - b) / d + (g < b ? 6 : 0); break;
                        case g: h = (b - r) / d + 2; break;
                        case b: h = (r - g) / d + 4; break;
                    }
                    h /= 6;
                }
            
                return [h * 360, s * 100, l * 100];
            }
            
            // Helper function to copy to clipboard
            function copyToClipboard(text) {
                const textarea = document.createElement('textarea');
                textarea.value = text;
                document.body.appendChild(textarea);
                textarea.select();
                document.execCommand('copy');
                document.body.removeChild(textarea);
            }
            
            // Show copied feedback
            function showCopiedFeedback(button) {
                const originalText = button.textContent;
                button.textContent = 'Copied!';
                setTimeout(() => {
                    button.textContent = originalText;
                }, 2000);
            }
        }
        
        // Calculator Tool
        function initCalculator() {
            const calcDisplay = document.getElementById('calcDisplay');
            let currentInput = '0';
            let previousInput = '';
            let operation = null;
            let resetInput = false;
            
            // Update display
            function updateDisplay() {
                calcDisplay.textContent = currentInput;
            }
            
            // Handle input
            window.calcInput = function(value) {
                if (currentInput === '0' || resetInput) {
                    currentInput = value;
                    resetInput = false;
                } else {
                    currentInput += value;
                }
                updateDisplay();
            };
            
            // Handle clear
            window.calcClear = function() {
                currentInput = '0';
                previousInput = '';
                operation = null;
                updateDisplay();
            };
            
            // Handle backspace
            window.calcBackspace = function() {
                if (currentInput.length === 1) {
                    currentInput = '0';
                } else {
                    currentInput = currentInput.slice(0, -1);
                }
                updateDisplay();
            };
            
            // Handle calculation
            window.calcCalculate = function() {
                let result;
                try {
                    // Replace × with *, ÷ with / for eval
                    const expression = currentInput.replace(/×/g, '*').replace(/÷/g, '/');
                    result = eval(expression);
                } catch (e) {
                    result = 'Error';
                }
                
                currentInput = result.toString();
                updateDisplay();
                resetInput = true;
            };
            
            // Initialize display
            updateDisplay();
        }
        
        // Text to Speech Tool
        function initTextToSpeech() {
            const ttsText = document.getElementById('ttsText');
            const ttsVoice = document.getElementById('ttsVoice');
            const ttsRate = document.getElementById('ttsRate');
            const ttsRateValue = document.getElementById('ttsRateValue');
            const ttsPitch = document.getElementById('ttsPitch');
            const ttsPitchValue = document.getElementById('ttsPitchValue');
            const speakBtn = document.getElementById('speakBtn');
            const stopBtn = document.getElementById('stopBtn');
            const downloadAudioBtn = document.getElementById('downloadAudioBtn');
            
            let voices = [];
            
            // Update rate and pitch values
            ttsRate.addEventListener('input', function() {
                ttsRateValue.textContent = this.value;
            });
            
            ttsPitch.addEventListener('input', function() {
                ttsPitchValue.textContent = this.value;
            });
            
            // Load available voices
            function loadVoices() {
                voices = speechSynthesis.getVoices();
                ttsVoice.innerHTML = '';
                
                voices.forEach(voice => {
                    const option = document.createElement('option');
                    option.textContent = `${voice.name} (${voice.lang})`;
                    option.setAttribute('data-name', voice.name);
                    ttsVoice.appendChild(option);
                });
            }
            
            // Load voices when they become available
            speechSynthesis.onvoiceschanged = loadVoices;
            loadVoices();
            
            // Speak function
            speakBtn.addEventListener('click', function() {
                if (ttsText.value.trim() === '') {
                    alert('Please enter text to speak');
                    return;
                }
                
                // Stop any current speech
                speechSynthesis.cancel();
                
                const utterance = new SpeechSynthesisUtterance(ttsText.value);
                
                // Set voice
                const selectedVoice = voices.find(voice => 
                    voice.name === ttsVoice.selectedOptions[0].getAttribute('data-name')
                );
                if (selectedVoice) utterance.voice = selectedVoice;
                
                // Set rate and pitch
                utterance.rate = parseFloat(ttsRate.value);
                utterance.pitch = parseFloat(ttsPitch.value);
                
                // Speak
                speechSynthesis.speak(utterance);
            });
            
            // Stop function
            stopBtn.addEventListener('click', function() {
                speechSynthesis.cancel();
            });
            
            // Download as audio (note: this is a simplified approach)
            downloadAudioBtn.addEventListener('click', function() {
                alert('Note: Due to browser limitations, this would typically require a server-side component to generate actual audio files. In a production environment, you would need to implement a server-side solution for this feature.');
            });
        }
        
        // Word Counter Tool
        function initWordCounter() {
            const wcText = document.getElementById('wcText');
            const wordCount = document.getElementById('wordCount');
            const charCount = document.getElementById('charCount');
            const charNoSpaceCount = document.getElementById('charNoSpaceCount');
            const sentenceCount = document.getElementById('sentenceCount');
            const paragraphCount = document.getElementById('paragraphCount');
            const readingTime = document.getElementById('readingTime');
            
            // Count when text changes
            wcText.addEventListener('input', updateCounts);
            
            // Initial count
            updateCounts();
            
            function updateCounts() {
                const text = wcText.value;
                
                // Word count (simplified)
                const words = text.trim() === '' ? 0 : text.trim().split(/\s+/).length;
                wordCount.textContent = words;
                
                // Character counts
                charCount.textContent = text.length;
                charNoSpaceCount.textContent = text.replace(/\s+/g, '').length;
                
                // Sentence count (simplified)
                const sentences = text.trim() === '' ? 0 : text.split(/[.!?]+/).filter(s => s.trim().length > 0).length;
                sentenceCount.textContent = sentences;
                
                // Paragraph count
                const paragraphs = text.trim() === '' ? 0 : text.split(/\n+/).filter(p => p.trim().length > 0).length;
                paragraphCount.textContent = paragraphs;
                
                // Reading time (average 200 words per minute)
                const minutes = Math.ceil(words / 200);
                readingTime.textContent = `${minutes} min read`;
            }
        }
        
        // Markdown Editor Tool
        function initMarkdownEditor() {
            const markdownInput = document.getElementById('markdownInput');
            const markdownPreview = document.getElementById('markdownPreview');
            const clearMarkdownBtn = document.getElementById('clearMarkdownBtn');
            const downloadMarkdownBtn = document.getElementById('downloadMarkdownBtn');
            
            // Update preview when input changes
            markdownInput.addEventListener('input', function() {
                updateMarkdownPreview();
            });
            
            // Clear editor
            clearMarkdownBtn.addEventListener('click', function() {
                markdownInput.value = '';
                markdownPreview.innerHTML = '';
            });
            
            // Download as HTML
            downloadMarkdownBtn.addEventListener('click', function() {
                if (!markdownInput.value.trim()) {
                    alert('Please enter some Markdown content first');
                    return;
                }
                
                const htmlContent = `
                    <!DOCTYPE html>
                    <html>
                    <head>
                        <meta charset="UTF-8">
                        <title>Markdown Export</title>
                        <style>
                            body { font-family: Arial, sans-serif; line-height: 1.6; max-width: 800px; margin: 0 auto; padding: 20px; }
                            h1, h2, h3 { color: #333; }
                            pre { background: #f5f5f5; padding: 10px; border-radius: 5px; overflow-x: auto; }
                            code { font-family: monospace; }
                            blockquote { border-left: 3px solid #ddd; padding-left: 15px; color: #666; }
                        </style>
                    </head>
                    <body>
                        ${marked.parse(markdownInput.value)}
                    </body>
                    </html>
                `;
                
                const blob = new Blob([htmlContent], { type: 'text/html' });
                const url = URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url;
                a.download = 'markdown-export.html';
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                URL.revokeObjectURL(url);
            });
            
            // Update markdown preview
            function updateMarkdownPreview() {
                const markdown = markdownInput.value;
                // Sanitize the HTML output to prevent XSS
                markdownPreview.innerHTML = DOMPurify.sanitize(marked.parse(markdown));
            }
            
            // Initial preview update
            updateMarkdownPreview();
        }
        
        // JSON Formatter Tool
        function initJsonFormatter() {
            const jsonInput = document.getElementById('jsonInput');
            const jsonOutput = document.getElementById('jsonOutput');
            const formatJsonBtn = document.getElementById('formatJsonBtn');
            const minifyJsonBtn = document.getElementById('minifyJsonBtn');
            const validateJsonBtn = document.getElementById('validateJsonBtn');
            const clearJsonBtn = document.getElementById('clearJsonBtn');
            const copyJsonBtn = document.getElementById('copyJsonBtn');
            
            // Format JSON
            formatJsonBtn.addEventListener('click', function() {
                try {
                    const jsonObj = JSON.parse(jsonInput.value);
                    jsonOutput.value = JSON.stringify(jsonObj, null, 4);
                } catch (e) {
                    jsonOutput.value = `Error: ${e.message}`;
                }
            });
            
            // Minify JSON
            minifyJsonBtn.addEventListener('click', function() {
                try {
                    const jsonObj = JSON.parse(jsonInput.value);
                    jsonOutput.value = JSON.stringify(jsonObj);
                } catch (e) {
                    jsonOutput.value = `Error: ${e.message}`;
                }
            });
            
            // Validate JSON
            validateJsonBtn.addEventListener('click', function() {
                try {
                    JSON.parse(jsonInput.value);
                    jsonOutput.value = 'Valid JSON';
                } catch (e) {
                    jsonOutput.value = `Invalid JSON: ${e.message}`;
                }
            });
            
            // Clear JSON
            clearJsonBtn.addEventListener('click', function() {
                jsonInput.value = '';
                jsonOutput.value = '';
            });
            
            // Copy JSON
            copyJsonBtn.addEventListener('click', function() {
                if (!jsonOutput.value) {
                    alert('No JSON to copy');
                    return;
                }
                
                jsonOutput.select();
                document.execCommand('copy');
                
                // Show copied feedback
                const originalText = copyJsonBtn.textContent;
                copyJsonBtn.textContent = 'Copied!';
                setTimeout(() => {
                    copyJsonBtn.textContent = originalText;
                }, 2000);
            });
        }
        
        // URL Shortener Tool
        function initUrlShortener() {
            const urlInput = document.getElementById('urlInput');
            const customAlias = document.getElementById('customAlias');
            const shortenUrlBtn = document.getElementById('shortenUrlBtn');
            const urlSpinner = document.getElementById('urlSpinner');
            const shortenedUrlResult = document.getElementById('shortenedUrlResult');
            const shortenedUrl = document.getElementById('shortenedUrl');
            const copyUrlBtn = document.getElementById('copyUrlBtn');
            
            // Shorten URL
            shortenUrlBtn.addEventListener('click', function() {
                const longUrl = urlInput.value.trim();
                const alias = customAlias.value.trim();
                
                if (!longUrl) {
                    alert('Please enter a URL to shorten');
                    return;
                }
                
                // In a real implementation, this would call a URL shortening service API
                // For this demo, we'll just create a fake shortened URL
                urlSpinner.style.display = 'block';
                shortenedUrlResult.style.display = 'none';
                
                setTimeout(() => {
                    const domain = 'https://short.url/';
                    const shortCode = alias || Math.random().toString(36).substring(2, 8);
                    const shortUrl = domain + shortCode;
                    
                    shortenedUrl.textContent = shortUrl;
                    shortenedUrl.href = shortUrl;
                    
                    // Set up copy button
                    copyUrlBtn.onclick = function() {
                        copyToClipboard(shortUrl);
                        const originalText = copyUrlBtn.textContent;
                        copyUrlBtn.textContent = 'Copied!';
                        setTimeout(() => {
                            copyUrlBtn.textContent = originalText;
                        }, 2000);
                    };
                    
                    shortenedUrlResult.style.display = 'block';
                    urlSpinner.style.display = 'none';
                }, 1000);
            });
            
            // Helper function to copy to clipboard
            function copyToClipboard(text) {
                const textarea = document.createElement('textarea');
                textarea.value = text;
                document.body.appendChild(textarea);
                textarea.select();
                document.execCommand('copy');
                document.body.removeChild(textarea);
            }
        }
        
        // Age Calculator Tool
        function initAgeCalculator() {
            const birthDate = document.getElementById('birthDate');
            const ageAtDate = document.getElementById('ageAtDate');
            const calculateAgeBtn = document.getElementById('calculateAgeBtn');
            const ageResult = document.getElementById('ageResult');
            const ageYears = document.getElementById('ageYears');
            const ageMonths = document.getElementById('ageMonths');
            const ageDays = document.getElementById('ageDays');
            const ageTotalDays = document.getElementById('ageTotalDays');
            
            // Set default dates
            const today = new Date();
            birthDate.valueAsDate = new Date(today.getFullYear() - 30, today.getMonth(), today.getDate());
            ageAtDate.valueAsDate = today;
            
            // Calculate age
            calculateAgeBtn.addEventListener('click', function() {
                const birthDateValue = new Date(birthDate.value);
                const ageAtDateValue = ageAtDate.value ? new Date(ageAtDate.value) : new Date();
                
                if (birthDateValue > ageAtDateValue) {
                    alert('Birth date cannot be after the age at date');
                    return;
                }
                
                // Calculate age
                let years = ageAtDateValue.getFullYear() - birthDateValue.getFullYear();
                let months = ageAtDateValue.getMonth() - birthDateValue.getMonth();
                let days = ageAtDateValue.getDate() - birthDateValue.getDate();
                
                if (days < 0) {
                    months--;
                    // Get days in previous month
                    const prevMonthLastDay = new Date(
                        ageAtDateValue.getFullYear(),
                        ageAtDateValue.getMonth(),
                        0
                    ).getDate();
                    days += prevMonthLastDay;
                }
                
                if (months < 0) {
                    years--;
                    months += 12;
                }
                
                // Calculate total days
                const diffTime = Math.abs(ageAtDateValue - birthDateValue);
                const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
                
                // Display results
                ageYears.textContent = years;
                ageMonths.textContent = months;
                ageDays.textContent = days;
                ageTotalDays.textContent = diffDays;
                
                ageResult.style.display = 'block';
            });
        }
        
        // BMI Calculator Tool
        function initBmiCalculator() {
            const bmiHeight = document.getElementById('bmiHeight');
            const bmiWeight = document.getElementById('bmiWeight');
            const calculateBmiBtn = document.getElementById('calculateBmiBtn');
            const bmiResult = document.getElementById('bmiResult');
            const bmiValue = document.getElementById('bmiValue');
            const bmiCategory = document.getElementById('bmiCategory');
            const bmiDescription = document.getElementById('bmiDescription');
            
            // Calculate BMI
            calculateBmiBtn.addEventListener('click', function() {
                const height = parseFloat(bmiHeight.value);
                const weight = parseFloat(bmiWeight.value);
                
                if (isNaN(height)) {
                    alert('Please enter a valid height');
                    return;
                }
                
                if (isNaN(weight)) {
                    alert('Please enter a valid weight');
                    return;
                }
                
                if (height <= 0 || weight <= 0) {
                    alert('Height and weight must be positive numbers');
                    return;
                }
                
                // Calculate BMI (weight in kg / (height in m)^2)
                const heightInMeters = height / 100;
                const bmi = weight / (heightInMeters * heightInMeters);
                const roundedBmi = Math.round(bmi * 10) / 10;
                
                // Determine category
                let category, description, color;
                if (bmi < 18.5) {
                    category = 'Underweight';
                    description = 'Your BMI suggests you are underweight. Consider consulting a healthcare provider.';
                    color = '#ff4444';
                } else if (bmi < 25) {
                    category = 'Normal weight';
                    description = 'Your BMI suggests you have a healthy weight. Keep it up!';
                    color = '#00C851';
                } else if (bmi < 30) {
                    category = 'Overweight';
                    description = 'Your BMI suggests you are overweight. Consider healthier eating and more exercise.';
                    color = '#ffbb33';
                } else {
                    category = 'Obese';
                    description = 'Your BMI suggests you are obese. Please consult a healthcare provider.';
                    color = '#ff4444';
                }
                
                // Display results
                bmiValue.textContent = roundedBmi;
                bmiCategory.textContent = category;
                bmiDescription.textContent = description;
                bmiCategory.style.backgroundColor = color;
                
                bmiResult.style.display = 'block';
            });
        }
        
        // Case Converter Tool
        function initCaseConverter() {
            const caseInput = document.getElementById('caseInput');
            const caseOutput = document.getElementById('caseOutput');
            const caseOptions = document.querySelectorAll('.case-option');
            const copyCaseBtn = document.getElementById('copyCaseBtn');
            
            let currentCase = 'lower';
            
            // Set up case option buttons
            caseOptions.forEach(option => {
                option.addEventListener('click', function() {
                    // Remove active class from all options
                    caseOptions.forEach(opt => opt.classList.remove('active'));
                    // Add active class to clicked option
                    this.classList.add('active');
                    // Set current case
                    currentCase = this.getAttribute('data-case');
                    // Convert text
                    convertCase();
                });
            });
            
            // Convert text when input changes
            caseInput.addEventListener('input', convertCase);
            
            // Copy converted text
            copyCaseBtn.addEventListener('click', function() {
                if (!caseOutput.value) {
                    alert('No text to copy');
                    return;
                }
                
                caseOutput.select();
                document.execCommand('copy');
                
                // Show copied feedback
                const originalText = copyCaseBtn.textContent;
                copyCaseBtn.textContent = 'Copied!';
                setTimeout(() => {
                    copyCaseBtn.textContent = originalText;
                }, 2000);
            });
            
            // Convert text based on selected case
            function convertCase() {
                const text = caseInput.value;
                let convertedText = '';
                
                switch (currentCase) {
                    case 'lower':
                        convertedText = text.toLowerCase();
                        break;
                    case 'upper':
                        convertedText = text.toUpperCase();
                        break;
                    case 'title':
                        convertedText = text.toLowerCase().replace(/\b\w/g, char => char.toUpperCase());
                        break;
                    case 'sentence':
                        convertedText = text.toLowerCase().replace(/(^\s*\w|[.!?]\s*\w)/g, char => char.toUpperCase());
                        break;
                    case 'camel':
                        convertedText = text.toLowerCase()
                            .replace(/[^a-zA-Z0-9]+(.)/g, (_, char) => char.toUpperCase())
                            .replace(/^./, firstChar => firstChar.toLowerCase());
                        break;
                    case 'pascal':
                        convertedText = text.toLowerCase()
                            .replace(/[^a-zA-Z0-9]+(.)/g, (_, char) => char.toUpperCase())
                            .replace(/^./, firstChar => firstChar.toUpperCase());
                        break;
                    case 'snake':
                        convertedText = text.toLowerCase()
                            .replace(/\s+/g, '_')
                            .replace(/[^a-z0-9_]/g, '');
                        break;
                    case 'kebab':
                        convertedText = text.toLowerCase()
                            .replace(/\s+/g, '-')
                            .replace(/[^a-z0-9-]/g, '');
                        break;
                    default:
                        convertedText = text;
                }
                
                caseOutput.value = convertedText;
            }
            
            // Initial conversion
            convertCase();
        }
        
        // Time Zone Converter Tool
        function initTimezoneConverter() {
            const tzDate = document.getElementById('tzDate');
            const tzTime = document.getElementById('tzTime');
            const tzFrom = document.getElementById('tzFrom');
            const tzTo = document.getElementById('tzTo');
            const convertTimezoneBtn = document.getElementById('convertTimezoneBtn');
            const timezoneResult = document.getElementById('timezoneResult');
            const convertedTimezone = document.getElementById('convertedTimezone');
            
            // Set default date to today
            tzDate.valueAsDate = new Date();
            
            // Convert timezone
            convertTimezoneBtn.addEventListener('click', function() {
                const dateStr = tzDate.value;
                const timeStr = tzTime.value;
                const fromZone = tzFrom.value;
                const toZone = tzTo.value;
                
                if (!dateStr || !timeStr) {
                    alert('Please select both date and time');
                    return;
                }
                
                // Create date string in format expected by toLocaleString
                const dateTimeStr = `${dateStr}T${timeStr}`;
                const date = new Date(dateTimeStr);
                
                if (isNaN(date.getTime())) {
                    alert('Invalid date/time combination');
                    return;
                }
                
                // Format options
                const options = {
                    timeZone: toZone,
                    year: 'numeric',
                    month: 'long',
                    day: 'numeric',
                    weekday: 'long',
                    hour: '2-digit',
                    minute: '2-digit',
                    second: '2-digit',
                    timeZoneName: 'short'
                };
                
                // Convert timezone
                const convertedTime = date.toLocaleString('en-US', options);
                
                // Display result
                convertedTimezone.textContent = convertedTime;
                timezoneResult.style.display = 'block';
            });
        }
        
        // Image to Base64 Tool
        function initImageToBase64() {
            const base64UploadArea = document.getElementById('base64UploadArea');
            const base64FileInput = document.getElementById('base64FileInput');
            const base64Result = document.querySelector('.base64-result');
            const base64Output = document.getElementById('base64Output');
            const copyBase64Btn = document.getElementById('copyBase64Btn');
            
            // Handle drag and drop
            base64UploadArea.addEventListener('dragover', function(e) {
                e.preventDefault();
                this.classList.add('active');
            });
            
            base64UploadArea.addEventListener('dragleave', function() {
                this.classList.remove('active');
            });
            
            base64UploadArea.addEventListener('drop', function(e) {
                e.preventDefault();
                this.classList.remove('active');
                
                const files = e.dataTransfer.files;
                if (files.length > 0) {
                    handleImageFile(files[0]);
                }
            });
            
            // Handle click to browse
            base64UploadArea.addEventListener('click', function() {
                base64FileInput.click();
            });
            
            base64FileInput.addEventListener('change', function() {
                if (this.files.length > 0) {
                    handleImageFile(this.files[0]);
                }
            });
            
            // Copy Base64 to clipboard
            copyBase64Btn.addEventListener('click', function() {
                if (!base64Output.value) {
                    alert('No Base64 data to copy');
                    return;
                }
                
                base64Output.select();
                document.execCommand('copy');
                
                // Show copied feedback
                const originalText = copyBase64Btn.textContent;
                copyBase64Btn.textContent = 'Copied!';
                setTimeout(() => {
                    copyBase64Btn.textContent = originalText;
                }, 2000);
            });
            
            // Handle image file
            function handleImageFile(file) {
                if (!file.type.match('image/jpeg') && !file.type.match('image/png') && !file.type.match('image/webp')) {
                    alert('Please select a valid image file (JPEG, PNG, or WebP)');
                    return;
                }
                
                const reader = new FileReader();
                reader.onload = function(e) {
                    base64Output.value = e.target.result;
                    base64Result.style.display = 'block';
                };
                reader.readAsDataURL(file);
            }
        }
        
        // HTML Escape Tool
        function initHtmlEscape() {
            const htmlInput = document.getElementById('htmlInput');
            const htmlOutput = document.getElementById('htmlOutput');
            const escapeHtmlBtn = document.getElementById('escapeHtmlBtn');
            const unescapeHtmlBtn = document.getElementById('unescapeHtmlBtn');
            const copyHtmlBtn = document.getElementById('copyHtmlBtn');
            const clearHtmlBtn = document.getElementById('clearHtmlBtn');
            
            // Escape HTML
            escapeHtmlBtn.addEventListener('click', function() {
                const text = htmlInput.value;
                htmlOutput.value = escapeHtml(text);
            });
            
            // Unescape HTML
            unescapeHtmlBtn.addEventListener('click', function() {
                const text = htmlInput.value;
                htmlOutput.value = unescapeHtml(text);
            });
            
            // Copy HTML
            copyHtmlBtn.addEventListener('click', function() {
                if (!htmlOutput.value) {
                    alert('No HTML to copy');
                    return;
                }
                
                htmlOutput.select();
                document.execCommand('copy');
                
                // Show copied feedback
                const originalText = copyHtmlBtn.textContent;
                copyHtmlBtn.textContent = 'Copied!';
                setTimeout(() => {
                    copyHtmlBtn.textContent = originalText;
                }, 2000);
            });
            
            // Clear HTML
            clearHtmlBtn.addEventListener('click', function() {
                htmlInput.value = '';
                htmlOutput.value = '';
            });
            
            // Escape HTML entities
            function escapeHtml(text) {
                const div = document.createElement('div');
                div.textContent = text;
                return div.innerHTML;
            }
            
            // Unescape HTML entities
            function unescapeHtml(text) {
                const div = document.createElement('div');
                div.innerHTML = text;
                return div.textContent;
            }
        }
        
        // Random Number Generator Tool
        function initRandomNumberGenerator() {
            const randomMin = document.getElementById('randomMin');
            const randomMax = document.getElementById('randomMax');
            const randomCount = document.getElementById('randomCount');
            const randomUnique = document.getElementById('randomUnique');
            const generateRandomBtn = document.getElementById('generateRandomBtn');
            const randomResult = document.getElementById('randomResult');
            const randomNumbers = document.getElementById('randomNumbers');
            const copyRandomBtn = document.getElementById('copyRandomBtn');
            
            // Generate random numbers
            generateRandomBtn.addEventListener('click', function() {
                const min = parseInt(randomMin.value) || 0;
                const max = parseInt(randomMax.value) || 100;
                const count = parseInt(randomCount.value) || 1;
                const unique = randomUnique.checked;
                
                if (min > max) {
                    alert('Minimum value must be less than or equal to maximum value');
                    return;
                }
                
                if (count < 1) {
                    alert('Count must be at least 1');
                    return;
                }
                
                if (unique && (max - min + 1) < count) {
                    alert('Range is too small to generate unique numbers');
                    return;
                }
                
                let numbers = [];
                
                if (unique) {
                    // Generate unique numbers
                    const range = max - min + 1;
                    const allNumbers = Array.from({ length: range }, (_, i) => min + i);
                    
                    // Shuffle array and take first 'count' elements
                    for (let i = allNumbers.length - 1; i > 0; i--) {
                        const j = Math.floor(Math.random() * (i + 1));
                        [allNumbers[i], allNumbers[j]] = [allNumbers[j], allNumbers[i]];
                    }
                    
                    numbers = allNumbers.slice(0, count);
                } else {
                    // Generate numbers (may contain duplicates)
                    for (let i = 0; i < count; i++) {
                        numbers.push(Math.floor(Math.random() * (max - min + 1)) + min);
                    }
                }
                
                // Display results
                randomNumbers.textContent = numbers.join(', ');
                randomResult.style.display = 'block';
                copyRandomBtn.style.display = 'inline-block';
            });
            
            // Copy random numbers
            copyRandomBtn.addEventListener('click', function() {
                if (!randomNumbers.textContent) {
                    alert('No numbers to copy');
                    return;
                }
                
                const textarea = document.createElement('textarea');
                textarea.value = randomNumbers.textContent;
                document.body.appendChild(textarea);
                textarea.select();
                document.execCommand('copy');
                document.body.removeChild(textarea);
                
                // Show copied feedback
                const originalText = copyRandomBtn.textContent;
                copyRandomBtn.textContent = 'Copied!';
                setTimeout(() => {
                    copyRandomBtn.textContent = originalText;
                }, 2000);
            });
        }
        
        // YouTube Thumbnail Downloader Tool
        function initYoutubeThumbnail() {
            const youtubeUrl = document.getElementById('youtubeUrl');
            const fetchThumbnailBtn = document.getElementById('fetchThumbnailBtn');
            const thumbnailSpinner = document.getElementById('thumbnailSpinner');
            const thumbnailResult = document.getElementById('thumbnailResult');
            const thumbnailPreview = document.getElementById('thumbnailPreview');
            const downloadThumbnailBtn = document.getElementById('downloadThumbnailBtn');
            const thumbnailOptions = document.querySelectorAll('.thumbnail-options .btn');
            
            let currentVideoId = '';
            let currentQuality = 'maxres';
            
            // Fetch thumbnail
            fetchThumbnailBtn.addEventListener('click', function() {
                const url = youtubeUrl.value.trim();
                const videoId = extractYouTubeId(url);
                
                if (!videoId) {
                    alert('Please enter a valid YouTube URL');
                    return;
                }
                
                currentVideoId = videoId;
                thumbnailSpinner.style.display = 'block';
                thumbnailResult.style.display = 'none';
                
                // Simulate API call with setTimeout
                setTimeout(() => {
                    updateThumbnail(currentQuality);
                    thumbnailResult.style.display = 'block';
                    thumbnailSpinner.style.display = 'none';
                }, 500);
            });
            
            // Handle thumbnail quality selection
            thumbnailOptions.forEach(option => {
                option.addEventListener('click', function() {
                    currentQuality = this.getAttribute('data-quality');
                    updateThumbnail(currentQuality);
                });
            });
            
            // Download thumbnail
            downloadThumbnailBtn.addEventListener('click', function() {
                if (!currentVideoId) {
                    alert('No thumbnail to download');
                    return;
                }
                
                const link = document.createElement('a');
                link.href = getThumbnailUrl(currentVideoId, currentQuality);
                link.download = `youtube-thumbnail-${currentVideoId}-${currentQuality}.jpg`;
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);
            });
            
            // Update thumbnail preview
            function updateThumbnail(quality) {
                const thumbnailUrl = getThumbnailUrl(currentVideoId, quality);
                thumbnailPreview.src = thumbnailUrl;
            }
            
            // Get thumbnail URL based on quality
            function getThumbnailUrl(videoId, quality) {
                switch (quality) {
                    case 'maxres':
                        return `https://img.youtube.com/vi/${videoId}/maxresdefault.jpg`;
                    case 'hq':
                        return `https://img.youtube.com/vi/${videoId}/hqdefault.jpg`;
                    case 'mq':
                        return `https://img.youtube.com/vi/${videoId}/mqdefault.jpg`;
                    case 'sd':
                        return `https://img.youtube.com/vi/${videoId}/sddefault.jpg`;
                    default:
                        return `https://img.youtube.com/vi/${videoId}/default.jpg`;
                }
            }
            
            // Extract YouTube video ID from URL
            function extractYouTubeId(url) {
                const regExp = /^.*(youtu.be\/|v\/|u\/\w\/|embed\/|watch\?v=|&v=)([^#&?]*).*/;
                const match = url.match(regExp);
                return (match && match[2].length === 11) ? match[2] : null;
            }
        }
        
        // Instagram Downloader Tool
        function initInstagramDownloader() {
            const instagramUrl = document.getElementById('instagramUrl');
            const fetchInstagramBtn = document.getElementById('fetchInstagramBtn');
            const instagramSpinner = document.getElementById('instagramSpinner');
            const instagramResult = document.getElementById('instagramResult');
            const instagramMedia = document.getElementById('instagramMedia');
            
            // Fetch Instagram media
            fetchInstagramBtn.addEventListener('click', function() {
                const url = instagramUrl.value.trim();
                
                if (!url.includes('instagram.com/p/') && !url.includes('instagram.com/reel/')) {
                    alert('Please enter a valid Instagram post or reel URL');
                    return;
                }
                
                instagramSpinner.style.display = 'block';
                instagramResult.style.display = 'none';
                
                // Simulate API call with setTimeout
                setTimeout(() => {
                    // In a real implementation, this would fetch the actual media
                    // For demo purposes, we'll show a placeholder
                    instagramMedia.innerHTML = `
                        <div style="text-align: center; margin: 20px 0;">
                            <p>In a real implementation, this would display the Instagram media.</p>
                            <p>For demo purposes, we're showing a placeholder.</p>
                            <button class="download-btn">Download Image</button>
                            <button class="download-btn">Download Video</button>
                        </div>
                    `;
                    
                    instagramResult.style.display = 'block';
                    instagramSpinner.style.display = 'none';
                }, 1000);
            });
        }
        
        // Facebook Downloader Tool
        function initFacebookDownloader() {
            const facebookUrl = document.getElementById('facebookUrl');
            const fetchFacebookBtn = document.getElementById('fetchFacebookBtn');
            const facebookSpinner = document.getElementById('facebookSpinner');
            const facebookResult = document.getElementById('facebookResult');
            const facebookVideo = document.getElementById('facebookVideo');
            
            // Fetch Facebook video
            fetchFacebookBtn.addEventListener('click', function() {
                const url = facebookUrl.value.trim();
                
                if (!url.includes('facebook.com/') || !url.includes('/videos/')) {
                    alert('Please enter a valid Facebook video URL');
                    return;
                }
                
                facebookSpinner.style.display = 'block';
                facebookResult.style.display = 'none';
                
                // Simulate API call with setTimeout
                setTimeout(() => {
                    // In a real implementation, this would fetch the actual video
                    // For demo purposes, we'll show a placeholder
                    facebookVideo.innerHTML = `
                        <div style="text-align: center; margin: 20px 0;">
                            <p>In a real implementation, this would display the Facebook video.</p>
                            <p>For demo purposes, we're showing a placeholder.</p>
                            <button class="download-btn">Download Video (HD)</button>
                            <button class="download-btn">Download Video (SD)</button>
                        </div>
                    `;
                    
                    facebookResult.style.display = 'block';
                    facebookSpinner.style.display = 'none';
                }, 1000);
            });
        }
        
        // Twitter Downloader Tool
        function initTwitterDownloader() {
            const twitterUrl = document.getElementById('twitterUrl');
            const fetchTwitterBtn = document.getElementById('fetchTwitterBtn');
            const twitterSpinner = document.getElementById('twitterSpinner');
            const twitterResult = document.getElementById('twitterResult');
            const twitterMedia = document.getElementById('twitterMedia');
            
            // Fetch Twitter media
            fetchTwitterBtn.addEventListener('click', function() {
                const url = twitterUrl.value.trim();
                
                if (!url.includes('twitter.com/') || !url.includes('/status/')) {
                    alert('Please enter a valid Twitter tweet URL');
                    return;
                }
                
                twitterSpinner.style.display = 'block';
                twitterResult.style.display = 'none';
                
                // Simulate API call with setTimeout
                setTimeout(() => {
                    // In a real implementation, this would fetch the actual media
                    // For demo purposes, we'll show a placeholder
                    twitterMedia.innerHTML = `
                        <div style="text-align: center; margin: 20px 0;">
                            <p>In a real implementation, this would display the Twitter media.</p>
                            <p>For demo purposes, we're showing a placeholder.</p>
                            <button class="download-btn">Download Image</button>
                            <button class="download-btn">Download Video</button>
                        </div>
                    `;
                    
                    twitterResult.style.display = 'block';
                    twitterSpinner.style.display = 'none';
                }, 1000);
            });
        }
        
        // TikTok Downloader Tool
        function initTiktokDownloader() {
            const tiktokUrl = document.getElementById('tiktokUrl');
            const fetchTiktokBtn = document.getElementById('fetchTiktokBtn');
            const tiktokSpinner = document.getElementById('tiktokSpinner');
            const tiktokResult = document.getElementById('tiktokResult');
            const tiktokVideo = document.getElementById('tiktokVideo');
            
            // Fetch TikTok video
            fetchTiktokBtn.addEventListener('click', function() {
                const url = tiktokUrl.value.trim();
                
                if (!url.includes('tiktok.com/') || !url.includes('/video/')) {
                    alert('Please enter a valid TikTok video URL');
                    return;
                }
                
                tiktokSpinner.style.display = 'block';
                tiktokResult.style.display = 'none';
                
                // Simulate API call with setTimeout
                setTimeout(() => {
                    // In a real implementation, this would fetch the actual video
                    // For demo purposes, we'll show a placeholder
                    tiktokVideo.innerHTML = `
                        <div style="text-align: center; margin: 20px 0;">
                            <p>In a real implementation, this would display the TikTok video.</p>
                            <p>For demo purposes, we're showing a placeholder.</p>
                            <button class="download-btn">Download Video (No Watermark)</button>
                            <button class="download-btn">Download Video (With Watermark)</button>
                        </div>
                    `;
                    
                    tiktokResult.style.display = 'block';
                    tiktokSpinner.style.display = 'none';
                }, 1000);
            });
        }
    </script>
    
    <!-- Schema.org markup for SEO -->
    <script type="application/ld+json">
    {
      "@context": "https://schema.org",
      "@type": "WebApplication",
      "name": "Free Online Tools Collection",
      "url": "https://yourwebsite.com/tools",
      "description": "Collection of 25+ free online tools including image compression, PDF tools, converters, and more.",
      "applicationCategory": "UtilitiesApplication",
      "operatingSystem": "Any",
      "offers": {
        "@type": "Offer",
        "price": "0",
        "priceCurrency": "USD"
      }
    }
    </script>
</body>
</html>

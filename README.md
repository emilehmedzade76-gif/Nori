# Nori<!DOCTYPE html>
<html lang="az">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nori AI - Ağıllı Köpəkçiniz</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <style>
        :root {
            --bg-color: #0f172a;
            --panel-bg: #1e293b;
            --chat-bg: #0f172a;
            --accent-green: #22c55e;
            --accent-green-hover: #16a34a;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --border-color: #334155;
            --user-msg-bg: #2563eb;
            --nori-msg-bg: #1e293b;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
        }

        /* Əsas App Konteyner */
        .app-container {
            width: 100%;
            max-width: 900px;
            height: 100vh;
            display: flex;
            flex-direction: column;
            background-color: var(--bg-color);
            border-left: 1px solid var(--border-color);
            border-right: 1px solid var(--border-color);
        }

        /* Başlıq Hissəsi */
        header {
            background-color: rgba(30, 41, 59, 0.8);
            backdrop-filter: blur(12px);
            padding: 16px 24px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-bottom: 1px solid var(--border-color);
            z-index: 10;
        }

        .brand {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-container {
            width: 44px;
            height: 44px;
            background: linear-gradient(135deg, #15803d, #22c55e);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 22px;
            box-shadow: 0 4px 12px rgba(34, 197, 94, 0.25);
        }

        .app-title h1 {
            font-size: 18px;
            color: var(--text-main);
            font-weight: 700;
            letter-spacing: -0.3px;
        }

        .status-badge {
            display: flex;
            align-items: center;
            gap: 6px;
            font-size: 12px;
            color: var(--accent-green);
            font-weight: 500;
        }

        .status-dot {
            width: 8px;
            height: 8px;
            background-color: var(--accent-green);
            border-radius: 50%;
            box-shadow: 0 0 8px var(--accent-green);
        }

        /* Çat Sahəsi */
        #chat-container {
            flex: 1;
            padding: 24px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 20px;
            scroll-behavior: smooth;
        }

        .message-wrapper {
            display: flex;
            gap: 12px;
            max-width: 80%;
            animation: fadeIn 0.3s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .message-wrapper.user {
            align-self: flex-end;
            flex-direction: row-reverse;
        }

        .message-wrapper.nori {
            align-self: flex-start;
        }

        .avatar {
            width: 36px;
            height: 36px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 16px;
            flex-shrink: 0;
        }

        .user .avatar {
            background-color: var(--user-msg-bg);
            color: white;
        }

        .nori .avatar {
            background-color: #166534;
            color: white;
        }

        .message-content {
            padding: 14px 18px;
            border-radius: 16px;
            line-height: 1.6;
            font-size: 15px;
            word-break: break-word;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        .user .message-content {
            background-color: var(--user-msg-bg);
            color: #ffffff;

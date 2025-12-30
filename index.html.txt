import os

# --- 設定 ---
SITE_TITLE = "マスクフェチ・ログ"
SUB_TITLE = "FANZA厳選！マスク美人作品カタログ"
AFFILIATE_ID = "your-id-999" # 自分のIDが決まったら書き換えてにょ

def generate_site():
    # 本番ではAPIから取得するけど、まずは見た目を確認するための「マスク美人」ダミーデータだにょ
    sample_products = [
        {"title": "【マスク美人】透明感あふれる素顔とのギャップ", "url": "https://www.dmm.co.jp/digital/videoa/", "tag": "FANZAビデオ", "price": "1,980円〜"},
        {"title": "密着！マスク女子のプライベート・ショット", "url": "https://www.dmm.co.jp/digital/videoa/", "tag": "独占配信", "price": "550円〜"},
        {"title": "マスクフェチのための特選写真集 Vol.1", "url": "https://www.dmm.co.jp/digital/videoa/", "tag": "電子書籍", "price": "880円"}
    ]
    
    items_html = ""
    for p in sample_products:
        items_html += f"""
        <article class="card">
            <div class="card-img-area">
                <div class="badge">{p['tag']}</div>
                <div style="color:#64748b; font-size:0.8rem;">[サンプル画像]</div>
            </div>
            <div class="card-body">
                <h2 class="title">{p['title']}</h2>
                <div class="price-row">
                    <span class="price">{p['price']}</span>
                </div>
                <a href="{p['url']}" target="_blank" class="buy-btn">作品詳細を見る</a>
                <p class="ad-notice">※本ページはプロモーションが含まれています</p>
            </div>
        </article>
        """

    full_html = f"""
    <!DOCTYPE html>
    <html lang="ja">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>{SITE_TITLE} | {SUB_TITLE}</title>
        <style>
            @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;700&display=swap');
            :root {{ --bg: #0b0f19; --card: #161e2d; --accent: #f43f5e; --text: #f8fafc; }}
            body {{ font-family: 'Noto Sans JP', sans-serif; background: var(--bg); color: var(--text); margin: 0; line-height: 1.6; }}
            
            /* 規約対策：18禁警告バー */
            .age-warning {{ background: #ff0000; color: white; text-align: center; padding: 5px; font-size: 0.8rem; font-weight: bold; }}

            header {{ padding: 60px 20px; text-align: center; background: radial-gradient(circle at top, #1e293b 0%, #0b0f19 100%); }}
            header h1 {{ font-size: 2.8rem; margin: 0; color: var(--accent); text-shadow: 0 0 20px rgba(244,63,94,0.3); }}
            header p {{ color: #94a3b8; margin-top: 10px; font-weight: bold; }}

            .container {{ max-width: 1200px; margin: -30px auto 60px; padding: 0 20px; }}
            .grid {{ display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 30px; }}
            
            .card {{ background: var(--card); border-radius: 20px; overflow: hidden; border: 1px solid rgba(255,255,255,0.05); transition: 0.3s; }}
            .card:hover {{ transform: translateY(-10px); border-color: var(--accent); box-shadow: 0 10px 30px rgba(0,0,0,0.5); }}
            
            .card-img-area {{ height: 200px; background: #1e293b; display: flex; align-items: center; justify-content: center; position: relative; }}
            .badge {{ position: absolute; top: 15px; left: 15px; background: var(--accent); color: white; padding: 4px 12px; border-radius: 50px; font-size: 0.7rem; font-weight: bold; }}
            
            .card-body {{ padding: 25px; }}
            .title {{ font-size: 1.1rem; margin: 0 0 15px 0; height: 3.2em; overflow: hidden; color: #e2e8f0; }}
            .price {{ color: var(--accent); font-size: 1.2rem; font-weight: bold; }}
            
            .buy-btn {{ display: block; background: var(--accent); color: white; text-align: center; padding: 12px; text-decoration: none; border-radius: 12px; font-weight: bold; margin-top: 20px; transition: 0.2s; }}
            .buy-btn:hover {{ opacity: 0.8; transform: scale(0.98); }}
            
            .ad-notice {{ font-size: 0.65rem; color: #64748b; text-align: center; margin-top: 15px; }}
            
            footer {{ text-align: center; padding: 80px 20px; color: #475569; border-top: 1px solid #1e293b; }}
            .disclaimer {{ font-size: 0.75rem; max-width: 600px; margin: 0 auto; line-height: 1.8; }}
        </style>
    </head>
    <body>
        <div class="age-warning">【18禁】本サイトはアダルトコンテンツを含みます。18歳未満の方の閲覧は固くお断りいたします。</div>
        <header>
            <h1>{SITE_TITLE}</h1>
            <p>{SUB_TITLE}</p>
        </header>
        <main class="container">
            <div class="grid">{items_html}</div>
        </main>
        <footer>
            <div class="disclaimer">
                <p>&copy; 2025 {SITE_TITLE} | マスクフェチ作品専門カタログ</p>
                <p>当サイトはFANZAアフィリエイトプログラムに参加しており、適切な作品紹介を行っています。作品の購入・視聴に関する規約はFANZA公式サイトに準拠します。18歳未満の方はご利用いただけません。</p>
            </div>
        </footer>
    </body>
    </html>
    """
    
    with open("index.html", "w", encoding="utf-8") as f:
        f.write(full_html)
    print("🎭 マスクフェチ特化型の index.html が完成したにょ！")

if __name__ == "__main__":
    generate_site()
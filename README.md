# Template Mail Roundcube

Repositori ini menyediakan template lengkap untuk setup mail server dengan Roundcube sebagai webmail client.

## 📋 Deskripsi

Template ini menggabungkan beberapa komponen untuk menciptakan sistem mail yang terintegrasi:
- **DNS Server** - Konfigurasi zone forward dan reverse
- **Postfix** - Mail Transfer Agent (MTA) untuk SMTP
- **Dovecot** - IMAP/POP3 server untuk mail retrieval
- **Roundcube** - Webmail client berbasis web
- **Apache2** - Web server untuk Roundcube

## 🏗️ Struktur Folder

```
Template-Mail-Roundcube/
├── Roundcube-v1.yml              # Docker compose untuk Roundcube v1
├── Roundcube-v2.yml              # Docker compose untuk Roundcube v2
├── dns/                          # Konfigurasi DNS
│   ├── forward                   # Forward zone configuration
│   ├── reverse                   # Reverse zone configuration
│   ├── named.conf.default-zones  # Named default zones
│   └── named.conf.options        # Named options
├── mail/                         # Konfigurasi mail server
│   ├── dovecot/                  # Dovecot IMAP/POP3 configuration
│   │   ├── 10-auth.conf          # Authentication settings
│   │   └── 10-mail.conf          # Mail configuration
│   ├── postfix/                  # Postfix SMTP configuration
│   │   └── main.cf               # Main postfix configuration
│   └── roundcube/                # Roundcube webmail configuration
│       ├── apache2.conf          # Apache virtual host config
│       ├── config.inc.php        # Roundcube main configuration
│       └── mail.conf             # Additional mail settings
└── README.md                     # Dokumentasi ini
```

## 🔧 Komponen Utama

### DNS Configuration
- **Forward Zone** - Menerjemahkan domain name ke IP address
- **Reverse Zone** - Menerjemahkan IP address ke domain name
- Penting untuk validasi email dan preventing spam

### Postfix (SMTP Server)
- Menangani pengiriman email keluar
- Konfigurasi TLS untuk keamanan
- Queue management dan delivery

### Dovecot (IMAP/POP3 Server)
- Menyediakan akses mail untuk client
- Autentikasi user
- Penyimpanan dan manajemen mail

### Roundcube (Webmail)
- Interface web untuk membaca dan mengirim email
- Berbasis PHP
- Kompatibel dengan IMAP/POP3

## ✅ Prerequisites

- Docker & Docker Compose (jika menggunakan docker setup)
- VPS/Server dengan akses root
- Domain name dengan DNS pointing ke server
- Minimal 2GB RAM, 20GB storage

## 📚 Tutorial & Dokumentasi Lengkap

Untuk panduan instalasi dan konfigurasi yang lengkap, silahkan akses dokumentasi modul di link berikut:

📖 **[Dokumentasi Lengkap dan Tutorial](https://drive.google.com/file/d/143OIiVA2yQY_HcM98f9JbOkikNgnViSF/view?usp=drive_link)**

## 🚀 Quick Start

### 1. Clone Repository
```bash
git clone <repository-url>
cd Template-Mail-Roundcube
```

### 2. Konfigurasi DNS
- Edit file `dns/forward` dengan domain dan IP Anda
- Edit file `dns/reverse` untuk reverse zone

### 3. Konfigurasi Mail Server
- Ubah konfigurasi di `mail/postfix/main.cf`
- Sesuaikan `mail/dovecot/10-mail.conf` untuk storage path
- Konfigurasi `mail/roundcube/config.inc.php`

### 4. Setup Apache & Roundcube
- Gunakan `mail/roundcube/apache2.conf` sebagai virtual host
- Copy `mail/roundcube/config.inc.php` ke direktori Roundcube

### 5. Deploy dengan Docker (Opsional)
```bash
# Gunakan docker-compose
docker-compose -f Roundcube-v1.yml up -d
# atau
docker-compose -f Roundcube-v2.yml up -d
```

## 📝 File Konfigurasi

### DNS Files
- `dns/forward` - Zone file untuk forward lookup
- `dns/reverse` - Zone file untuk reverse lookup
- `dns/named.conf.default-zones` - Default zone definitions
- `dns/named.conf.options` - Global options untuk BIND

### Postfix Configuration
- `mail/postfix/main.cf` - Konfigurasi utama Postfix

### Dovecot Configuration
- `mail/dovecot/10-auth.conf` - Mekanisme autentikasi
- `mail/dovecot/10-mail.conf` - Lokasi dan format mailbox

### Roundcube Configuration
- `mail/roundcube/config.inc.php` - Setting koneksi ke IMAP/SMTP
- `mail/roundcube/apache2.conf` - Virtual host Apache
- `mail/roundcube/mail.conf` - Additional mail settings

## 🔒 Security Considerations

- Selalu gunakan SSL/TLS untuk koneksi mail
- Implementasikan SPF, DKIM, dan DMARC records
- Update system packages secara berkala
- Monitor logs untuk aktivitas mencurigakan
- Backup data mail secara regular

## 📞 Support & Dokumentasi

Untuk informasi lebih detail tentang:
- Instalasi langkah demi langkah
- Troubleshooting
- Best practices
- Advanced configuration

Silahkan merujuk ke dokumentasi lengkap di link yang disediakan.

## 📄 Lisensi

Template ini disediakan sesuai dengan lisensi yang berlaku. Silahkan merujuk pada dokumentasi modul untuk detail lisensi.

---

**Last Updated**: May 2026

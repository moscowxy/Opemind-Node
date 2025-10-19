# Opemind-Node
# OpenMind OM1 Node Kurulum Rehberi

OpenMind OM1 node’u kurarak yapay zeka ağına katkıda bulunun ve ödüller kazanın.

## 📋 Sistem Gereksinimleri

|Bileşen        |Minimum Gereksinim|
|---------------|------------------|
|Disk           |100 GB+ NVME/SSD  |
|İnternet Hızı  |500 Mbps+         |
|İşletim Sistemi|Ubuntu 24.04++    |

##  Kurulum Adımları

### 1. Sistem Güncellemeleri ve Gerekli Paketlerin Kurulumu

```bash
sudo apt update -y && sudo apt upgrade -y

sudo apt install htop ca-certificates zlib1g-dev libncurses5-dev libgdbm-dev \
libnss3-dev tmux iptables curl nvme-cli git wget make jq libleveldb-dev \
build-essential pkg-config ncdu tar clang bsdmainutils lsb-release libssl-dev \
libreadline-dev libffi-dev jq gcc screen file unzip lz4 -y

sudo apt install portaudio19-dev python3-dev ffmpeg -y
```

### 2. UV Paket Yöneticisinin Kurulumu

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
source ~/.bashrc
```

**Versiyonu kontrol edin:**

```bash
uv --version
```

### 3. OpenMind Deposunu İndirme

```bash
git clone https://github.com/openmind/OM1.git
cd OM1
git submodule update --init
```

### 4. Python Sanal Ortamının Oluşturulması

```bash
uv venv
source .venv/bin/activate
```

## API Key Alma

1. **OpenMind Portal’a gidin:** <https://portal.openmind.org/>
1. **Bakiye Yükleme:**
- “Purchase Credits” bölümünden USDC ile bakiye yükleyin
- Minimum 5 USDC
- Sadece crypto ödeme (USDC) kabul edilir
- Base ağı
1. **API Key Oluşturma:**
- “Create API Key” butonuna tıklayın
- Verilen API key’i kaydedin (tek sefer gösterilir!)

## Yapılandırma

### 1. Ortam Değişkenlerini Ayarlama

```bash
cp env.example .env
nano .env
```

### 2. API Key’i Girme

`.env` dosyasında aşağıdaki satırı bulun ve API key’inizi girin:

```bash
OM_API_KEY=buraya_api_keyinizi_yapisitirin
```

Dosyayı kaydetmek için: `CTRL + X`, ardından `Y`, sonra `ENTER`

### 3. Bağımlılıkları Yükleme

```bash
uv sync
```

##  Node’u Çalıştırma

### Screen Oturumu Oluşturma (Önerilen)

```bash
screen -S OM1
```

### Sanal Ortamı Aktifleştirme

```bash
source .venv/bin/activate
```

### Node’u Başlatma

```bash
uv run src/run.py spot
```

### Screen’den Çıkma

Node çalışırken screen’den çıkmak için: `CTRL + A`, ardından `D`

### Screen’e Geri Dönme

```bash
screen -r OM1
```

##  İzleme ve Kontrol

Node çalıştıktan sonra:

- Portal üzerinden node durumunuzu kontrol edebilirsiniz
- Kazanç istatistiklerinizi görüntüleyebilirsiniz
- API kullanımınızı takip edebilirsiniz

##  Sorun Giderme

### Yaygın Hatalar

**API Key Hatası:**

```bash
# .env dosyasını kontrol edin
cat .env | grep OM_API_KEY
```

**Bağımlılık Hatası:**

```bash
# Tekrar yükleyin
uv sync --force
```

**Python Ortam Hatası:**

```bash
# Sanal ortamı yeniden oluşturun
rm -rf .venv
uv venv
source .venv/bin/activate
```

## Notlar

- Node’u 7/24 çalışır durumda tutun
- Sunucu kesintilerine karşı dikkatli olun
- API bakiyenizi düzenli kontrol edin
- Güvenlik güncellemelerini takip edin

## Faydalı Linkler

- **OpenMind Portal:** <https://portal.openmind.org/>
- **Resmi GitHub:** <https://github.com/openmind/OM1>
- **Dokümantasyon:** OpenMind resmi websitesini kontrol edin

## Uyarılar

- API key’inizi asla paylaşmayın
- `.env` dosyanızı asla GitHub’a yüklemeyin
- Düzenli yedekleme yapın
- Güvenlik önlemlerinizi güncel tutun

## Lisans

Bu proje OpenMind tarafından sağlanmaktadır. Lütfen resmi lisans koşullarını kontrol edin.

-----

**Sorularınız için:** OpenMind Discord kanalına katılın veya resmi destek kanallarını kullanın.

**İyi çalışmalar! **

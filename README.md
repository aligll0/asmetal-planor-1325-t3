# As Metal PLANOR 1325 T3 · Safety 4.0 Güvenlik ve Emniyet Analizi

**Hazırlayan:** Ali Güllü · **Grup:** Gündüz B · **Tarih:** 23.10.2026

Safety 4.0 Bootcamp laboratuvar föylerinden **Lab 1–4**, genel sürümdeki şişeleme hattı yerine **As Metal PLANOR 1325 T3 CNC Nesting ve Kapı İşleme Merkezi** için doldurulmuştur. Ek olarak makinenin **SWOT analizi** hazırlanmıştır.

## Makine

PLANOR 1325 T3, ahşap esaslı levhaları (MDF, sunta, kontrplak) ve alüminyum/plastik panelleri vakumla tablaya sabitleyip bilgisayar kontrolünde kesen, delen ve frezeleyen düz tablalı bir CNC nesting ve kapı işleme merkezidir. Standart tabla 1300 × 2500 mm; X 1300 mm, Y 2500 mm stroklarında 40 m/dk hızla hareket eder. Dik eksende üç bağımsız freze ünitesi vardır: biri ±90° eksenel hareketli, ikisi sabit, her biri 6 kW ER 32 (HSD) yüksek frekanslı motor, 6.000–18.000 dev/dk. Parça tutma iki adet 230 m³/h · 7,5 kW vakum pompası ile yapılır; tabla kenarlarındaki 6 pnömatik stop pistonu levhayı sıfırlar. Kontrol ünitesi **Windows tabanlı OSAI CNC**'dir (Türkçe işletim sistemi, AlphaCAM uyumlu arayüz, kablosuz modem içeren PC); servolar Yaskawa, invertör DELTA, şalt malzemesi Siemens/Schneider. Makinede 8 pozisyonlu lineer takım değiştirici, otomatik takım boyu ölçme sensörü, periyodik yağlama ve **internet üzerinden uzaktan erişim sağlayan teleservis ünitesi** bulunur.

Dik eksendeki ±90° dönebilen ünite sayesinde **kapı kilit yuvası, menteşe yatağı ve fitil kanalı gibi yatay işlemler ek aparat olmadan** yapılabilir.

Emniyet açısından en kritik nokta: levha yükleme manuel olduğu için operatörün eli **her levhada** 18.000 dev/dk dönen üç açık kesici takımın ve 40 m/dk hareket eden köprünün bulunduğu alana yaklaşır.

Kaynak: <https://www.asmetal.com.tr/en/products/machines/cnc-machining-centers/flat-table-cnc-nesting-machines/>

## Dosyalar

| Dosya | İçerik |
|---|---|
| [Makine-Anlatimi.pdf](Makine-Anlatimi.pdf) | Üretici verileri, çalışma döngüsü, varsayımlar, tehlike özeti |
| [Laboratuvar1.pdf](Laboratuvar1.pdf) | **Safety Architecture:** tehlikeler, emniyet fonksiyonları, PLr, safe state, Safety Function Map (EP 03) |
| [Laboratuvar2.pdf](Laboratuvar2.pdf) | **IEC 62443 Mini Workshop:** 6 bölge, 6 conduit, uzak erişim kararları (EP 05) |
| [Laboratuvar3.pdf](Laboratuvar3.pdf) | **Threat & Risk + Risk Matrix:** 3 siber-fiziksel senaryo, L×S×E puanlama, Risk Register (EP 04) |
| [Laboratuvar4.pdf](Laboratuvar4.pdf) | **Secure Remote Access:** mevcut → hedef mimari, emniyet bağımsızlığı gereksinimleri (EP 02 + EP 06) |
| [PLANOR-1325-T3-SWOT-Analizi.pdf](PLANOR-1325-T3-SWOT-Analizi.pdf) | SWOT matrisi, ayrıntılı maddeler, TOWS stratejileri |

## Öne çıkan sonuçlar

- **Ana emniyet fonksiyonu:** Kapı kilitlemeli güvenli durdurma. Koruyucu kapı kapalı ve kilitli değilse eksen hareketi ve mil dönüşü başlayamaz (tahmini **PL e** — S2 ampütasyon, F2 her levhada, P2 40 m/dk'da kaçış yok).
- **En kritik senaryo:** Teleservis erişiminden kapı interlock'unun yazılımda bypass edilmesi, operatör levha koyarken çevrimin başlaması ve **el/parmak ampütasyonu** (skor 18, Kritik).
- **S=3 kuralı:** USB üzerinden takım devrinin ve toz emiş interlock'unun bozulması (yangın / toz patlaması) skoru düşük kalsa da öne alındı.
- **Hedef mimari:** Jump server, VPN, MFA, kişisel hesap, oturum kaydı ve varsayılan kapalı erişim. Emniyet fonksiyonları ağdan bağımsız, kablolu ve kilitli.

## Kapsam notu

Üretici sayfasında Z ekseni stroku, makine ölçü/ağırlığı, hava basıncı, toplam elektrik gücü, emniyet donanımı ve Performance Level hakkında bilgi yoktur. Bu konular **varsayım** olarak işaretlenmiştir (bkz. Makine Anlatımı, V1–V6). Buna karşılık **kablosuz modem ve teleservis ünitesi varsayım değildir**: üretici sayfasında standart donanım olarak yazmaktadır. Varsayım olan yalnızca tesis içi ağ ve MES bağlantısıdır. Firmanın AİMSAD üyeliği açık kaynaklardan teyit edilemediği için föylerde yalnızca üretici sayfası esas alınmıştır.

> Bu çalışma bir eğitim çıktısıdır; resmî denetim, uygunluk değerlendirmesi veya belgelendirme değildir ve CE/mevzuat uygunluğu garantisi vermez.

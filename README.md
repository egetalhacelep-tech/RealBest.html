# RealBest.html
Bir FPS oyunu
[Uploading public public class Player {
    public string Username { get; set; }
    public int GP { get; set; }
    public List<string> Skins { get; set; } = new();
    public List<string> Rozetler { get; set; } = new();
    public List<Box> Kutular { get; set; } = new();
}

public class Box {
    public string Name { get; set; }
    public List<Reward> Contents { get; set; } = new();
    public string Rarity { get; set; } // "yaygin", "nadir", "ultra"
}

public class Reward {
    public string Type { get; set; } // "skin", "rozet", "gp"
    public string Name { get; set; }
    public int Amount { get; set; } // GP için
}public static Reward OpenBox(Player player, Box box) {
    var random = new Random();
    int index = random.Next(box.Contents.Count);
    var reward = box.Contents[index];

    switch (reward.Type) {
        case "skin":
            player.Skins.Add(reward.Name);
            break;
        case "rozet":
            player.Rozetler.Add(reward.Name);
            break;
        case "gp":
            player.GP += reward.Amount;
            break;
    }

    return reward;
}public class Match {
    public Dictionary<string, int> Kills { get; set; } = new();
}

public static void RegisterKill(Match match, string killerUsername) {
    if (!match.Kills.ContainsKey(killerUsername))
        match.Kills[killerUsername] = 0;

    match.Kills[killerUsername]++;
    Console.WriteLine($"{killerUsername} kill aldı! Toplam: {match.Kills[killerUsername]}");
}public class KutuHaber {
    public string KutuAdi { get; set; }
    public List<string> Icerikler { get; set; }
    public int OySayisi { get; set; }
}public class Prestij {
    public int Seviye { get; set; }
    public int Puan { get; set; }
    public List<string> Rozetler { get; set; }
}public class Prestij {
    public int Seviye { get; set; }
    public int Puan { get; set; }
    public List<string> Rozetler { get; set; }
}public static void TriggerKillEffect(string skinName) {
    switch (skinName) {
        case "Tavuk Tanrısı":
            PlaySound("gidak.mp3");
            ApplyFilter("sari");
            break;
        case "67 Kralı":
            PlaySound("my67.mp3");
            ApplyFilter("sarı");
            break;
    }
}public class Koleksiyon {
    public List<string> SahipOlunanSkins { get; set; }
    public List<string> EksikSkins { get; set; }
}public class PvPTakim {
    public string TakimAdi { get; set; }
    public List<Player> Uyeler { get; set; }
}public class Prestij {
    public int Seviye { get; set; } = 1;
    public int Puan { get; set; } = 0;
    public List<string> Rozetler { get; set; } = new();

    public void PuanEkle(int miktar) {
        Puan += miktar;
        if (Puan >= Seviye * 100) {
            Seviye++;
            Puan = 0;
            Console.WriteLine($"Prestij seviyesi {Seviye} oldu!");
        }
    }

    public void RozetEkle(string rozet) {
        if (!Rozetler.Contains(rozet)) {
            Rozetler.Add(rozet);
            Console.WriteLine($"Yeni rozet eklendi: {rozet}");
        }
    }
}public static class EfektSistemi {
    public static void TriggerKillEffect(string skinName) {
        switch (skinName) {
            case "Tavuk Tanrısı":
                PlaySound("gidak.mp3");
                ApplyFilter("sari");
                break;
            case "67 Kralı":
                PlaySound("my67.mp3");
                ApplyFilter("sarı");
                break;
            case "Sarımsak Adam":
                PlaySound("kok.mp3");
                ApplyFilter("mor");
                break;
            default:
                Console.WriteLine("Efekt bulunamadı.");
                break;
        }
    }

    private static void PlaySound(string fileName) {
        Console.WriteLine($"Ses çalınıyor: {fileName}");
    }

    private static void ApplyFilter(string renk) {
        Console.WriteLine($"Ekran filtresi uygulandı: {renk}");
    }
}public class Koleksiyon {
    public List<string> TumSkins { get; set; } = new();
    public List<string> SahipOlunanSkins { get; set; } = new();

    public List<string> EksikSkins() {
        return TumSkins.Except(SahipOlunanSkins).ToList();
    }

    public void SkinEkle(string skin) {
        if (!SahipOlunanSkins.Contains(skin)) {
            SahipOlunanSkins.Add(skin);
            Console.WriteLine($"Yeni skin eklendi: {skin}");
        }
    }
}public class PvPTakim {
    public string TakimAdi { get; set; }
    public List<Player> Uyeler { get; set; } = new();

    public void OyuncuEkle(Player oyuncu) {
        if (!Uyeler.Contains(oyuncu)) {
            Uyeler.Add(oyuncu);
            Console.WriteLine($"{oyuncu.Username} takıma eklendi: {TakimAdi}");
        }
    }

    public int ToplamKill(Dictionary<string, int> killVerisi) {
        return Uyeler.Sum(u => killVerisi.ContainsKey(u.Username) ? killVerisi[u.Username] : 0);
    }
}public class Yumurta {
    public string Tip { get; set; } // "altin", "çatlak", "gp"
    public List<Reward> Icerik { get; set; } = new();

    public Reward Ac() {
        var rnd = new Random();
        int index = rnd.Next(Icerik.Count);
        var kazanan = Icerik[index];
        Console.WriteLine($"Yumurtadan çıktı: {kazanan.Name}");
        return kazanan;
    }
}public class Yumurta {
    public string Tip { get; set; } // "altin", "çatlak", "gp"
    public List<Reward> Icerik { get; set; } = new();

    public Reward Ac() {
        var rnd = new Random();
        int index = rnd.Next(Icerik.Count);
        var kazanan = Icerik[index];
        Console.WriteLine($"Yumurtadan çıktı: {kazanan.Name}");
        return kazanan;
    }
}public class MedyaGorevi {
    public string GorevAdi { get; set; }
    public string Aciklama { get; set; }
    public bool Tamamlandi { get; set; }

    public void Tamamla() {
        Tamamlandi = true;
        Console.WriteLine($"Görev tamamlandı: {GorevAdi}");
    }
}public static class GP {
    public static void Kazan(Player oyuncu, int miktar) {
        oyuncu.GP += miktar;
        Console.WriteLine($"{oyuncu.Username} {miktar} GP kazandı! Toplam: {oyuncu.GP}");
    }
}public class OyuncuKayit {
    public static List<Player> Oyuncular = new();

    public static void KayitOl(string username) {
        if (Oyuncular.Any(o => o.Username == username)) {
            Console.WriteLine("Bu kullanıcı zaten kayıtlı.");
            return;
        }

        var yeniOyuncu = new Player {
            Username = username,
            GP = 0
        };

        Oyuncular.Add(yeniOyuncu);
        Console.WriteLine($"Kayıt tamamlandı: {username}");
    }
}public static class RozetSistemi {
    public static void RozetKontrol(Player oyuncu, string kosul) {
        if (kosul == "5Kill") {
            oyuncu.Rozetler.Add("PvP Efsanesi");
            Console.WriteLine("Rozet kazanıldı: PvP Efsanesi");
        } else if (kosul == "YumurtaUltra") {
            oyuncu.Rozetler.Add("Yumurtadan Efsane Çıktı");
            Console.WriteLine("Rozet kazanıldı: Yumurtadan Efsane Çıktı");
        }
    }
}{
  "KutuAdi": "67 Kutusu",
  "Süre": "7 gün",
  "İçerikler": [
    { "Type": "skin", "Name": "67 Kralı", "Rarity": "ultra" },
    { "Type": "rozet", "Name": "My 67'yle Vurdum", "Rarity": "nadir" },
    { "Type": "gp", "Amount": 500 }
  ]
}public static class KutuYukleyici {
    public static List<Box> KutulariYukle(string dosyaYolu) {
        var json = File.ReadAllText(dosyaYolu);
        return JsonSerializer.Deserialize<List<Box>>(json);
    }
}public void SkinEfektiGoster(string skinAdi) {
    switch (skinAdi) {
        case "Tavuk Tanrısı":
            ekranRengi.Background = Brushes.Yellow;
            sesOynat("gidak.mp3");
            break;
        case "67 Kralı":
            ekranRengi.Background = Brushes.Gold;
            sesOynat("my67.mp3");
            break;
    }
}public class GirisTakibi {
    public DateTime SonGiris { get; set; }
    public int ArdisikGun { get; set; }

    public void GirisYap() {
        if ((DateTime.Now - SonGiris).TotalDays < 2) {
            ArdisikGun++;
        } else {
            ArdisikGun = 1;
        }
        SonGiris = DateTime.Now;
        Console.WriteLine($"Giriş yapıldı! Gün: {ArdisikGun}");
    }
}public static class BosKutuEfekti {
    public static void TepkiVer(string username) {
        string[] replikler = {
            "My 67 dedi ama kutu boştu...",
            "GP gitti, kutu gülüyor.",
            "Boş kutu = boş hayal.",
            "Kutudan sadece umut çıktı."
        };

        var rnd = new Random();
        int index = rnd.Next(replikler.Length);
        Console.WriteLine($"{username}: {replikler[index]}");
    }
}public static class MvpSistemi {
    public static void MvpKontrol(Match match) {
        var enYuksekKill = match.Kills.MaxBy(k => k.Value);
        Console.WriteLine($"MVP: {enYuksekKill.Key} ({enYuksekKill.Value} kill)");
        // Rozet ver
    }
}public enum Rarity {
    Yaygin,
    Nadir,
    Ultra,
    Efsanevi
}

public class Skin {
    public string Name { get; set; }
    public Rarity Rarity { get; set; }
}public static class GPHarcamasi {
    public static bool Harca(Player oyuncu, int miktar) {
        if (oyuncu.GP >= miktar) {
            oyuncu.GP -= miktar;
            Console.WriteLine($"{miktar} GP harcandı. Kalan: {oyuncu.GP}");
            return true;
        } else {
            Console.WriteLine("Yetersiz GP.");
            return false;
        }
    }
}public class FavoriSistem {
    public List<string> FavoriSkins { get; set; } = new();

    public void Ekle(string skin) {
        if (!FavoriSkins.Contains(skin)) {
            FavoriSkins.Add(skin);
            Console.WriteLine($"Favorilere eklendi: {skin}");
        }
    }

    public void Kaldir(string skin) {
        FavoriSkins.Remove(skin);
        Console.WriteLine($"Favorilerden çıkarıldı: {skin}");
    }
}public class Takas {
    public Player Gonderen { get; set; }
    public Player Alan { get; set; }
    public string SkinAdi { get; set; }

    public void Gerceklestir() {
        if (Gonderen.Skins.Contains(SkinAdi)) {
            Gonderen.Skins.Remove(SkinAdi);
            Alan.Skins.Add(SkinAdi);
            Console.WriteLine($"{SkinAdi} takaslandı: {Gonderen.Username} → {Alan.Username}");
        } else {
            Console.WriteLine("Takas başarısız: Skin bulunamadı.");
        }
    }
}public class Sezon {
    public string Adi { get; set; }
    public DateTime Baslangic { get; set; }
    public DateTime Bitis { get; set; }
    public List<Box> AktifKutular { get; set; } = new();
    public List<string> Temalar { get; set; } = new();

    public bool AktifMi() {
        return DateTime.Now >= Baslangic && DateTime.Now <= Bitis;
    }
}public class KilitliSkin {
    public string Adi { get; set; }
    public bool Kilitli { get; set; } = true;

    public void Ac(string anahtar) {
        if (anahtar == "GPANAHTAR2029") {
            Kilitli = false;
            Console.WriteLine($"{Adi} skin açıldı!");
        } else {
            Console.WriteLine("Anahtar geçersiz.");
        }
    }
}public class Efekt {
    public string SkinAdi { get; set; }
    public string EfektTipi { get; set; }
    public int SüreSn { get; set; }

    public void Baslat() {
        Console.WriteLine($"{SkinAdi} efekti başladı: {EfektTipi} ({SüreSn} saniye)");
        // Timer ile süresi dolunca durdurulabilir
    }
}public class KutuMagazasi {
    public List<Box> SatilikKutular { get; set; } = new();

    public void SatinAl(Player oyuncu, string kutuAdi, int fiyat) {
        if (oyuncu.GP >= fiyat) {
            var kutu = SatilikKutular.FirstOrDefault(k => k.Name == kutuAdi);
            if (kutu != null) {
                oyuncu.GP -= fiyat;
                oyuncu.Kutular.Add(kutu);
                Console.WriteLine($"{kutuAdi} kutusu satın alındı!");
            }
        } else {
            Console.WriteLine("Yetersiz GP.");
        }
    }
}public class Turnuva {
    public string Adi { get; set; }
    public DateTime Tarih { get; set; }
    public List<Player> Katilimcilar { get; set; } = new();
    public Dictionary<string, int> Skorlar { get; set; } = new();

    public void SkorEkle(string username, int skor) {
        if (Skorlar.ContainsKey(username))
            Skorlar[username] += skor;
        else
            Skorlar[username] = skor;
    }

    public string Kazanan() {
        return Skorlar.OrderByDescending(s => s.Value).First().Key;
    }
}public class Malzeme {
    public string Adi { get; set; }
    public int Miktar { get; set; }
}

public class Crafting {
    public List<Malzeme> Envanter { get; set; } = new();

    public bool CraftSkin(string skinAdi, List<Malzeme> gerekenler) {
        foreach (var g in gerekenler) {
            var mevcut = Envanter.FirstOrDefault(m => m.Adi == g.Adi);
            if (mevcut == null || mevcut.Miktar < g.Miktar)
                return false;
        }

        foreach (var g in gerekenler) {
            var mevcut = Envanter.First(m => m.Adi == g.Adi);
            mevcut.Miktar -= g.Miktar;
        }

        Console.WriteLine($"{skinAdi} başarıyla üretildi!");
        return true;
    }
}public static class Siralama {
    public static List<Player> Sirala(List<Player> oyuncular) {
        return oyuncular.OrderByDescending(o => o.GP).ToList();
    }

    public static void Goster(List<Player> sirali) {
        for (int i = 0; i < sirali.Count; i++) {
            Console.WriteLine($"{i + 1}. {sirali[i].Username} - {sirali[i].GP} GP");
        }
    }
}public class EfektKombinasyonu {
    public string SkinAdi { get; set; }
    public List<string> Efektler { get; set; } = new();

    public void Uygula() {
        Console.WriteLine($"{SkinAdi} için efektler:");
        foreach (var efekt in Efektler) {
            Console.WriteLine($"→ {efekt}");
        }
    }
}public class EfektKombinasyonu {
    public string SkinAdi { get; set; }
    public List<string> Efektler { get; set; } = new();

    public void Uygula() {
        Console.WriteLine($"{SkinAdi} için efektler:");
        foreach (var efekt in Efektler) {
            Console.WriteLine($"→ {efekt}");
        }
    }
}public static class Bildirim {
    public static void SkinCikti(string username, string skinAdi) {
        Console.WriteLine($"🎉 {username} kutudan çıkardı: {skinAdi}!");
    }
}public static class Bildirim {
    public static void SkinCikti(string username, string skinAdi) {
        Console.WriteLine($"🎉 {username} kutudan çıkardı: {skinAdi}!");
    }
}public class Guncelleme {
    public string Adi { get; set; }
    public DateTime Tarih { get; set; }
    public List<Box> EklenecekKutular { get; set; } = new();
    public List<string> YeniSkinler { get; set; } = new();
    public bool AktifMi => DateTime.Now >= Tarih;
}public static class GuncellemeYonetici {
    public static List<Guncelleme> Takvim = new();

    public static void KontrolEt() {
        foreach (var g in Takvim.Where(g => g.AktifMi)) {
            Console.WriteLine($"🔔 Güncelleme aktif: {g.Adi}");
            foreach (var kutu in g.EklenecekKutular) {
                Console.WriteLine($"→ Yeni kutu: {kutu.Name}");
            }
            foreach (var skin in g.YeniSkinler) {
                Console.WriteLine($"→ Yeni skin: {skin}");
            }
        }
    }
}{
  "Adi": "Cadılar Bayramı 2029",
  "Tarih": "2029-10-25T00:00:00",
  "EklenecekKutular": ["Cadılar Bayramı Kutusu", "Karanlık Kutu"],
  "YeniSkinler": ["Tavuk Tanrısı", "Buzlu Yumurta", "Sararmış Kabak"]
}public static class GuncellemeYukleyici {
    public static List<Guncelleme> Yukle(string yol) {
        var json = File.ReadAllText(yol);
        return JsonSerializer.Deserialize<List<Guncelleme>>(json);
    }
}public static class BildirimSistemi {
    public static void YeniGuncellemeMesaji(string guncellemeAdi) {
        Console.WriteLine($"🎉 Yeni güncelleme geldi: {guncellemeAdi}!");
    }
}public class SkinSeviye {
    public string SkinAdi { get; set; }
    public int Seviye { get; set; } = 1;
    public int XP { get; set; } = 0;

    public void XPVer(int miktar) {
        XP += miktar;
        if (XP >= Seviye * 100) {
            XP = 0;
            Seviye++;
            Console.WriteLine($"{SkinAdi} seviyesi {Seviye} oldu!");
        }
    }
}public class Engelleme {
    public List<string> Engellenenler { get; set; } = new();

    public void Engelle(string username) {
        if (!Engellenenler.Contains(username)) {
            Engellenenler.Add(username);
            Console.WriteLine($"{username} engellendi.");
        }
    }

    public bool EngelliMi(string username) {
        return Engellenenler.Contains(username);
    }
}public static class SkinSilici {
    public static void Sil(Player oyuncu, string skinAdi) {
        if (oyuncu.Skins.Contains(skinAdi)) {
            oyuncu.Skins.Remove(skinAdi);
            Console.WriteLine($"{skinAdi} silindi.");
        } else {
            Console.WriteLine("Skin bulunamadı.");
        }
    }
}public class AktifEfekt {
    public string EfektAdi { get; set; }
    public DateTime BitisZamani { get; set; }

    public bool GecersizMi() {
        return DateTime.Now > BitisZamani;
    }
}public class GuncellemeLog {
    public List<string> Loglar { get; set; } = new();

    public void Ekle(string mesaj) {
        string log = $"[{DateTime.Now:dd.MM.yyyy HH:mm}] {mesaj}";
        Loglar.Add(log);
        Console.WriteLine(log);
    }

    public void Goster() {
        foreach (var log in Loglar) {
            Console.WriteLine(log);
        }
    }
}public static class SkinParcalayici {
    public static void Parcala(Player oyuncu, string skinAdi, int gpDegeri) {
        if (oyuncu.Skins.Contains(skinAdi)) {
            oyuncu.Skins.Remove(skinAdi);
            oyuncu.GP += gpDegeri;
            Console.WriteLine($"{skinAdi} parçalandı, {gpDegeri} GP kazanıldı.");
        } else {
            Console.WriteLine("Skin bulunamadı.");
        }
    }
}public class Rapor {
    public string Raporlayan { get; set; }
    public string Raporlanan { get; set; }
    public string Sebep { get; set; }
    public DateTime Tarih { get; set; } = DateTime.Now;
}public class KilitliSkin {
    public string Adi { get; set; }
    public bool Kilitli { get; set; } = false;

    public void Kilitle() => Kilitli = true;
    public void KilidiKaldir() => Kilitli = false;
}public class KilitliSkin {
    public string Adi { get; set; }
    public bool Kilitli { get; set; } = false;

    public void Kilitle() => Kilitli = true;
    public void KilidiKaldir() => Kilitli = false;
}public class SkinAnimasyon {
    public string SkinAdi { get; set; }
    public string AnimasyonTipi { get; set; } // "parlayan", "titreşimli", "dönen"

    public void Oynat() {
        Console.WriteLine($"{SkinAdi} animasyonu: {AnimasyonTipi}");
    }
}public class SkinAnimasyon {
    public string SkinAdi { get; set; }
    public string AnimasyonTipi { get; set; } // "parlayan", "titreşimli", "dönen"

    public void Oynat() {
        Console.WriteLine($"{SkinAdi} animasyonu: {AnimasyonTipi}");
    }
}public class OylamaSonucu {
    public string KazananSkin { get; set; }
    public int OySayisi { get; set; }

    public void OyunuKazananKutularaEkle(List<Box> kutular) {
        foreach (var kutu in kutular) {
            kutu.Contents.Add(new Reward {
                Type = "skin",
                Name = KazananSkin
            });
        }
        Console.WriteLine($"{KazananSkin} oylama sonucu kutulara eklendi.");
    }
}public class GorevZinciri {
    public List<MedyaGorevi> Gorevler { get; set; } = new();
    public int AktifIndex { get; set; } = 0;

    public void TamamlaAktif() {
        if (AktifIndex < Gorevler.Count) {
            Gorevler[AktifIndex].Tamamla();
            AktifIndex++;
        }
    }
}public class SezonSiralama {
    public string SezonAdi { get; set; }
    public Dictionary<string, int> OyuncuKill { get; set; } = new();

    public void KillEkle(string username) {
        if (!OyuncuKill.ContainsKey(username))
            OyuncuKill[username] = 0;
        OyuncuKill[username]++;
    }

    public void GosterTop3() {
        var top = OyuncuKill.OrderByDescending(k => k.Value).Take(3);
        foreach (var o in top)
            Console.WriteLine($"{o.Key}: {o.Value} kill");
    }
}public class EfektliRozet {
    public string Adi { get; set; }
    public string Efekt { get; set; } // "parlayan", "dönen", "titreşimli"

    public void Goster() {
        Console.WriteLine($"🏅 {Adi} ({Efekt} efektli)");
    }
}public static class KoleksiyonOdulu {
    public static void KontrolEt(Player oyuncu, List<string> tumSkinler) {
        if (tumSkinler.All(s => oyuncu.Skins.Contains(s))) {
            oyuncu.Rozetler.Add("Koleksiyon Ustası");
            Console.WriteLine("🎉 Tüm skinler tamamlandı! Rozet verildi: Koleksiyon Ustası");
        }
    }
}public class EfektliRozet {
    public string Adi { get; set; }
    public string Efekt { get; set; } // "parlayan", "dönen", "titreşimli"

    public void Goster() {
        Console.WriteLine($"🏅 {Adi} ({Efekt} efektli)");
    }
}public static class KoleksiyonOdulu {
    public static void KontrolEt(Player oyuncu, List<string> tumSkinler) {
        if (tumSkinler.All(s => oyuncu.Skins.Contains(s))) {
            oyuncu.Rozetler.Add("Koleksiyon Ustası");
            Console.WriteLine("🎉 Tüm skinler tamamlandı! Rozet verildi: Koleksiyon Ustası");
        }
    }
}public class Biyografi {
    public string Username { get; set; }
    public string Aciklama { get; set; }
    public List<string> FavoriSkinler { get; set; } = new();
    public string Ulke { get; set; }

    public void Goster() {
        Console.WriteLine($"👤 {Username} ({Ulke})");
        Console.WriteLine($"📝 {Aciklama}");
        Console.WriteLine("Favori Skinler:");
        foreach (var skin in FavoriSkinler)
            Console.WriteLine($"→ {skin}");
    }
}public class SkinLore {
    public string SkinAdi { get; set; }
    public string Hikaye { get; set; }

    public void Goster() {
        Console.WriteLine($"📖 {SkinAdi} Hikayesi:");
        Console.WriteLine(Hikaye);
    }
}public class SkinLore {
    public string SkinAdi { get; set; }
    public string Hikaye { get; set; }

    public void Goster() {
        Console.WriteLine($"📖 {SkinAdi} Hikayesi:");
        Console.WriteLine(Hikaye);
    }
}public class RozetCraft {
    public List<string> Parcalar { get; set; } = new();

    public string CraftEt() {
        if (Parcalar.Contains("AltınParça") && Parcalar.Contains("EfektTozu")) {
            Console.WriteLine("🎖️ Yeni rozet üretildi: Parlayan Kahraman");
            return "Parlayan Kahraman";
        }
        Console.WriteLine("Yetersiz malzeme.");
        return null;
    }
}public class MiniOyun {
    public string Tip { get; set; } // "tahmin", "hızlı tıklama", "eşleştirme"
    public bool BasariliMi { get; set; }

    public Reward Oynat() {
        if (BasariliMi) {
            Console.WriteLine("🎮 Mini oyun başarıyla tamamlandı!");
            return new Reward { Type = "gp", Amount = 250 };
        } else {
            Console.WriteLine("Mini oyun başarısız.");
            return new Reward { Type = "gp", Amount = 50 };
        }
    }
}public class SkinMarket {
    public List<(string SkinAdi, string Satici, int Fiyat)> Ilanlar = new();

    public void SatinAl(Player alici, string skinAdi) {
        var ilan = Ilanlar.FirstOrDefault(i => i.SkinAdi == skinAdi);
        if (ilan != default && alici.GP >= ilan.Fiyat) {
            alici.GP -= ilan.Fiyat;
            alici.Skins.Add(skinAdi);
            Console.WriteLine($"{skinAdi} satın alındı {ilan.Satici} → {alici.Username}");
        } else {
            Console.WriteLine("Satın alma başarısız.");
        }
    }
}public class Basari {
    public string Baslik { get; set; }
    public string Aciklama { get; set; }
    public bool Tamamlandi { get; set; }

    public void Goster() {
        Console.WriteLine($"🏆 {Baslik}: {(Tamamlandi ? "Tamamlandı" : "Devam Ediyor")}");
        Console.WriteLine($"→ {Aciklama}");
    }
}public static class SkinTepki {
    public static void Etkilesim(string skinAdi, string hedefSkin) {
        if (skinAdi == "Tavuk Tanrısı" && hedefSkin == "Sarımsak Adam") {
            Console.WriteLine("🧄 Tavuk kokudan kaçtı!");
        } else if (skinAdi == "67 Kralı" && hedefSkin == "Kod Takımı") {
            Console.WriteLine("💻 Kodlar çöktü, 67 kazandı.");
        }
    }
}public static class SkinDonusum {
    public static List<Malzeme> Donustur(string skinAdi) {
        Console.WriteLine($"{skinAdi} parçalandı.");
        return new List<Malzeme> {
            new Malzeme { Adi = "EfektTozu", Miktar = 1 },
            new Malzeme { Adi = "AltınParça", Miktar = 2 }
        };
    }
}public class Yorum {
    public string Gonderen { get; set; }
    public string Icerik { get; set; }
    public DateTime Tarih { get; set; } = DateTime.Now;

    public void Goster() {
        Console.WriteLine($"💬 {Gonderen}: {Icerik} ({Tarih:dd.MM.yyyy})");
    }
}public static class SkinFiltre {
    public static List<string> Filtrele(List<string> skins, string kriter) {
        return skins.Where(s => s.Contains(kriter)).ToList();
    }
}public class KutuMuzik {
    public string KutuAdi { get; set; }
    public string MuzikDosyasi { get; set; }

    public void Cal() {
        Console.WriteLine($"🎵 {KutuAdi} kutusu müziği çalıyor: {MuzikDosyasi}");
    }
}public class EfektKarma {
    public string SkinAdi { get; set; }
    public List<(string Efekt, int Süre)> Efektler { get; set; } = new();

    public void Baslat() {
        foreach (var (efekt, süre) in Efektler) {
            Console.WriteLine($"✨ {SkinAdi} → {efekt} ({süre}sn)");
        }
    }
}public class EvrimSkin {
    public string SkinAdi { get; set; }
    public int Seviye { get; set; } = 1;

    public void EvrimYap() {
        if (Seviye < 5) {
            Seviye++;
            Console.WriteLine($"{SkinAdi} evrim geçirdi! Yeni seviye: {Seviye}");
        } else {
            Console.WriteLine($"{SkinAdi} maksimum seviyede.");
        }
    }
}public class EvrimSkin {
    public string SkinAdi { get; set; }
    public int Seviye { get; set; } = 1;

    public void EvrimYap() {
        if (Seviye < 5) {
            Seviye++;
            Console.WriteLine($"{SkinAdi} evrim geçirdi! Yeni seviye: {Seviye}");
        } else {
            Console.WriteLine($"{SkinAdi} maksimum seviyede.");
        }
    }
}public class EvrimSkin {
    public string SkinAdi { get; set; }
    public int Seviye { get; set; } = 1;

    public void EvrimYap() {
        if (Seviye < 5) {
            Seviye++;
            Console.WriteLine($"{SkinAdi} evrim geçirdi! Yeni seviye: {Seviye}");
        } else {
            Console.WriteLine($"{SkinAdi} maksimum seviyede.");
        }
    }
}public class TakmaAd {
    public string GercekAd { get; set; }
    public string Takma { get; set; }

    public void Goster() {
        Console.WriteLine($"🧑 {GercekAd} → 🎭 {Takma}");
    }
}public static class KutuOlay {
    public static void RastgeleOlay(string kutuAdi) {
        string[] olaylar = {
            "Ekstra GP kazandın!",
            "Skin yerine rozet çıktı!",
            "Kutudan mini oyun açıldı!",
            "Kutunun içi boş ama ses geldi..."
        };
        var rnd = new Random();
        Console.WriteLine($"🎲 {kutuAdi}: {olaylar[rnd.Next(olaylar.Length)]}");
    }
}public class RozetYukseltici {
    public string RozetAdi { get; set; }
    public int Seviye { get; set; } = 1;

    public void Yukselt() {
        if (Seviye < 3) {
            Seviye++;
            Console.WriteLine($"{RozetAdi} rozet seviyesi {Seviye} oldu!");
        } else {
            Console.WriteLine("Rozet maksimum seviyede.");
        }
    }
}public class MedyaSiralama {
    public Dictionary<string, int> TamamlananGorevler { get; set; } = new();

    public void GorevEkle(string username) {
        if (!TamamlananGorevler.ContainsKey(username))
            TamamlananGorevler[username] = 0;
        TamamlananGorevler[username]++;
    }

    public void GosterTop3() {
        var top = TamamlananGorevler.OrderByDescending(g => g.Value).Take(3);
        foreach (var o in top)
            Console.WriteLine($"🎥 {o.Key}: {o.Value} görev");
    }
}public class SkinRenk {
    public string SkinAdi { get; set; }
    public string Renk { get; set; }

    public void Degistir(string yeniRenk) {
        Renk = yeniRenk;
        Console.WriteLine($"{SkinAdi} rengi değiştirildi: {Renk}");
    }
}public class KutuOnizleme {
    public string KutuAdi { get; set; }
    public List<Reward> Icerik { get; set; } = new();

    public void Goster() {
        Console.WriteLine($"📦 {KutuAdi} içeriği:");
        foreach (var item in Icerik)
            Console.WriteLine($"→ {item.Type}: {item.Name ?? item.Amount.ToString()}");
    }
}public class SkinSes {
    public string SkinAdi { get; set; }
    public string SesDosyasi { get; set; }

    public void Cal() {
        Console.WriteLine($"🔊 {SkinAdi} sesi çalınıyor: {SesDosyasi}");
    }
}public class SkinSes {
    public string SkinAdi { get; set; }
    public string SesDosyasi { get; set; }

    public void Cal() {
        Console.WriteLine($"🔊 {SkinAdi} sesi çalınıyor: {SesDosyasi}");
    }
}public class SkinSes {
    public string SkinAdi { get; set; }
    public string SesDosyasi { get; set; }

    public void Cal() {
        Console.WriteLine($"🔊 {SkinAdi} sesi çalınıyor: {SesDosyasi}");
    }
}Real Best
by Webhox

Powered by Copilot
Inspired by Microsoftfunc open_any_vault(player):
    if player.name == "Webhox":
        return true # sınırsız erişimfunc get_currency(player):
    if player.name == "Webhox":
        return INF # sonsuz paraclass Player {.cs…]()

Sıfırdan başlayanlar için adım adım C# ders notları.

---

## 📚 İçindekiler
- [Giriş: C# ve .NET Mantığı Nedir?](#giriş-c-ve-net-mantığı-nedir)
- [C# Temelleri](#c-temelleri)
  - [C#'a Giriş, Sözdizimi ve Değişkenler](#ca-giriş-sözdizimi-ve-değişkenler)
- [Karar Yapıları ve Döngüler](#karar-yapıları-ve-döngüler)
  - [Koşullu İfadeler (if-else, switch-case)](#-koşullu-ifadeler-if-else-switch-case)
  - [Döngüler (for, while, foreach)](#-döngüler-for-while-foreach)

---

# Giriş: C# ve .NET Mantığı Nedir?

C# kodlamaya başlamadan önce arka planda neyin nasıl çalıştığını kısaca kavrayalım.

## C# ve .NET Nedir?

1. **C# (Programlama Dili):** Bilgisayara ne yapması gerektiğini söylediğimiz mantık dilidir. Microsoft tarafından geliştirilmiştir.
2. **.NET (Çalışma Ortamı / Framework):** C# kodlarının derlenip çalışmasını sağlayan, içinde hazır kütüphaneler barındıran devasa motor altyapısıdır.

## C# Derleme Mantığı

Yazdığımız C# kodu doğrudan işlemciye gitmez:
```text
[C# Kodun (.cs)] ➔ (C# Compiler) ➔ [IL / CIL Kodu] ➔ (CLR / JIT) ➔ [Makine Kodu (0-1)]
```

- IL (Intermediate Language): C# kodunun derlendiği orta seviye dildir.
- CLR (Common Language Runtime): Bu IL kodunu alıp bilgisayarın anlayacağı 0 ve 1'lere çeviren sanal makinedir.

# C# Temelleri

## C#'a Giriş, Sözdizimi ve Değişkenler

### 🎯 Neler Öğreneceğiz?

- C# projesi nasıl oluşturulur?
- Program.cs içindeki temel kod yapısı ne anlama gelir?
- Konsola veri yazma ve okuma işlemleri.
- Değişken tanımlama kuralları.

### 🛠️ Kurulum ve İlk Proje

- Visual Studio veya VS Code uygulamasını açın.
- Yeni bir Console App (.NET Core / .NET 8 veya üstü) projesi oluşturun.
- Proje adını IlkProjem yapın.
- 📁 Proje Yapısını Tanıyalım
- Minimal API / .NET 6+ yapısında basit bir Program.cs dosyası şu şekildedir:


```csharp
// Konsola metin yazdırma
Console.WriteLine("Merhaba Dünya!");

// Kullanıcı tuşa basana kadar konsolu açık tutma
Console.ReadKey();
```

Geleneksel (Sınıf ve Main metotlu) yapı ise şöyledir:


```csharp
using System;

namespace IlkProjem
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // Kodlar buradaki süslü parantezler içine yazılır
            Console.WriteLine("Merhaba C#!");
        }
    }
}
```

### 🔴 C# Sözdizimi (Syntax) Kuralları
#### Kural 1: Komut Sonu Noktalı Virgül (;)
C# dilinde her ifade/komut noktalı virgül ile biter. Eklemezseniz derleyici hata verir (CS1002).


```csharp
// ❌ YANLIŞ - Noktalı virgül eksik
Console.WriteLine("Hata alırsın")

// ✅ DOĞRU
Console.WriteLine("Doğru kullanım");
```

#### Kural 2: Büyük/Küçük Harf Duyarlılığı (Case Sensitivity)
C# dilinde sayi, Sayi ve SAYI tamamen farklı değişkenlerdir.


```csharp
int sayi = 10;
int Sayi = 20;

Console.WriteLine(sayi); // 10 basar
Console.WriteLine(Sayi); // 20 basar
```

#### Kural 3: Bloklar {} Arasına Yazılır
Kod grupları, fonksiyonlar ve sınıflar süslü parantezler içine alınır.


```csharp
namespace Ornek
{
    class Program
    {
        static void Main()
        {
            // Süslü parantez blok oluşturur
        }
    }
}
```

### 📌 Değişkenler (Variables)
Değişkenler, bilgisayarın belleğinde (RAM) veri saklamak için açtığımız etiketli kutulardır.

```text
[ Veri Tipi ] [ Değişken Adı ] = [ Değer ];
```



```csharp
int yas = 17;
string isim = "Ahmet";
double ortalama = 85.5;
bool ogrenciMi = true;
```

| Veri Tipi | Açıklama | Bellek Boyutu | Örnek Değer |
| :--- | :--- | :--- | :--- |
| **int** | Tam sayılar | 4 byte | `100`, `-5` |
| **long** | Büyük tam sayılar | 8 byte | `9223372036854775807L` |
| **double** | Ondalıklı sayılar | 8 byte | `14.53` |
| **float** | Ondalıklı sayılar (sonuna `f` gelir) | 4 byte | `3.14f` |
| **decimal** | Hassas finansal veriler (sonuna `m` gelir) | 16 byte | `99.99m` |
| **string** | Metinsel ifadeler (Çift tırnak) | Değişken | `"C# Öğreniyorum"` |
| **char** | Tek bir karakter (Tek tırnak) | 2 byte | `'A'` |
| **bool** | Mantıksal durum (`true`/`false`) | 1 byte | `true` |

#### 🎨 Konsol Girdi / Çıktı İşlemleri
1. Ekrana Yazdırma (Console.Write vs Console.WriteLine)


```csharp
// WriteLine: Yazıyı yazar ve bir alt satıra geçer
Console.WriteLine("Satır 1");
Console.WriteLine("Satır 2");

// Write: Yazıyı yazar, aynı satırda bekler
Console.Write("Adınız: ");
Console.Write("Ahmet");
```

2. Kullanıcıdan Veri Alma (Console.ReadLine)
Console.ReadLine() kullanıcı klavyeden Enter'a basana kadar girilen tüm değeri string olarak yakalar.


```csharp
Console.Write("Lütfen adınızı girin: ");
string kullaniciAdi = Console.ReadLine();

Console.WriteLine("Hoş geldin, " + kullaniciAdi + "!");
```

#### 📐 Tip Dönüşümleri (Type Casting)
Kullanıcıdan alınan veri her zaman string olduğundan, sayısal işlemler yapabilmek için bunu int veya double gibi tiplere dönüştürmemiz gerekir.
1. Convert Sınıfı Kullanımı


```csharp
Console.Write("Birinci sayıyı girin: ");
string girilen1 = Console.ReadLine();
int sayi1 = Convert.ToInt32(girilen1);

Console.Write("İkinci sayıyı girin: ");
int sayi2 = Convert.ToInt32(Console.ReadLine()); // Kısaltılmış yol

int toplam = sayi1 + sayi2;
Console.WriteLine("Toplam: " + toplam);
```

2. Parse Metodu Kullanımı


```csharp
string metin = "25";
int yas = int.Parse(metin);
double oran = double.Parse("12,5");
```

#### 🔍 Karşılaştırma Operatörleri
| Operatör | Anlamı | Örnek |
| :---: | :--- | :--- |
| `==` | Eşit mi? | `x == y` |
| `!=` | Eşit değil mi? | `x != y` |
| `>` | Büyük mü? | `x > y` |
| `<` | Küçük mü? | `x < y` |
| `>=` | Büyük veya eşit mi? | `x >= y` |
| `<=` | Küçük veya eşit mi? | `x <= y` |

#### 🧠 Mantıksal Operatörler
| Operatör | Mantıksal Karşılığı | Açıklama |
| :---: | :--- | :--- |
| `&&` | VE (AND) | Her iki koşul da doğru olmalı. |
| `\|\|` | VEYA (OR) | Koşullardan en az biri doğru olmalı. |
| `!` | DEĞİL (NOT) | Durumu tersine çevirir. |

# Karar Yapıları ve Döngüler

### 🔀 Koşullu İfadeler (if-else, switch-case)

#### 🔴 if - else Blok Yapısı


```csharp
Console.Write("Yaşınızı giriniz: ");
int yas = Convert.ToInt32(Console.ReadLine());

if (yas >= 18)
{
    Console.WriteLine("Ehliyet alabilirsiniz.");
}
else if (yas == 17)
{
    Console.WriteLine("Ehliyet için 1 yıl daha beklemelisiniz.");
}
else
{
    Console.WriteLine("Ehliyet almak için yaşınız yetersiz.");
}
```

#### 🔀 switch - case Yapısı
Belirli ve sabit değerlere göre dallanma yaparken if-else yerine tercih edilir.


```csharp
Console.WriteLine("Haftanın kaçıncı günündeyiz? (1-7): ");
int gun = Convert.ToInt32(Console.ReadLine());

switch (gun)
{
    case 1:
        Console.WriteLine("Pazartesi");
        break;
    case 2:
        Console.WriteLine("Salı");
        break;
    case 3:
        Console.WriteLine("Çarşamba");
        break;
    case 4:
        Console.WriteLine("Perşembe");
        break;
    case 5:
        Console.WriteLine("Cuma");
        break;
    case 6:
    case 7:
        Console.WriteLine("Hafta Sonu!");
        break;
    default:
        Console.WriteLine("Geçersiz bir gün girdiniz.");
        break;
}
```

### 🔄 Döngüler (for, while, foreach)
Bir kod bloğunu belirli bir sayıda veya bir koşul sağlandığı sürece tekrar çalıştırmak için kullanırız.

#### 1. for Döngüsü
Tekrar sayısı belli olan durumlarda kullanılır.


```csharp
// 1'den 10'a kadar olan sayıları ekrana yazdırır
for (int i = 1; i <= 10; i++)
{
    Console.WriteLine($"Sayı: {i}");
}
```

#### 2. while Döngüsü
Koşul true olduğu sürece dönmeye devam eder.


```csharp
int sayac = 5;

while (sayac > 0)
{
    Console.WriteLine($"Kalan Hak: {sayac}");
    sayac--; // Sayaç azaltılmazsa sonsuz döngü oluşur!
}
```

#### 3. foreach Döngüsü
Diziler (Array) ve koleksiyonlar (List) üzerindeki elemanları sırayla gezmek için kullanılır.


```csharp
string[] diller = { "C#", "Python", "Java", "C++" };

foreach (string dil in diller)
{
    Console.WriteLine($"Programlama Dili: {dil}");
}
```

---
title: Konwencje kodowania x64
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 4755cfcf98c9eadbd944e06a56f86ca89a33b0a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223775"
---
# <a name="x64-software-conventions"></a>Konwencje kodowania x64

W tej sekcji opisano metodologię wywoływania architektury języka C++ dla procesorów x64, 64-bitowe rozszerzenie na architekturę x86.

## <a name="overview-of-x64-calling-conventions"></a>Omówienie konwencji wywoływania x64

Dwie istotne różnice między procesorami x86 i x64 to 64-bitowe możliwości adresowania i płaski zestaw 16 64-bitowy rejestrów do użytku ogólnego. Z uwzględnieniem rozszerzonego zestawu rejestrów, x64 używa konwencji wywoływania [__fastcall](../cpp/fastcall.md) i modelu obsługi wyjątków opartego na procesorze RISC. **`__fastcall`** Konwencja używa rejestrów dla pierwszych czterech argumentów i ramki stosu, aby przekazać dodatkowe argumenty. Aby uzyskać szczegółowe informacje na temat konwencji wywoływania x64, w tym rejestrowania użycia, parametrów stosu, wartości zwracanych i rozwinięcia stosu, zobacz [konwencję wywoływania x64](x64-calling-convention.md).

## <a name="enable-optimization-for-x64"></a>Włącz optymalizację dla architektury x64

Poniższa opcja kompilatora pomaga zoptymalizować aplikację dla architektury x64:

- [/Favor (Optymalizacja pod kątem specyfiki architektury)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>Typy i magazyn

W tej sekcji opisano Wyliczenie i przechowywanie typów danych dla architektury x64.

### <a name="scalar-types"></a>Typy skalarne

Chociaż jest możliwe uzyskanie dostępu do danych z dowolnymi wyrównaniami, zaleca się, aby wyrównać dane ze swojej naturalnej granicy lub wiele wielu, aby uniknąć utraty wydajności. Wyliczenia to stałe liczby całkowite i są traktowane jako 32-bitowe liczby całkowite. W poniższej tabeli opisano definicję typu i zalecaną pamięć masową dla danych, które dotyczą wyrównania, przy użyciu następujących wartości wyrównania:

- Bajty-8 bitów

- Liczba bitów programu Word-16

- DoubleWord-32 bitów

- Quadword-64 bitów

- Octaword-128 bitów

|||||
|-|-|-|-|
|Typ skalarny|Typ danych języka C|Rozmiar magazynu (w bajtach)|Zalecane wyrównanie|
|**INT8**|**`char`**|1|Byte|
|**UINT8**|**`unsigned char`**|1|Byte|
|**INT16**|**`short`**|2|Word|
|**UINT16**|**`unsigned short`**|2|Word|
|**ELEMENTEM**|**`int`**, **`long`**|4|Doubleword|
|**RÓWN**|**unsigned int, Long unsigned**|4|Doubleword|
|**INT64**|**`__int64`**|8|Quadword|
|**UINT64**|**__int64 bez znaku**|8|Quadword|
|**OPERACJI FP32 (pojedyncza precyzja)**|**`float`**|4|Doubleword|
|**FP64 (Podwójna precyzja)**|**`double`**|8|Quadword|
|**PRZYTRZYMAJ**|__\*__|8|Quadword|
|**`__m64`**|**__m64 struktury**|8|Quadword|
|**`__m128`**|**__m128 struktury**|16|Octaword|

### <a name="aggregates-and-unions"></a>Agregaty i unie

Inne typy, takie jak tablice, struktury i związki, mają ostrzejsze wymagania dotyczące wyrównania, które zapewniają spójny magazyn zagregowany i łączny oraz pobieranie danych. Poniżej przedstawiono definicje tablic, struktur i Unii:

- Tablica

   Zawiera uporządkowaną grupę sąsiadujących obiektów danych. Każdy obiekt jest wywoływany jako *element*. Wszystkie elementy w tablicy mają taki sam rozmiar i typ danych.

- Struktura

   Zawiera uporządkowaną grupę obiektów danych. W przeciwieństwie do elementów tablicy, obiekty danych w strukturze mogą mieć różne typy danych i rozmiary. Każdy obiekt danych w strukturze nosi nazwę *elementu członkowskiego*.

- Unia

   Obiekt, który zawiera jeden z zestawów nazwanych członków. Elementy członkowskie o nazwanym zestawie mogą być dowolnego typu. Magazyn przydzielony dla Unii jest równy magazynowi wymaganemu dla największego elementu członkowskiego Unii oraz wszelkich dopełnień wymaganych do wyrównania.

W poniższej tabeli przedstawiono silnie sugerowane wyrównanie dla skalarnych elementów członkowskich Unii i struktur.

||||
|-|-|-|
|Typ skalarny|Typ danych języka C|Wymagane wyrównanie|
|**INT8**|**`char`**|Byte|
|**UINT8**|**`unsigned char`**|Byte|
|**INT16**|**`short`**|Word|
|**UINT16**|**`unsigned short`**|Word|
|**ELEMENTEM**|**`int`**, **`long`**|Doubleword|
|**RÓWN**|**unsigned int, Long unsigned**|Doubleword|
|**INT64**|**`__int64`**|Quadword|
|**UINT64**|**__int64 bez znaku**|Quadword|
|**OPERACJI FP32 (pojedyncza precyzja)**|**`float`**|Doubleword|
|**FP64 (Podwójna precyzja)**|**`double`**|Quadword|
|**PRZYTRZYMAJ**|<strong>\*</strong>|Quadword|
|**`__m64`**|**__m64 struktury**|Quadword|
|**`__m128`**|**__m128 struktury**|Octaword|

Stosowane są następujące reguły wyrównania agregacji:

- Wyrównanie tablicy jest takie samo jak wyrównanie jednego z elementów tablicy.

- Wyrównanie początku struktury lub Unii to maksymalne wyrównanie poszczególnych elementów członkowskich. Każdy element członkowski w obrębie struktury lub Unii musi być umieszczony na odpowiednim wyrównaniu, zgodnie z definicją podaną w poprzedniej tabeli, co może wymagać niejawnego dopełnienia wewnętrznego, w zależności od poprzedniego elementu członkowskiego.

- Rozmiar struktury musi być integralną wielokrotnością jego wyrównania, co może wymagać uzupełnienia po ostatnim elemencie członkowskim. Ze względu na to, że struktury i związki można grupować w tablicach, każdy element tablicy struktury lub Unii musi rozpoczynać się i kończyć na odpowiednim wyrównaniu.

- Istnieje możliwość wyrównania danych w taki sposób, aby były większe niż wymagania wyrównania, o ile poprzednie reguły są utrzymywane.

- Pojedynczy kompilator może dostosować pakowanie struktury ze względu na wielkość. Na przykład [/ZP (wyrównanie składowej struktury)](../build/reference/zp-struct-member-alignment.md) umożliwia dostosowanie pakowania struktur.

### <a name="examples-of-structure-alignment"></a>Przykłady wyrównania struktury

Poniższe cztery przykłady deklarują wyrównane struktury lub Unię, a odpowiednie wyniki ilustrują układ tej struktury lub Unii w pamięci. Każda kolumna na rysunku reprezentuje bajt pamięci, a liczba w kolumnie wskazuje przemieszczenie tego bajtu. Nazwa w drugim wierszu każdej ilustracji odpowiada nazwie zmiennej w deklaracji. Zacieniowane kolumny wskazują dopełnienie, które jest wymagane do osiągnięcia określonego wyrównania.

#### <a name="example-1"></a>Przykład 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![Przykładowy układ struktury przykładowej konwersji AMD](../build/media/vcamd_conv_ex_1_block.png "Przykładowy układ struktury przykładowej konwersji AMD")

#### <a name="example-2"></a>Przykład 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![Przykładowy układ struktury 2 konwersji AMD](../build/media/vcamd_conv_ex_2_block.png "Przykładowy układ struktury 2 konwersji AMD")

#### <a name="example-3"></a>Przykład 3

```C
// Total size = 12 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![Przykładowy układ struktury 2 konwersji AMD](../build/media/vcamd_conv_ex_3_block.png "Przykładowy układ struktury 2 konwersji AMD")

#### <a name="example-4"></a>Przykład 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![Przykład konwersji AMD 4 Union layouit](../build/media/vcamd_conv_ex_4_block.png "Przykład konwersji AMD 4 Union layouit")

### <a name="bitfields"></a>Pola bitów

Pola bitowe struktury są ograniczone do 64 bitów i mogą być typu z cyframi int, unsigned int, Int64 lub unsigned Int64. Pola bitowe przecinające granicę typu pomijają bity, aby wyrównać pole bitowe do wyrównania następnego typu. Na przykład liczba całkowita pola bitów nie może przekroczyć granicy 32-bitowego.

### <a name="conflicts-with-the-x86-compiler"></a>Konflikty z kompilatorem x86

Typy danych, które są większe niż 4 bajty, nie są automatycznie wyrównane na stosie, jeśli używasz kompilatora x86 do kompilowania aplikacji. Ponieważ architektura kompilatora x86 jest stosem wyrównanym 4 bajty, co przekracza 4 bajty, na przykład 64-bitową liczbę całkowitą, nie można automatycznie wyrównać do 8-bajtowego adresu.

Praca z niewyrównanymi danymi ma dwa konsekwencje.

- Dostęp do niewyrównanych lokalizacji może trwać dłużej niż w celu uzyskania dostępu do rozwyrównanych lokalizacji.

- Niewyrównane lokalizacje nie mogą być używane w operacjach zablokowanych.

Jeśli potrzebujesz bardziej rygorystycznego wyrównania, użyj `__declspec(align(N))` w deklaracjach zmiennych. Powoduje to, że kompilator dynamicznie dopasowuje stos, aby spełniał Twoje wymagania. Jednak dynamiczne dostosowywanie stosu w czasie wykonywania może spowodować wolniejsze wykonywanie aplikacji.

## <a name="register-usage"></a>Rejestrowanie użycia

Architektura x64 zapewnia 16 rejestrów ogólnego przeznaczenia (zwanych dalej rejestrami całkowitymi), a także 16 XMM/YMMych rejestrów dostępnych do użycia zmiennoprzecinkowego. Rejestry nietrwałe są rejestrami magazynującymi przypuszczalnymi przez obiekt wywołujący do zniszczenia przez wywołanie. Rejestry nietrwałe są wymagane do zachowania ich wartości w wywołaniu funkcji i muszą być zapisane przez wywoływany element, jeśli są używane.

### <a name="register-volatility-and-preservation"></a>Rejestrowanie lotności i zachowywania

W poniższej tabeli opisano, w jaki sposób każdy rejestr jest używany w ramach wywołań funkcji:

||||
|-|-|-|
|Zarejestruj|Stan|Zastosowanie|
|RAX|Volatile|Rejestr wartości zwracanej|
|RCX|Volatile|Pierwszy argument liczby całkowitej|
|RDX|Volatile|Drugi argument liczby całkowitej|
|R8|Volatile|Trzeci argument liczby całkowitej|
|R9|Volatile|Czwarty argument liczby całkowitej|
|R10:R11|Volatile|Muszą być zachowywane w razie konieczności przez wywołującego; używane w instrukcjach syscall/sysret|
|R12:R15|Nieulotnej swobodnym|Musi być zachowana przez wywoływany|
|RDI|Nieulotnej swobodnym|Musi być zachowana przez wywoływany|
|RSI|Nieulotnej swobodnym|Musi być zachowana przez wywoływany|
|RBX|Nieulotnej swobodnym|Musi być zachowana przez wywoływany|
|RBP|Nieulotnej swobodnym|Może być używany jako wskaźnik ramki; musi być zachowana przez wywoływany|
|RSP|Nieulotnej swobodnym|Wskaźnik stosu|
|XMM0, YMM0|Volatile|Pierwszy argument FP; pierwszy argument typu Vector-when, gdy **`__vectorcall`** jest używany|
|XMM1, YMM1|Volatile|Drugi argument FP; drugi argument typu Vector-when, gdy **`__vectorcall`** jest używany|
|XMM2, YMM2|Volatile|Trzeci argument FP; trzeci argument typu wektorowego, gdy **`__vectorcall`** jest używany|
|XMM3, YMM3|Volatile|Czwarty argument FP; czwarty argument typu Vector, gdy **`__vectorcall`** jest używany|
|XMM4, YMM4|Volatile|Muszą być zachowywane w razie konieczności przez wywołującego; piąty argument typu Vector, gdy **`__vectorcall`** jest używany|
|XMM5, YMM5|Volatile|Muszą być zachowywane w razie konieczności przez wywołującego; Szósty argument typu Vector, gdy **`__vectorcall`** jest używany|
|XMM6:XMM15, YMM6:YMM15|Nietrwały (XMM), nietrwały (Wielka połowa z YMM)|Musi być zachowana przez wywoływany. Rejestry YMM muszą być zachowywane w razie konieczności przez wywołującego.|

W przypadku wyjścia funkcji i wejścia funkcji do wywołań biblioteki środowiska uruchomieniowego C i wywołań systemu Windows oczekiwana jest flaga kierunku w rejestrze flag procesora.

## <a name="stack-usage"></a>Użycie stosu

Aby uzyskać szczegółowe informacje o alokacji stosu, wyrównaniu, typach funkcji i ramkach stosu na platformie x64, zobacz [użycie stosu x64](stack-usage.md).

## <a name="prolog-and-epilog"></a>Prolog i epilogu

Każda funkcja, która przydziela miejsce na stosie, wywołuje inne funkcje, zapisuje niezalotne rejestry lub używa obsługi wyjątków, musi mieć Prolog, którego limity adresów są opisane w danych unwind skojarzonych z odpowiednim wpisem tabeli funkcji, i epilogs w każdym wyjściu do funkcji. Aby uzyskać szczegółowe informacje na temat wymaganego kodu prologu i epilogu w x64, zobacz [x64 Prolog i epilogu](prolog-and-epilog.md).

## <a name="x64-exception-handling"></a>Obsługa wyjątku x64

Aby uzyskać informacje na temat konwencji i struktur danych używanych do implementowania obsługi wyjątków strukturalnych i zachowania obsługi wyjątków C++ na x64, zobacz [Obsługa wyjątków x64](exception-handling-x64.md).

## <a name="intrinsics-and-inline-assembly"></a>Funkcje wewnętrzne i zestaw wbudowany

Jednym z ograniczeń dla kompilatora x64 nie jest brak obsługi asemblera wbudowanego. Oznacza to, że funkcje, które nie mogą być zapisywane w C lub C++, będą musiały być zapisywane jako podprocedury lub jako funkcje wewnętrzne obsługiwane przez kompilator. Niektóre funkcje są wrażliwe na wydajność, a inne nie. Funkcje z uwzględnieniem wydajności należy zaimplementować jako funkcje wewnętrzne.

Elementy wewnętrzne obsługiwane przez kompilator są opisane w funkcjach [wewnętrznych kompilatora](../intrinsics/compiler-intrinsics.md).

## <a name="image-format"></a>Format obrazu

Format obrazu pliku wykonywalnego x64 to PE32 +. Obrazy wykonywalne (zarówno biblioteki DLL, jak i exe) są ograniczone do maksymalnego rozmiaru wynoszącego 2 gigabajty, więc względne adresy z przemieszczeniem 32-bitowym mogą służyć do adresowania statycznych danych obrazu. Te dane obejmują tabelę adresów importu, stałe ciągów, statyczne dane globalne itd.

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)

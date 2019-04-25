---
title: x64 konwencje kodowania
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 11d29b6c31ccecfe5b9c51c2f9311213bd4a6732
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313858"
---
# <a name="x64-software-conventions"></a>x64 konwencje kodowania

W tej sekcji opisano wywoływania metodologii Konwencji x64, rozszerzenie 64-bitowych x86 C++ architektury.

## <a name="overview-of-x64-calling-conventions"></a>Przegląd konwencji wywoływania x64

Dwie ważne różnice między x86 i x64 są możliwości adresowania 64-bitowych i prostego zestawu 16 64-bitowych rejestrów do użytku ogólnego. Biorąc pod uwagę zestaw rejestru rozwinięty, używa x64 [__fastcall](../cpp/fastcall.md) wywoływania Konwencji i model obsługi wyjątków, na podstawie RISC. `__fastcall` Konwencji używa rejestrów, pierwsze cztery argumenty i ramki stosu do przekazywania dodatkowych argumentów. Dla informacji na temat x64 Konwencja wywoływania, rejestrowanie użycia, w tym stosu parametrów, zwracać wartości i wykonywania operacji odwijania stosu, zobacz [x64 konwencji wywoływania](x64-calling-convention.md).

## <a name="enable-optimization-for-x64"></a>Włącz optymalizację x64

Następująca opcja kompilatora pomaga zoptymalizować aplikację x64:

- [/favor (Optymalizacja pod kątem specyfiki architektury)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>Typy i Magazyn

W tej sekcji opisano wyliczenie i magazyn danych typów x64 architektury.

### <a name="scalar-types"></a>typy skalarne

Chociaż dostęp do danych z każdego wyrównania, zaleca się wyrównanie danych w jego granicę fizyczne lub niektóre wiele, aby uniknąć utraty wydajności. Typy wyliczeniowe są stałych liczb całkowitych i są traktowane jako 32-bitowych liczb całkowitych. W poniższej tabeli opisano definicji typu i zalecany magazyn danych w odniesieniu do wyrównania, używając następujących wartości wyrównania:

- Byte — 8 bitów

- Word — 16 bitów

- Bitowego — 32-bitowy

- Quadword - 64-bitowy

- Octaword - 128 bitów

|||||
|-|-|-|-|
|Typ skalarny|Typ danych C|Rozmiar magazynu (w bajtach)|Zalecane wyrównania|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|Word|
|**UINT16**|**short bez znaku**|2|Word|
|**INT32**|**int**, **długi**|4|Bitowego|
|**UINT32**|**unsigned int, niepodpisane długa**|4|Bitowego|
|**INT64**|**__int64**|8|Quadword|
|**UINT64**|**__int64 bez znaku**|8|Quadword|
|**FP32 (Pojedyncza precyzja)**|**float**|4|Bitowego|
|**FP64 (Podwójna precyzja)**|**double**|8|Quadword|
|**WSKAŹNIK**|__\*__|8|Quadword|
|**__m64**|**__m64 — struktura**|8|Quadword|
|**__m128**|**struct __m128**|16|Octaword|

### <a name="aggregates-and-unions"></a>Agregacje i unie

Inne typy, takie jak tablice, struktur i Unii, ma bardziej rygorystyczne wymagania wyrównania, zapewniający spójny Unii i agregacji magazynem i danymi pobierania. Definicje dla tablic, struktury i Unii są następujące:

- Tablica

   Zawiera grupę uporządkowane obiekty sąsiadujące danych. Każdy obiekt jest nazywany *elementu*. Wszystkie elementy w tablicy mają ten sam rozmiar i typ danych.

- Struktura

   Zawiera grupę uporządkowane obiektów danych. W odróżnieniu od elementów tablicy obiektów danych w ramach struktury może mieć różne typy danych i rozmiary. Każdy obiekt danych w strukturze jest nazywany *elementu członkowskiego*.

- Union

   Obiekt, który zawiera jeden zestaw nazwanych elementów członkowskich. Nazwany zestaw elementów członkowskich mogą być dowolnego typu. Magazyn przydzielony dla Unii jest równy magazynu wymaganego dla największego elementu członkowskiego tej Unii, a także wszelkie dopełnienie wymaganych do wyrównania.

W poniższej tabeli przedstawiono silnie sugerowane wyrównanie skalarne elementów członkowskich Unii i struktur.

||||
|-|-|-|
|Typ skalarny|Typ danych C|Wymagane wyrównania|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|Word|
|**UINT16**|**short bez znaku**|Word|
|**INT32**|**int**, **długi**|Bitowego|
|**UINT32**|**unsigned int, niepodpisane długa**|Bitowego|
|**INT64**|**__int64**|Quadword|
|**UINT64**|**__int64 bez znaku**|Quadword|
|**FP32 (Pojedyncza precyzja)**|**float**|Bitowego|
|**FP64 (Podwójna precyzja)**|**double**|Quadword|
|**WSKAŹNIK**|<strong>\*</strong>|Quadword|
|**__m64**|**__m64 — struktura**|Quadword|
|**__m128**|**struct __m128**|Octaword|

Obowiązują następujące reguły wyrównanie agregacji:

- Wyrównanie w tablicy jest taka sama jak wyrównanie elementów tablicy.

- Wyrównanie początku struktury lub Unii jest maksymalna wyrównanie dowolnego członka. Każdy element członkowski w obrębie struktury lub Unii muszą być umieszczone na jego odpowiednie wyrównanie, zgodnie z definicją w poprzedniej tabeli, które mogą wymagać niejawne dopełnienie wewnętrzne, w zależności od poprzedniego elemenut Członkowskiego.

- Rozmiar struktury musi być wielokrotnością jego wyrównania, która może wymagać dopełnienie po ostatni element członkowski. Ponieważ struktur i Unii mogą być grupowane w tablicach, każdego elementu tablicy, struktury lub Unii należy rozpocząć i końcu prawidłowego wyrównania wcześniej określona.

- Istnieje możliwość wyrównanie danych w taki sposób, aby być większa niż wymagania wyrównania, tak długo, jak poprzednich zasad są obsługiwane.

- Poszczególne kompilator może dostosować pakowanie struktury powodów rozmiar. Na przykład [/ZP (wyrównanie członka struktury)](../build/reference/zp-struct-member-alignment.md) umożliwia dostosowanie pakowanie struktur.

### <a name="examples-of-structure-alignment"></a>Przykłady wyrównania struktury

Następujące cztery przykłady zadeklarować, że wyrównany struktury lub Unii i dane porównawcze ilustrują układ tej struktury lub Unii w pamięci. Każda kolumna na ilustracji reprezentuje bajt pamięci i liczby w kolumnie wskazuje przesunięcie tego bajtu. Nazwa w drugim wierszu każdej rysunek odnosi się do nazwy zmiennej w deklaracji. Zacieniowaniu kolumn wskazują, że dopełnienie, które są wymagane do osiągnięcia określonego wyrównania.

#### <a name="example-1"></a>Przykład 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![Układ struktury przykład 1 konwersji AMD](../build/media/vcamd_conv_ex_1_block.png "AMD konwersji przykład 1 struktury układu")

#### <a name="example-2"></a>Przykład 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![Układ struktury przykład 2 konwersji AMD](../build/media/vcamd_conv_ex_2_block.png "AMD konwersji przykład 2 struktury układu")

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

![Układ struktury przykład 2 konwersji AMD](../build/media/vcamd_conv_ex_3_block.png "AMD konwersji przykład 2 struktury układu")

#### <a name="example-4"></a>Przykład 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![AMD konwersji przykład 4 złożenia layouit](../build/media/vcamd_conv_ex_4_block.png "AMD konwersji przykład 4 złożenia layouit")

### <a name="bitfields"></a>Pola bitów

Struktura pola bitowe są ograniczone do 64-bitowy i może być typu podpisany int, niepodpisane int, int64 lub int64 bez znaku. Pola bitowe, które przecinają granice typu pominie bitów, aby wyrównać bitfield do następnego wyrównanie typu. Na przykład pola bitów liczba całkowita, nie mogą przekroczyć graniczny 32-bitowych.

### <a name="conflicts-with-the-x86-compiler"></a>Powoduje konflikt z x86 kompilatora

Typy danych, które są większe niż 4 bajty nie będą automatycznie wyrównywane do stosu w przypadku użycia x86 kompilatora do skompilowania aplikacji. Ponieważ architektury x86 kompilator jest stosu wyrównany 4-bajtowych, większe niż 4 bajty, na przykład 64-bitowa liczba całkowita, nie można automatycznie wyrównywane do adresu 8-bajtowych.

Praca z niewyrównanych danych ma dwa skutki.

- Może potrwać dłużej dostęp do niewyrównanych lokalizacji nie jest potrzebny dostęp do lokalizacji wyrównane.

- Niewyrównanych lokalizacji nie można używać w operacjach blokowane.

Jeśli potrzebujesz więcej wyrównanie strict, użyj `__declspec(align(N))` na swojej deklaracji zmiennych. To powoduje, że kompilator dynamicznie wyrównać stosu odpowiadających Twoim kryteriom. Dynamiczne Dostosowywanie stosu w czasie wykonywania mogą jednak spowodować wolniejszy wykonywanie aplikacji.

## <a name="register-usage"></a>Użycie metody Register

X64 architektury stosowany do 16 rejestrów ogólnego przeznaczenia (zwany dalej rejestruje liczby całkowitej), a także 16 XMM/YMM rejestruje dostępny do użytku zmiennoprzecinkowych. Volatile rejestrów są pliki tymczasowe rejestrów domniemania przez obiekt wywołujący, które mają zostać zniszczone na wywołanie. Nieulotnej rejestrów są wymagane do zachowują swoje wartości w wywołaniu funkcji i musi zostać zapisany przez obiekt wywoływany, jeśli używany.

### <a name="register-volatility-and-preservation"></a>Zarejestruj zmienność i konserwacji

W poniższej tabeli opisano, jak każdy rejestr jest używany dla wywołań funkcji:

||||
|-|-|-|
|Rejestruj|Stan|Zastosowanie|
|RAX|Volatile|Zwracana wartość rejestru|
|RCX|Volatile|Pierwszy argument liczby całkowitej|
|RDX|Volatile|Drugi argument liczby całkowitej|
|R8|Volatile|Trzeci argument liczby całkowitej|
|R9|Volatile|Czwarty argument liczby całkowitej|
|R10:R11|Volatile|Muszą być chronione, zgodnie z potrzebami przez obiekt wywołujący; używane w instrukcjach syscall/sysret|
|R12:R15|Nieulotnej|Muszą być chronione przez wywoływanego|
|RDI|Nieulotnej|Muszą być chronione przez wywoływanego|
|RSI|Nieulotnej|Muszą być chronione przez wywoływanego|
|RBX|Nieulotnej|Muszą być chronione przez wywoływanego|
|RBP|Nieulotnej|Może być używana jako wskaźnik ramki; muszą być chronione przez wywoływanego|
|RSP|Nieulotnej|Wskaźnik stosu|
|XMM0, YMM0|Volatile|Pierwszy argument FP; pierwszy argument typu wektor podczas `__vectorcall` jest używany|
|XMM1, YMM1|Volatile|Drugi argument FP; drugi argument Typ wektora podczas `__vectorcall` jest używany|
|XMM2, YMM2|Volatile|Trzeci argument FP; trzeci argument Typ wektora podczas `__vectorcall` jest używany|
|XMM3, YMM3|Volatile|Czwarty argument FP; czwarty argument Typ wektora podczas `__vectorcall` jest używany|
|XMM4, YMM4|Volatile|Muszą być chronione, zgodnie z potrzebami przez obiekt wywołujący; piąty argument Typ wektora podczas `__vectorcall` jest używany|
|XMM5, YMM5|Volatile|Muszą być chronione, zgodnie z potrzebami przez obiekt wywołujący; szósty argument Typ wektora podczas `__vectorcall` jest używany|
|XMM6:XMM15, YMM6:YMM15|Nieulotnej (XMM) Volatile (górnej połowie YMM)|Muszą zostać zachowane przez obiekt wywoływany. Musi zostać zachowane rejestrach YMM, zgodnie z potrzebami przez obiekt wywołujący.|

Zamykania funkcji, wejście funkcji do wywołania biblioteki wykonawczej C i wywołań systemu Windows, Flaga kierunku w Procesorze flags, rejestrze powinien zostać wyczyszczone.

## <a name="stack-usage"></a>Wykorzystanie stosu

Aby uzyskać szczegółowe informacje dotyczące alokacji stosu, wyrównania i typy funkcji oraz ramki stosu w x64, zobacz [x64 stosu użycia](stack-usage.md).

## <a name="prolog-and-epilog"></a>Prolog i epilog

Każdej funkcji, która przydziela miejsce stosu, wywołuje inne funkcje, zapisuje nieulotnej rejestrów lub korzysta z obsługi wyjątków, musi mieć prologu, na których limity adresów są opisane w dane odwinięcia skojarzonych z odpowiedniej funkcji spisu i epilogs w Każdy przycisk Zakończ, aby funkcja. Aby uzyskać szczegółowe informacje na temat wymaganych prologu i epilogu na x64, zobacz [x64 prologu i epilogu](prolog-and-epilog.md).

## <a name="x64-exception-handling"></a>x64 obsługi wyjątków

Aby uzyskać informacje na temat Konwencji i struktur danych używaną do zaimplementowania strukturalna Obsługa wyjątków i zachowanie w x64 obsługi wyjątków C++, zobacz [x64 wyjątków](exception-handling-x64.md).

## <a name="intrinsics-and-inline-assembly"></a>Funkcje wewnętrzne i wbudowany zestaw

Jednym z ograniczeń x64 kompilatora ma nie obsługują asemblera wbudowanego. Oznacza to, że funkcji nie można zapisać w C lub C++, albo musi być zapisywane jako procedury lub funkcji wewnętrznych obsługiwanych przez kompilator. Niektóre funkcje są wrażliwe na wydajność, a inne nie. Funkcje wrażliwego na wydajność, powinny zostać wdrożone jako funkcje wewnętrzne.

Funkcje wewnętrzne, obsługiwane przez kompilator są opisane w [funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md).

## <a name="image-format"></a>Format obrazu

X64 format obrazu pliku wykonywalnego jest je typu PE32 +. Obrazy wykonywalne (plików dll i exe) są ograniczone do maksymalnie 2 GB, więc względne adresowanie z 32-bitowe przesunięcie może służyć do danych obraz statyczny adres. Te dane obejmują tabeli adresów importowania, stałe typu string, statycznych danych globalnych i tak dalej.

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)

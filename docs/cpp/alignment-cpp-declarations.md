---
title: Wyrównanie
description: Sposób wyrównania danych w nowoczesnej C++.
ms.date: 12/11/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: 13f09366501de2482b8ae9ea430898d6c32134c2
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443666"
---
# <a name="alignment"></a>Wyrównanie

Jedną z funkcji niskiego poziomu systemu C++ jest możliwość określania precyzyjnego wyrównania obiektów w pamięci w celu maksymalnego wykorzystania konkretnej architektury sprzętu. Domyślnie kompilator wyrównuje elementy członkowskie klasy i struktury według ich wartości rozmiaru: `bool` i `char` na granicach 1-bajtowych, `short` na granicach 2-bajtowych, `int`, `long`i `float` na granicach 4-bajtowych, a `long long`, `double`i `long double` przy 8-bajtowych granicach. 

W większości scenariuszy nigdy nie trzeba być wyrównaniu, ponieważ domyślne wyrównanie jest już optymalne. W niektórych przypadkach można jednak uzyskać znaczące ulepszenia wydajności lub oszczędności pamięci, określając niestandardowe wyrównanie struktur danych. Przed uruchomieniem programu Visual Studio 2015 można użyć słów kluczowych określonych przez firmę Microsoft `__alignof` i `declspec(alignas)`, aby określić wyrównanie większe niż domyślne. Począwszy od programu Visual Studio 2015 należy używać standardowych słów kluczowych języka C++ 11 **alignof** i **alignas** w celu uzyskania maksymalnej przenośności kodu. Nowe słowa kluczowe działają w taki sam sposób, jak w przypadku rozszerzeń specyficznych dla firmy Microsoft. Dokumentacja tych rozszerzeń dotyczy również nowych słów kluczowych. Aby uzyskać więcej informacji, zobacz [__Alignof operatora](../cpp/alignof-operator.md) i [align](../cpp/align-cpp.md). Standard nie określa zachowania pakowania w przypadku granic mniejszych niż domyślne ustawienia kompilatora dla platformy docelowej, dlatego w takim przypadku nadal trzeba używać pakietu Microsoft #pragma Pack. [pack](../preprocessor/pack.md) C++

Użyj [klasy aligned_storage](../standard-library/aligned-storage-class.md) do przydzielania pamięci struktur danych z wyrównaniami niestandardowymi. [Klasa aligned_union](../standard-library/aligned-union-class.md) służy do określania wyrównania dla Unii z nieprostymi konstruktorami lub destruktorami.

## <a name="alignment-and-memory-addresses"></a>Wyrównania i adresy pamięci

Wyrównanie jest właściwością adresu pamięci wyrażoną jako adres liczbowy modulo potęgi 2. Na przykład adres 0x0001103F modulo 4 to 3. Ten adres jest określany jako wyrównany do 4N + 3, gdzie 4 wskazuje wybraną moc 2. Wyrównanie adresu zależy od wybranej potęgi 2. Ten sam adres modulo 8 to 7. Adres jest określany jako wyrównany do X, jeśli jego wyrównanie jest równe Xn + 0.

Procesor CPU wykonuje instrukcje, które działają na danych przechowywanych w pamięci. Dane są identyfikowane przez ich adresy w pamięci. Pojedynczy Datum ma również rozmiar. Wywoływana jest podstawa firmy w sposób *naturalny wyrównany* , jeśli jej adres jest wyrównany do jego rozmiaru. Jest on wywoływany jako *niewyrównany* w przeciwnym razie. Na przykład 8-bajtowa Jednostka wymiarowa zmiennoprzecinkowa jest w sposób naturalny wyrównany, jeśli adres używany do identyfikacji jest wyrównania 8-bajtowego.

## <a name="compiler-handling-of-data-alignment"></a>Obsługa wyrównania danych przez kompilator

Kompilatory podejmują próbę wykonania alokacji danych w sposób uniemożliwiający niezgodność danych.

W przypadku prostych typów danych kompilator przypisuje adresy, które są wielokrotnością rozmiaru w bajtach typu danych. Na przykład kompilator przypisuje adresy do zmiennych typu `long`, które są wielokrotnościami 4, ustawiając 2 ostatnie bity adresu na zero.

Kompilator tworzy również struktury w sposób, który naturalnie wyrównuje każdy element struktury. Rozważmy strukturę `struct x_` w poniższym przykładzie kodu:

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} bar[3];
```

Kompilator konsoluje tę strukturę w celu wymuszenia wyrównania w sposób naturalny.

Poniższy przykład kodu pokazuje, jak kompilator umieszcza uzupełnioną strukturę w pamięci:

```cpp
// Shows the actual memory layout
struct x_
{
   char a;            // 1 byte
   char _pad0[3];     // padding to put 'b' on 4-byte boundary
   int b;            // 4 bytes
   short c;          // 2 bytes
   char d;           // 1 byte
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4
} bar[3];
```

Obie deklaracje zwracają `sizeof(struct x_)` jako 12 bajtów.

Druga deklaracja zawiera dwa elementy uzupełniające:

1. `char _pad0[3]`, aby wyrównać element członkowski `int b` na granicy 4-bajtowej.

1. `char _pad1[1]`, aby wyrównać elementy tablicy struktury `struct _x bar[3];` na granicy czterech bajtów.

Uzupełnienie wyrównuje elementy `bar[3]` w sposób, który umożliwia dostęp naturalny.

Poniższy przykład kodu przedstawia układ tablicy `bar[3]`:

```Output
adr offset   element
------   -------
0x0000   char a;         // bar[0]
0x0001   char pad0[3];
0x0004   int b;
0x0008   short c;
0x000a   char d;
0x000b   char _pad1[1];

0x000c   char a;         // bar[1]
0x000d   char _pad0[3];
0x0010   int b;
0x0014   short c;
0x0016   char d;
0x0017   char _pad1[1];

0x0018   char a;         // bar[2]
0x0019   char _pad0[3];
0x001c   int b;
0x0020   short c;
0x0022   char d;
0x0023   char _pad1[1];
```

## <a name="alignof-and-alignas"></a>alignof i alignas

Specyfikator typu **alignas** to przenośny, C++ standardowy sposób określania niestandardowego wyrównania zmiennych i typów zdefiniowanych przez użytkownika. Operator **alignof** jest podobnie jak standardowy, przenośny sposób uzyskania wyrównania określonego typu lub zmiennej.

## <a name="example"></a>Przykład

Można użyć **alignas** na klasy, struktury lub Unii lub poszczególnych członków. Gdy napotkanych jest wiele specyfikatorów **alignas** , kompilator wybierze najstrictiej jeden (drugi z największą wartością).

```cpp
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar
{
    int i;       // 4 bytes
    int n;      // 4 bytes
    alignas(4) char arr[3];
    short s;          // 2 bytes
};

int main()
{
    std::cout << alignof(Bar) << std::endl; // output: 16
}
```

## <a name="see-also"></a>Zobacz też

[Wyrównanie struktury danych](https://en.wikipedia.org/wiki/Data_structure_alignment)

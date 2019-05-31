---
title: Wyrównanie (deklaracje języka C++)
description: Jak wyrównanie danych została określona w nowoczesnym C++.
ms.date: 05/30/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: b6e03ac2b89624a0eb6602183d4ff4bf8b518f8d
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450773"
---
# <a name="alignment-c-declarations"></a>Wyrównanie (deklaracje języka C++)

Jedną z niższego poziomu funkcji języka C++ jest możliwość określenia dokładne dostosowanie obiektów w pamięci, aby w maksymalnym wykorzystaniu architektury określonego sprzętu. Domyślnie kompilator wyrównywany klasy i struktury elementów członkowskich w ich wartość rozmiaru: `bool` i `char` przy 1-bajtowych granicach `short` przy 2-bajtowych granicach `int`, `long`, i `float` na 4-bajtowych granicach, a `long long`, `double`, i `long double` na 8-bajtowych granicach. W większości przypadków nie trzeba wiedzieć z wyrównaniem, ponieważ jest już optymalne domyślne wyrównanie. W niektórych przypadkach jednak można osiągnąć znaczne ulepszenia wydajności i oszczędności pamięci, określając niestandardowy Wyrównanie struktury danych użytkownika. Przed Visual Studio 2015 można użyć słowa kluczowe specyficzne dla firmy Microsoft `__alignof` i `declspec(alignas)` do określenia wyrównania, większa niż wartość domyślna. Uruchamianie programu Visual Studio 2015 należy używać języka C ++ 11 standardowe słowa kluczowe [alignof i alignas](../cpp/alignof-and-alignas-cpp.md) przenośności maksymalna kodu. Nowych słów kluczowych zachowują się w taki sam sposób kulisy jako rozszerzenia specyficzne dla firmy Microsoft. W dokumentacji dotyczącej te rozszerzenia dotyczą również nowych słów kluczowych. Aby uzyskać więcej informacji, zobacz [__alignof Operator](../cpp/alignof-operator.md) i [wyrównać](../cpp/align-cpp.md). C++ Standard nie określa zachowanie pakowania dla wyrównania w granicach mniejszy niż domyślna wartość kompilatora dla platformy docelowej, więc nadal musisz korzystać z usługi Microsoft #pragma [pakiet](../preprocessor/pack.md) w takiej sytuacji.

Użyj [klasy aligned_storage](../standard-library/aligned-storage-class.md) dla alokacji pamięci struktury danych niestandardowych wyrównania. [Klasy aligned_union](../standard-library/aligned-union-class.md) jest określanie wyrównania Unii z nietrywialnymi konstruktorów i destruktorów.

## <a name="about-alignment"></a>Temat wyrównania

Wyrównanie jest właściwością adres pamięci, wyrażone jako adres numeryczny modulo potęgą liczby 2. Na przykład adres 0x0001103F modulo 4 to 3. Ten adres jest nazywany zostanie wyrównany do 4 n + 3, gdzie 4 oznacza wybranym potęgą liczby 2. Wyrównanie adres zależy od wybranego potęgą liczby 2. Ten sam adres modulo 8 to 7. Adres jest nazywany wyrównane do X, jeśli jego wyrównania jest Xn + 0.

Procesory CPU wykonać instrukcje, które działają na danych przechowywanych w pamięci. Dane są identyfikowane przez ich adresy w pamięci. Pojedynczy datum również ma rozmiar. Nazywamy datum *naturalnie wyrównane* Jeśli adres jest wyrównany do jej rozmiaru. Jest on nazywany *niewyrównane* inaczej. Na przykład jeśli adres używany do identyfikowania ma 8-bajtowe wyrównanie datum zmiennoprzecinkowego 8-bajtowych jest wyrównany naturalnie.

## <a name="compiler-handling-of-data-alignment"></a>Obsługa kompilatora Wyrównywanie danych

Kompilatory nawiązania alokacji danych w taki sposób, że Niedopasowanie typów danych.

Proste typy danych kompilator przypisuje adresy, które stanowią wielokrotność rozmiar w bajtach typu danych. Na przykład, kompilator przypisuje adresy zmiennych typu `long` , które są wielokrotnością 4, ustawienia dolnej 2 bity adresu do zera.

Kompilator dopełnia również struktury w sposób naturalny pasującą do każdego elementu struktury. Należy wziąć pod uwagę struktury `struct x_` w poniższym przykładzie kodu:

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} MyStruct;
```

Kompilator dopełnia tej struktury, aby wymusić wyrównanie naturalnie.

Poniższy przykład kodu pokazuje, jak kompilator umieszcza wypełniony struktury w pamięci:

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
}
```

1. Obie deklaracje zwracają `sizeof(struct x_)` jako 12-bajtowy.

1. Deklaracja drugi zawiera dwa elementy dopełnienie:

1. `char _pad0[3]` Aby wyrównać `int b` elementu członkowskiego w granicach 4-bajtowych

1. `char _pad1[1]` Aby wyrównać elementów tablicy struktury `struct _x bar[3];`

1. Dopełnienie wyrównuje elementy `bar[3]` w sposób umożliwiający dostęp do naturalnym.

Poniższy kod przedstawia przykład `bar[3]` układ tablicy:

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

## <a name="see-also"></a>Zobacz także

[Wyrównanie struktury danych](https://en.wikipedia.org/wiki/Data_structure_alignment)

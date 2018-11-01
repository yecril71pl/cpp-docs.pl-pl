---
title: Wyrównanie (deklaracje języka C++)
ms.date: 11/04/2016
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: 644a1f5d476fc35093c99b26e2d0685ad041b0af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563114"
---
# <a name="alignment-c-declarations"></a>Wyrównanie (deklaracje języka C++)

Jedną z niższego poziomu funkcji języka C++ jest możliwość określenia dokładne dostosowanie obiektów w pamięci, aby w maksymalnym wykorzystaniu architektury określonego sprzętu. Domyślnie kompilator wyrównywany klasy i struktury elementów członkowskich w ich wartość rozmiaru: wartość logiczna i char są wyrównane na granicach jednobajtowego krótki na dwóch bajtów int na cztery bajty long long, double a double na 8 bajtów. W większości przypadków nie trzeba być zaniepokojona wyrównanie, ponieważ domyślne wyrównanie już jest optymalna. W niektórych przypadkach jednak może osiągnąć znaczne ulepszenia wydajności i oszczędności pamięci, określając niestandardowy Wyrównanie struktury danych użytkownika. Przed Visual Studio 2015 można Użyj __alignof słowa kluczowe specyficzne dla firmy Microsoft i declspec(alignas), aby określić wyrównanie, które są większe niż domyślna. Uruchamianie programu Visual Studio 2015 należy używać języka C ++ 11 standardowe słowa kluczowe [alignof i alignas](../cpp/alignof-and-alignas-cpp.md) przenośności maksymalna kodu. Nowych słów kluczowych zachowują się w taki sam sposób kulisy jako rozszerzenia specyficzne dla firmy Microsoft i dokumentacji dotyczącej tych rozszerzeń ma również zastosowanie do nowych słów kluczowych. Zobacz [__alignof Operator](../cpp/alignof-operator.md) i [wyrównać](../cpp/align-cpp.md) Aby uzyskać więcej informacji. C++ standard nie określa zachowanie pakowania wyrównywanie w granicach mniejszy niż domyślna wartość kompilatora dla platformy docelowej, dlatego musisz nadal korzystać z usługi Microsoft #pragma [pakiet](../preprocessor/pack.md) w takiej sytuacji.

Standardowej biblioteki języka C++ udostępnia [aligned_storage, klasa](../standard-library/aligned-storage-class.md) do przydzielania pamięci dla struktur danych przy użyciu niestandardowych wyrównanie i [aligned_union, klasa](../standard-library/aligned-union-class.md) do określenia wyrównania Unii z nietrywialnymi konstruktorów i destruktorów.

## <a name="about-alignment"></a>Temat wyrównania

Wyrównanie jest właściwością adres pamięci, wyrażone jako adres numeryczny modulo potęgą liczby 2. Na przykład adres 0x0001103F modulo 4 to 3; Ten adres jest nazywany zostanie wyrównany do 4 n + 3, gdzie 4 oznacza wybranym potęgą liczby 2. Wyrównanie adres zależy od wybranego potęgą liczby dwa. Ten sam adres modulo 8 to 7. Adres jest nazywany wyrównane do X, jeśli jego wyrównania jest Xn + 0.

Procesory CPU wykonania instrukcji, które działają na danych przechowywanych w pamięci, a dane są identyfikowane przez ich adresy w pamięci. Oprócz jego adres pojedynczego datum ma rozmiar. Datum jest nazywana naturalnie wyrównane, jeśli jego adres jest wyrównany do jej rozmiaru i niewyrównane inaczej. Na przykład jeśli adres używany do identyfikowania pokrywa się z 8 datum zmiennoprzecinkowego 8-bajtowych jest wyrównany naturalnie.

Obsługa kompilatora danych alignmentDevice kompilatory próbę przydzielenia danych w taki sposób, że Niedopasowanie typów danych.

Proste typy danych kompilator przypisuje adresy, które stanowią wielokrotność rozmiar w bajtach typu danych. W efekcie kompilator przypisuje adresy zmiennych typu long, które stanowią wielokrotność czterech, ustawienie dwa bity adres na zero.

Ponadto kompilator dopełnia struktury w sposób naturalny pasującą do każdego elementu struktury. Należy wziąć pod uwagę x_ struktury struktury w poniższym przykładzie kodu:

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

Poniższy przykład kodu pokazuje, jak kompilator umieszcza wypełniony struktury w pamięci: kopiowanie

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

1. Obie deklaracje zwrócić sizeof(struct x_) jako 12-bajtowy.

1. Deklaracja drugi zawiera dwa elementy dopełnienie:

1. CHAR _pad0 [3], aby wyrównać element członkowski b int na granicy czwartego bajtu

1. CHAR _pad1 [1], aby wyrównać elementów tablicy _x struktury struktury paska [3];

1. Dopełnienie wyrównuje elementy paska [3] w sposób umożliwiający dostęp do naturalnym.

Poniższy przykład kodu pokazuje pasek układ tablicy [3]:

```
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

[Wyrównanie struktury danych](http://en.wikipedia.org/wiki/Data_structure_alignment)
---
title: "Wyrównanie (deklaracje języka C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a1326a0813e0d4092a7033e3e995336ac1f29056
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="alignment-c-declarations"></a>Wyrównanie (deklaracje języka C++)
Jedną z niskiego poziomu funkcji C++ jest możliwość określenia dokładne dostosowanie obiektów w pamięci, aby wykorzystać maksymalną architektury sprzętu. Domyślnie kompilator wyrównuje klasy i struktury elementów członkowskich na ich wartość rozmiaru: bool i char są wyrównane co granice jednego bajtu, short na dwubajtowo, int na 4 bajty, long double i long double 8 bajtów. W większości przypadków nie trzeba być związane z wyrównania, ponieważ domyślne wyrównanie już jest optymalna. W niektórych przypadkach jednak można osiągnąć znaczną poprawę wydajności lub zużycie pamięci, określając niestandardowy Wyrównanie struktury danych użytkownika. Przed Visual Studio 2015 umożliwiają __alignof słowa kluczowe specyficzne dla firmy Microsoft i declspec(alignas) określ wyrównanie większe niż wartość domyślna. Poczynając od programu Visual Studio 2015 należy używać języka C ++ 11 standardowe słowa kluczowe [alignof i alignas](../cpp/alignof-and-alignas-cpp.md) przenośności maksymalną kodu. Zachowanie nowych słów kluczowych w taki sam sposób kulisy jako rozszerzenia specyficzne dla firmy Microsoft, a w dokumentacji tych rozszerzeń ma również zastosowanie do nowych słów kluczowych. Zobacz [__alignof Operator](../cpp/alignof-operator.md) i [Dopasuj](../cpp/align-cpp.md) Aby uzyskać więcej informacji. C++ standard nie określa zachowanie pakowania wyrównywania na granicach mniejszą niż domyślne kompilatora dla platformy docelowej, dzięki czemu nadal trzeba korzystać z usługi Microsoft #pragma [pakietu](../preprocessor/pack.md) w takiej sytuacji.  
  
 Udostępnia standardowa biblioteka C++ [aligned_storage — klasa](../standard-library/aligned-storage-class.md) alokacji pamięci dla struktur danych z niestandardowych wyrównanie i [aligned_union — klasa](../standard-library/aligned-union-class.md) służący do określania wyrównanie unie z nieuproszczony konstruktorów ani destruktorów.  
  
## <a name="about-alignment"></a>Wyrównanie — informacje  
 Wyrównanie jest właściwością adres pamięci, wyrażone jako adres numeryczny modulo potęgą liczby 2. Na przykład adres 0x0001103F modulo 4 jest 3; Ten adres jest nazywany wyrównać je do 4 n + 3, w którym 4 oznacza wybrane potęgą liczby 2. Wyrównanie adres zależy od wybranej potęgą liczby dwa. Ten sam adres modulo 8 to 7. Adres jest nazywany wyrównywana X, jeśli jego wyrównania jest Xn + 0.  
  
 Procesory wykonania instrukcji, które działają na dane przechowywane w pamięci, a dane są identyfikowane przez adresy w pamięci. Oprócz jego adres pojedynczego elementu danych ma rozmiar. Datum jest nazywana naturalnie wyrównane, jeśli jego adres jest wyrównany do jego rozmiaru i niewyrównanych w przeciwnym razie wartość. Na przykład jeśli adres używany do identyfikowania jest wyrównane do 8 podstawy wymiarowej 8-bajtowych liczb zmiennoprzecinkowych jest wyrównany naturalny.  
  
 Obsługa kompilatora próby kompilatory alignmentDevice danych można przydzielić dane w taki sposób, który uniemożliwia niespójność danych.  
  
 Proste typy danych kompilator przypisuje adresy, które są wielokrotności rozmiar w bajtach typu danych. W związku z tym kompilator przypisywania adresów na zmiennych typu long wielokrotności 4, ustawienia dwa bity adres od zera.  
  
 Ponadto kompilator dopełnia struktury w sposób naturalny wyrównuje poszczególne elementy struktury. Należy wziąć pod uwagę x_ struktury struktury w poniższym przykładzie kodu:  
  
```  
struct x_  
{  
   char a;     // 1 byte  
   int b;      // 4 bytes  
   short c;    // 2 bytes  
   char d;     // 1 byte  
} MyStruct;  
  
```  
  
 Kompilator dopełnia tej struktury naturalnie wymusić wyrównania.  
  
 Poniższy przykład kodu pokazuje, jak kompilator umieszcza wypełniony struktury w pamięci: kopiowanie  
  
```  
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
  
1.  Obie deklaracje zwrócić sizeof(struct x_) 12 bajtów.  
  
2.  Druga deklaracja zawiera dwa elementy uzupełnienie:  
  
3.  CHAR — _pad0 [3], aby wyrównać element członkowski b int w granicach 4 bajtowych  
  
4.  CHAR — _pad1 [1], aby wyrównać elementy tablicy _x struktury struktury paska [3];  
  
5.  Dopełnienie wyrównuje elementy paska [3] w sposób umożliwiający dostęp do fizycznych.  
  
 Poniższy przykład kodu pokazuje pasek układu tablicy [3]:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Wyrównanie struktury danych](http://en.wikipedia.org/wiki/Data_structure_alignment)
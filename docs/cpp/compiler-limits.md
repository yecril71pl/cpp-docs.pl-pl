---
title: Limity kompilatora
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9e61cae1638c87f03b6fa775552408961bde6859
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189584"
---
# <a name="compiler-limits"></a>Limity kompilatora

C++ Standard zaleca limity dla różnych konstrukcji językowych. Poniżej znajduje się lista przypadków, w których kompilator firmy C++ Microsoft nie implementuje zalecanych limitów. Pierwszy numer to limit ustanowiony w standardzie ISO C++ 11 (INCITS/ISO/IEC 14882-2011 [2012], załącznik B), a druga liczba to limit zaimplementowany przez kompilator firmy Microsoft: C++

- Zagnieżdżanie poziomów instrukcji złożonych, struktur kontroli iteracji i struktur kontroli wyboru — C++ standard: 256, Microsoft C++ Compiler: zależy od kombinacji zagnieżdżonych instrukcji, ale ogólnie od 100 do 110.

- Parametry w jednej definicji makra — C++ standardowe: 256, Microsoft C++ Compiler: 127.

- Argumenty w jednym wywołaniu makra — C++ standard: 256, Microsoft C++ Compiler 127.

- Znaki w postaci literału ciągu znaków lub szeroki literał ciągu (po łączeniu) — C++ standard: 65536, Microsoft C++ Compiler: 65535 jednobajtowe znaki, łącznie z terminatorem wartości null i 32767 znaki dwubajtowe, w tym terminator o wartości null.

- Poziomy zagnieżdżonej klasy, struktury lub definicji Unii w jednym `struct-declaration-list` — C++ standard: 256, kompilator firmy Microsoft C++ : 16.

- Inicjatory elementów członkowskich w definicji konstruktora — C++ standard: 6144, kompilator C++ firmy Microsoft: co najmniej 6144.

- Kwalifikacje zakresu jednego identyfikatora — C++ standard: 256, Microsoft C++ Compiler: 127.

- Zagnieżdżone **specyfikacje** zewnętrzne — C++ standardowa: 1024, Microsoft C++ Compiler: 9 (nie zliczanie niejawnej specyfikacji **extern** w zakresie globalnym lub 10, jeśli zliczasz niejawną specyfikację **extern** w zakresie globalnym).

- Argumenty szablonu w deklaracji szablonu — C++ standard: 1024, Microsoft C++ Compiler: 2046.

## <a name="see-also"></a>Zobacz też

[Niestandardowe zachowanie](../cpp/nonstandard-behavior.md)

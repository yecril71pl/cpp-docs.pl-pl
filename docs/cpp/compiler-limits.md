---
title: Limity kompilatora
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: e0e2381d88c727466b06a97c72826d2d5e15a87b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233772"
---
# <a name="compiler-limits"></a>Limity kompilatora

Standard C++ zaleca limity dla różnych konstrukcji językowych. Poniżej znajduje się lista przypadków, w których kompilator języka Microsoft C++ nie implementuje zalecanych limitów. Pierwszy numer jest limitem ustalonym w standardzie ISO C++ 11 (INCITS/ISO/IEC 14882-2011 [2012], załącznik B), a druga liczba jest limitem zaimplementowanym przez kompilator języka Microsoft C++:

- Zagnieżdżanie poziomów instrukcji złożonych, struktur kontroli iteracji i struktur kontroli wyboru — C++ standard: 256, kompilator języka Microsoft C++: zależy od kombinacji zagnieżdżonych instrukcji, ale ogólnie od 100 do 110.

- Parametry w jednej definicji makra — C++ standard: 256, kompilator Microsoft C++: 127.

- Argumenty w jednym wywołaniu makra — standard C++: 256, kompilator Microsoft C++ 127.

- Znaki w postaci literału ciągu znaków lub szeroki literał ciągu (po łączeniu) — C++ standard: 65536, kompilator Microsoft C++: 65535 jednobajtowe znaki, w tym terminator o wartości NULL i 32767 znaki dwubajtowe, w tym terminator o wartości NULL.

- Poziomy zagnieżdżonej klasy, struktury lub definicji Unii w jednym `struct-declaration-list` standardzie c++: 256, kompilator języka Microsoft C++: 16.

- Inicjatory elementów członkowskich w definicji konstruktora — standard C++: 6144, kompilator Microsoft C++: co najmniej 6144.

- Kwalifikacje zakresu jednego identyfikatora — standard C++: 256, kompilator Microsoft C++: 127.

- **`extern`** Specyfikacje zagnieżdżone — C++ standard: 1024, kompilator języka Microsoft C++: 9 (nie zliczanie niejawnej **`extern`** specyfikacji w zakresie globalnym lub 10, jeśli zliczasz niejawną **`extern`** specyfikację w zakresie globalnym).

- Argumenty szablonu w deklaracji szablonu — C++ standard: 1024, kompilator Microsoft C++: 2046.

## <a name="see-also"></a>Zobacz także

[Niestandardowe zachowanie](../cpp/nonstandard-behavior.md)

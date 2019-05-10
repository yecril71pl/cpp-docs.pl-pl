---
title: Limity kompilatora
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: 9663da06c97886ef1cd20ca2928944795b39dc18
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222193"
---
# <a name="compiler-limits"></a>Limity kompilatora

C++ standard zaleca limity dla różnych konstrukcji językowych. Poniżej przedstawiono listę przypadki gdzie Microsoft C++ kompilatora nie implementuje zalecane limity. Pierwsza liczba jest to limit, który jest określana w ISO C++ standardem 11 (Stowarzyszenie INCITS/ISO/IEC 14882 2011 [2012], w załączniku B), a druga liczba jest limit implementowany przez Microsoft C++ kompilatora:

- Poziomów zagnieżdżenia instrukcje złożone, struktur sterujących iteracji i struktury sterujące wybór - C++ standardowe: 256, Microsoft C++ kompilatora: zależy od kombinacji instrukcji, które są zagnieżdżone, ale zazwyczaj zakresu od 100 do 110.

- Parametrów w definicji makra jednego - C++ standardowe: 256, Microsoft C++ compiler: 127.

- Argumenty w wywołaniu makra jednego - C++ standardowe: 256, Microsoft C++ compiler 127.

- Znaki w znaku ciągu literału lub szerokiego literału ciągu znaków (po łączenie) - C++ standardowe: 65536, Microsoft C++ compiler: 65535 znaków jednobajtowych, w tym terminator o wartości NULL i 32767 znaków dwubajtowych, w tym terminator o wartości NULL.

- Poziomów zagnieżdżonych klasy, struktury lub union definicje w jednym `struct-declaration-list` - C++ standardowe: 256, Microsoft C++ compiler: 16.

- Inicjatorów składowych w Konstruktorze definicji - C++ standardowe: Microsoft 6144, C++ kompilatora: co najmniej 6144.

- Zakres kwalifikacji jeden identyfikator - C++ standardowe: 256, Microsoft C++ compiler: 127.

- Zagnieżdżone **extern** specyfikacje - C++ standardowe: 1024, Microsoft C++ compiler: 9 (nie licząc zamykającego niejawny **extern** specyfikacji w zakresie globalnym lub 10, jeśli liczyć niejawny **extern** specyfikacji w zakresie globalnym.

- Argumenty szablonu w deklaracji szablonu - C++ standardowe: 1024, Microsoft C++ compiler: 2046.

## <a name="see-also"></a>Zobacz także

[Niestandardowe zachowanie](../cpp/nonstandard-behavior.md)
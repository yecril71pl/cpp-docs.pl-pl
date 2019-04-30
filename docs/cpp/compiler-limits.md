---
title: Limity kompilatora
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
ms.openlocfilehash: a0c6041d326982dc9807355733cf714dcfa62ca8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399164"
---
# <a name="compiler-limits"></a>Limity kompilatora

C++ standard zaleca limity dla różnych konstrukcji językowych. Oto lista przypadków, w którym kompilator języka Visual C++ nie implementuje zalecane limity. Pierwsza liczba jest to limit, który jest określana w ISO C++ standardem 11 (Stowarzyszenie INCITS/ISO/IEC 14882 2011 [2012], w załączniku B), a druga liczba jest limit implementowane przez wizualizację C++:

- Poziomów zagnieżdżenia instrukcje złożone, struktur sterujących iteracji i struktury sterujące wybór - C++ standardowe: 256, visual C++ kompilatora: zależy od kombinacji instrukcji, które są zagnieżdżone, ale zazwyczaj zakresu od 100 do 110.

- Parametrów w definicji makra jednego - C++ standardowe: 256, Visual C++ compiler: 127.

- Argumenty w wywołaniu makra jednego - C++ standardowe: 256, Visual C++ compiler 127.

- Znaki w znaku ciągu literału lub szerokiego literału ciągu znaków (po łączenie) - C++ standardowe: 65536, visual C++ kompilatora: 65535 znaków jednobajtowych, w tym terminator o wartości NULL i 32767 znaków dwubajtowych, w tym terminator o wartości NULL.

- Poziomów zagnieżdżonych klasy, struktury lub union definicje w jednym `struct-declaration-list` - C++ standardowe: 256, Visual C++ compiler: 16.

- Inicjatorów składowych w Konstruktorze definicji - C++ standardowe: Visual 6144, C++ kompilatora: co najmniej 6144.

- Zakres kwalifikacji jeden identyfikator - C++ standardowe: 256, Visual C++ compiler: 127.

- Zagnieżdżone **extern** specyfikacje - C++ standardowe: 1024, visual C++ kompilatora: 9 (nie licząc zamykającego niejawny **extern** specyfikacji w zakresie globalnym lub 10, jeśli liczyć niejawny **extern** specyfikacji w zakresie globalnym.

- Argumenty szablonu w deklaracji szablonu - C++ standardowe: 1024, visual C++ kompilatora: 2046.

## <a name="see-also"></a>Zobacz także

[Niestandardowe zachowanie](../cpp/nonstandard-behavior.md)
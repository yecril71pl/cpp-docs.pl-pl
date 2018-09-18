---
title: Limity kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76b08ab88ce5487485c8b8872488c0cf784ad2c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093548"
---
# <a name="compiler-limits"></a>Limity kompilatora

C++ standard zaleca limity dla różnych konstrukcji językowych. Oto lista przypadków, w którym kompilator języka Visual C++ nie implementuje zalecane limity. Pierwsza liczba jest to limit, który jest określana w ISO standardzie c ++ 11 (Stowarzyszenie INCITS/ISO/IEC 14882 2011 [2012], w załączniku B), a druga liczba jest limit implementowaną przez Visual C++:

- Poziomów zagnieżdżenia instrukcje złożone struktury sterujące iteracji i wybór kontrolować struktur — C++ standard: 256, kompilator języka Visual C++: zależy od kombinacji instrukcji, które są zagnieżdżone, ale zazwyczaj zakresu od 100 do 110.

- Parametrów w definicji makra jeden — C++ standard: 256, kompilator języka Visual C++: 127 znaków.

- Argumenty w wywołaniu makra jeden — C++ standard: 256, kompilator języka Visual C++ 127 znaków.

- Znaki w znaku ciągu literału lub szerokiego literału ciągu znaków (po łączenie) — C++ standard: 65536, kompilator języka Visual C++: 65535 znaków jednobajtowych, w tym terminator o wartości NULL i 32767 znaków dwubajtowych, w tym terminator o wartości NULL.

- Poziomów zagnieżdżonych klasy, struktury lub union definicje w jednym `struct-declaration-list` — C++ standard: 256, kompilator języka Visual C++: 16.

- Inicjatorów składowych w Konstruktorze definicji — C++ standard: 6144, kompilator języka Visual C++: co najmniej 6144.

- Zakres kwalifikacji jeden identyfikator — C++ standard: 256, kompilator języka Visual C++: 127 znaków.

- Zagnieżdżone **extern** specyfikacje — C++ standard: 1024, kompilator języka Visual C++: 9 (bez uwzględnienia niejawny **extern** specyfikacji w zakresie globalnym lub 10, jeśli liczyć niejawny **extern**  specyfikacji w zakresie globalnym...

- Argumenty szablonu w deklaracji szablonu — C++ standard: 1024, kompilator języka Visual C++: 2046.

## <a name="see-also"></a>Zobacz także

[Niestandardowe zachowanie](../cpp/nonstandard-behavior.md)
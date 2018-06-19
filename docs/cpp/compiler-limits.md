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
ms.openlocfilehash: bc7cd26add0a46bab8df7669fb6dfb6060b0010e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412140"
---
# <a name="compiler-limits"></a>Limity kompilatora
C++ standard zaleca limity dotyczące konstrukcji języka różne. Poniżej znajduje się lista przypadków, w którym kompilator języka Visual C++ nie implementuje zalecane limity. Pierwsza liczba jest limit, która jest określana w ISO C++ 11 standardowe (INCITS/ISO/IEC 14882 2011 [2012] załącznik B), a druga liczba jest limit implementowane przez Visual C++:  
  
-   Poziomów zagnieżdżenia instrukcje złożone, struktury sterujące iteracji i wybór kontrolowanie struktury — C++ standard: 256, kompilator języka Visual C++: zależy od kombinacji instrukcji, które są zagnieżdżone, ale zazwyczaj w przedziale od 100 do 110.  
  
-   Parametry w definicji makra jeden — C++ standard: 256, kompilator języka Visual C++: 127.  
  
-   Argumentów w wywołaniu makra jeden — C++ standard: 256, kompilator języka Visual C++ 127.  
  
-   Znaki znakiem ciągu literału ciągu literału lub szerokie (po łączenia) - C++ standard: 65536, kompilator języka Visual C++: 65535 znaków jednobajtowych, w tym `null` terminatora i 32767 znaków dwubajtowych, w tym `null` terminator.  
  
-   Poziomów zagnieżdżonych klasy, struktury lub Unii definicje w jednej `struct-declaration-list` — C++ standard: 256, kompilator języka Visual C++: 16.  
  
-   Inicjatorów elementów członkowskich w definicji konstruktora — C++ standard: 6144, kompilator języka Visual C++: co najmniej 6144.  
  
-   Zakres kwalifikacji jeden identyfikator - C++ standard: 256, kompilator języka Visual C++: 127.  
  
-   Zagnieżdżone `extern` specyfikacje — C++ standard: 1024, kompilator języka Visual C++: 9 (bez uwzględnienia niejawne `extern` w zakresie globalnym lub 10, jeśli niejawne liczenia specyfikacja `extern` w zakresie globalnym specyfikacja..  
  
-   Argumenty szablonu w deklaracji szablonu — C++ standard: 1024, kompilator języka Visual C++: 2046.  
  
## <a name="see-also"></a>Zobacz też  
 [Niestandardowe zachowanie](../cpp/nonstandard-behavior.md)
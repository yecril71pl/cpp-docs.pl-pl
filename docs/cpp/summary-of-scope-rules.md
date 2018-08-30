---
title: Podsumowanie reguł zakresu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- class scope [C++], rules
- classes [C++], scope
- class names [C++], scope rules
- names [C++], class
- scope [C++], class names
ms.assetid: 47e26482-0111-466f-b857-598c15d05105
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d58bf1d860bac7328c491164f6aeb77bed19b9cd
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195034"
---
# <a name="summary-of-scope-rules"></a>Podsumowanie reguł zakresu
Użycie nazwy muszą być jednoznaczną w jego zakresie (aż do momentu, w której jest określana przeciążenie). Jeśli nazwa wskazuje funkcję, funkcja musi być jednoznaczną względem numer i typ parametrów. Jeśli nazwa jest jednoznaczna, [dostęp do elementu członkowskiego](../cpp/member-access-control-cpp.md) reguły są stosowane.  
  
## <a name="constructor-initializers"></a>Inicjatory konstruktora  
 Inicjatory konstruktora (opisanego w [Inicjowanie baz i elementów członkowskich](https://msdn.microsoft.com/2f71377e-2b6b-49da-9a26-18e9b40226a1)) są obliczane w zakresie peryferyjnych bloku konstruktora, dla której są określone. W związku z tym mogą używać nazwy parametrów konstruktora.  
  
## <a name="global-names"></a>Nazwy globalne  
 Nazwa obiektu, funkcji lub modułu wyliczającego jest globalna, jeśli zostanie wprowadzone poza żadnych funkcji lub klasy lub poprzedzony globalnego zakresu jednoargumentowej (`::`), a jeśli nie jest używany w połączeniu z dowolną z tych operatorów binarnych:  
  
-   Rozpoznawania zakresu (`::`)  
  
-   Wybór elementów członkowskich dla obiektów i odwołania (**.**)  
  
-   Wybieranie wskaźników do elementów członkowskich (**->**)  
  
## <a name="qualified-names"></a>Kwalifikowane nazwy  
 Nazwy używane z binarnym operatorem rozwiązywania zakresu (`::`) są nazywane „nazwami kwalifikowanymi”. Nazwa określona po binarnym operatorze rozwiązywania zakresu musi być składową klasy określonej po lewej stronie operatora lub składową jej klas podstawowych.  
  
 Nazwy określone po operatorze wyboru składowej (**.** lub **->**) muszą być elementami członkowskimi typu klasy obiektu określonego po lewej stronie operatora lub składowymi jej klas podstawowych. Nazwy określone po prawej stronie operatora wyboru składowej (**->**) mogą być również obiektami innego typu klasy, pod warunkiem, że po lewej stronie **->** jest obiektem klasy i czy klasy definiuje operator przeciążona wybór elementów członkowskich (**->**) który ocenia do wskaźnika do typu innej klasy. (Omówiono bardziej szczegółowo w tym zapisem [dostęp do składowej klasy](../cpp/member-access.md).)  
  
 Kompilator wyszukuje nazwy w następującej kolejności, zatrzymując się, gdy nazwa zostanie znaleziona:  
  
1.  Bieżący blok zakresu, jeśli nazwa jest używana wewnątrz funkcji; w przeciwnym przypadku, zakres globalny.  
  
2.  Na zewnątrz przez każdy otaczający blok zakresu, łącznie z najbardziej zewnętrznym zakresem funkcji (która obejmuje parametry funkcji).  
  
3.  Jeśli nazwa jest używana wewnątrz funkcji składowej, to nazwa jest wyszukiwana w zakresie klasy.  
  
4.  Nazwa jest wyszukiwana w klasach bazowych klasy.  
  
5.  Przeszukiwany jest otaczający, zagnieżdżony zakres klasy (jeśli istnieje) oraz jego klasy podstawowe. Wyszukiwanie jest kontynuowane, dopóki nie zostanie przeszukany najbardziej zewnętrzny, otaczający zakres klasy.  
  
6.  Przeszukiwany jest zakres globalny.  
  
 Jednakże, możesz wykonać następujące modyfikacje kolejności wyszukiwania:  
  
1.  Nazwy poprzedzone operatorem `::` wymuszają rozpoczęcie wyszukiwania od zakresu globalnego.  
  
2.  Nazwy poprzedzone **klasy**, **struktury**, i **Unii** słowa kluczowe wymusić na kompilatorze wyszukiwanie tylko **klasy**,  **Struktura**, lub **Unii** nazwy.  
  
3.  Nazwy po lewej stronie operatora rozpoznawania zakresu (`::`) może być tylko **klasy**, **struktury**, **przestrzeni nazw**, lub **Unii**nazwy.  
  
 Jeśli nazwa odwołuje się do niestatycznego elementu członkowskiego, ale jest używana w statycznej funkcji członkowskiej, to wygenerowany zostanie komunikat o błędzie. Podobnie, jeśli nazwa odwołuje się do dowolnej, niestatycznej składowej w otaczającej klasie, komunikat o błędzie jest generowany ponieważ klasy otaczające nie mają wskaźnika otaczającej klasy **to** wskaźników.  
  
## <a name="function-parameter-names"></a>Nazwy parametrów funkcji  
 Nazwy parametrów funkcji, definicje funkcji są uznawane za w zakresie bloku najbardziej zewnętrznej funkcji. W związku z tym są w lokalnej nazwy i wykraczają poza zakres, gdy funkcja jest został zakończony.  
  
 Nazwy parametrów funkcji w deklaracjach funkcji (prototypy) znajdują się w zakresie lokalnym deklaracji i wykraczają poza zakres na końcu deklaracji.  
  
 Domyślne parametry znajdują się w zakresie parametru, w którym są domyślnie, zgodnie z opisem w dwóch poprzednich akapitach. Jednak mogą nie dostęp do zmiennych lokalnych lub niestatycznych składowych. Domyślne parametry są oceniane w momencie wywołania funkcji, ale są one obliczane w deklaracji funkcji oryginalny zakres. W związku z tym domyślne parametry dla funkcji elementów członkowskich są obliczane zawsze w zakresie klasy.  
  
## <a name="see-also"></a>Zobacz także  
 [Dziedziczenie](../cpp/inheritance-cpp.md)
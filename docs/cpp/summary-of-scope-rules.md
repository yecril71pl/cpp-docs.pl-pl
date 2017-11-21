---
title: "Podsumowanie reguł zakresu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- class scope [C++], rules
- classes [C++], scope
- class names [C++], scope rules
- names [C++], class
- scope [C++], class names
ms.assetid: 47e26482-0111-466f-b857-598c15d05105
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2261f5c2b843f607f8f0906764aee833c6a100f4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="summary-of-scope-rules"></a>Podsumowanie reguł zakresu
Użycie nazwy musi być jednoznaczne w jego zakresie (do punktu, w której jest określana przeładowanie). Jeśli nazwa oznacza funkcję, funkcja musi być jednoznaczne względem liczba i typ parametrów. Jeśli nazwa pozostanie jednoznaczne, [dostęp do elementu członkowskiego](../cpp/member-access-control-cpp.md) reguły są stosowane.  
  
## <a name="constructor-initializers"></a>Inicjatory konstruktora  
 Inicjatory konstruktora (opisany w [Inicjowanie baz i elementów członkowskich](http://msdn.microsoft.com/en-us/2f71377e-2b6b-49da-9a26-18e9b40226a1)) są oceniane w zakresie bloku peryferyjnych konstruktora, dla którego zostały określone. W związku z tym użyciem nazwy parametrów konstruktora.  
  
## <a name="global-names"></a>Nazwy globalne  
 Nazwa obiektu, funkcji lub moduł wyliczający jest globalnych, jeśli jest wprowadzone poza żadnych funkcji lub klasy lub prefiksu określonego przez operator jednoargumentowy globalnego zakresu (`::`), a jeśli nie jest on używany w połączeniu z dowolną z tych operatorów binarnych:  
  
-   Rozpoznawanie zakresów (`::`)  
  
-   Wybór elementu członkowskiego dla obiektów oraz z odwołań (**.**)  
  
-   Wybór elementu członkowskiego dla wskaźników (**->**)  
  
## <a name="qualified-names"></a>Kwalifikowane nazwy  
 Nazwy używane z binarnym operatorem rozwiązywania zakresu (`::`) są nazywane „nazwami kwalifikowanymi”. Nazwa określona po binarnym operatorze rozwiązywania zakresu musi być elementem członkowskim klasy określonej po lewej stronie operatora lub elementem członkowskim jej klas podstawowych.  
  
 Nazwy określone po operatorze wyboru elementu członkowskiego (**.** lub  **->** ) muszą być elementami członkowskimi typu klasy obiektu określonego w lewej strony operatora i członkowie jego klasy podstawowej. Nazwy określone po prawej stronie operatora wyboru elementu członkowskiego (**->**) może być także obiekty innego typu klasy, pod warunkiem, że po lewej stronie  **->**  jest obiektem klasy i Czy tej klasy definiuje operator przeciążone wyboru elementu członkowskiego (**->**) zwraca wskaźnik do innego typu klasy. (Niniejszymi omówiono bardziej szczegółowo w [dostęp do elementu członkowskiego klasy](../cpp/member-access.md).)  
  
 Kompilator wyszukuje nazwy w następującej kolejności, zatrzymując się, gdy nazwa zostanie znaleziona:  
  
1.  Bieżący blok zakresu, jeśli nazwa jest używana wewnątrz funkcji; w przeciwnym przypadku, zakres globalny.  
  
2.  Na zewnątrz za pośrednictwem każdej otaczającym zakresie bloku, w tym zakresie najbardziej zewnętrzną funkcję, (w tym parametry funkcji).  
  
3.  Jeśli nazwa jest używana wewnątrz funkcji członkowskiej, to nazwa jest wyszukiwana w zakresie klasy.  
  
4.  Nazwa jest wyszukiwana w klasa podstawowych klasy.  
  
5.  Przeszukiwany jest otaczający, zagnieżdżony zakres klasy (jeśli istnieje) oraz jego klasy podstawowe. Wyszukiwanie jest kontynuowane, dopóki nie zostanie przeszukany najbardziej zewnętrzny, otaczający zakres klasy.  
  
6.  Przeszukiwany jest zakres globalny.  
  
 Jednakże, możesz wykonać następujące modyfikacje kolejności wyszukiwania:  
  
1.  Nazwy poprzedzone operatorem `::` wymuszają rozpoczęcie wyszukiwania od zakresu globalnego.  
  
2.  Nazwy poprzedzone **klasy**, `struct`, i **Unii** słowa kluczowe wymusić kompilator, aby wyszukać tylko **klasy**, `struct`, lub **Unii**  nazwy.  
  
3.  Nazwy po lewej stronie operatora rozpoznawanie zakresów (`::`) może być tylko **klasy**, `struct`, **przestrzeni nazw**, lub **Unii** nazwy.  
  
 Jeśli nazwa odwołuje się do niestatycznego elementu członkowskiego, ale jest używana w statycznej funkcji członkowskiej, to wygenerowany zostanie komunikat o błędzie. Podobnie, jeśli nazwa odwołuje się do żadnych niestatycznego elementu członkowskiego klasy otaczającej, komunikat o błędzie jest generowany objętego klas nie ma klasy otaczającej **to** wskaźników.  
  
## <a name="function-parameter-names"></a>Nazwy parametrów funkcji  
 Nazwy parametrów funkcji w definicjach funkcji są traktowane jako znajdował się w zakresie bloku peryferyjnych funkcji. W związku z tym są lokalne nazwy i znaleźć poza zakresem, gdy funkcja jest zakończony.  
  
 Nazwy parametrów funkcji w deklaracjach funkcji (prototypy) znajdują się w zakresie lokalnym deklaracji i się znaleźć poza zakresem na końcu deklaracji.  
  
 Domyślne parametry znajdują się w zakresie parametru, w którym są domyślnie, zgodnie z opisem w dwóch akapitów. Jednak ich nie ma dostępu zmienne lokalne lub elementy członkowskie klasy niestatycznego. Domyślne parametry są oceniane w punkcie wywołania funkcji, ale są one oceniane w deklaracji funkcji oryginalny zakres. W związku z tym domyślne parametry dla funkcji Członkowskich są zawsze obliczane w zakresie klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Dziedziczenie](../cpp/inheritance-cpp.md)
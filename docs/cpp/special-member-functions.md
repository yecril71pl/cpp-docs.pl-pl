---
title: "Specjalne funkcje Członkowskie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/06/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff4fc72d2a40cc52ec614cbd5b470738ad1aa391
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="special-member-functions"></a>Specjalne funkcje Członkowskie  
  
*Specjalnych funkcji Członkowskich* są, że w niektórych przypadkach kompilator automatycznie generuje dla Ciebie funkcje Członkowskie klasy (lub struct). Te funkcje są [domyślnego konstruktora](constructors-cpp.md#default_constructors), [destruktora](destructors-cpp.md), [konstruktora kopiującego i operatora przypisania kopii](copy-constructors-and-copy-assignment-operators-cpp.md)i [przenoszenie konstruktora i operator przypisania przenoszenia](move-constructors-and-move-assignment-operators-cpp.md). Jeśli klasa nie definiuje co najmniej jeden specjalnych funkcji Członkowskich, kompilator może niejawnie deklaruje i zdefiniuj funkcje, które są używane. Implementacje generowane przez kompilator są nazywane *domyślne* specjalnych funkcji Członkowskich. Kompilator nie generuje funkcji, jeśli nie są wymagane.  
  
Można jawnie deklarować domyślne specjalną funkcją członkowską przy użyciu `= default` — słowo kluczowe. Powoduje to kompilator, aby zdefiniować funkcję tylko wtedy, gdy jest to potrzebne w taki sam sposób, jakby funkcja nie została zadeklarowana w ogóle. 

W niektórych przypadkach, kompilator może wygenerować *usunięte* specjalnych funkcji Członkowskich, które nie są zdefiniowane i dlatego nie można wywołać. Może to nastąpić w przypadkach, gdy wywołanie określonego specjalną funkcją członkowską klasy nie ma sensu, podane inne właściwości klasy. Aby zapobiec jawnie automatyczne generowanie specjalną funkcją członkowską, można zadeklarować go jako usunięte za pomocą `= delete` — słowo kluczowe.  
  
Kompilator generuje *domyślnego konstruktora*, konstruktora, który nie przyjmuje żadnych argumentów tylko wtedy, gdy nie zostanie zgłoszone innego konstruktora. Jeśli można zadeklarować tylko konstruktora, który przyjmuje parametry, kod, który próby wywołania konstruktora domyślnego powoduje, że kompilator, aby utworzyć komunikat o błędzie. Generowane przez kompilator domyślnego konstruktora wykonuje proste member-wise [domyślne inicjowanie](initializers.md#default_initialization) obiektu. Inicjowanie domyślnych pozostawia wszystkie zmienne Członkowskie w stanie nieokreślonym.  
  
Destruktor domyślne wykonuje member-wise zniszczenia obiektu. Jest wirtualny tylko wtedy, gdy wirtualny destruktor klasy podstawowej.  
  
Domyślne kopiowania i przenoszenia konstruowania i przypisania operacji wykonania member-wise wzorca bitowego kopiuje lub przenosi elementów członkowskich danych niestatycznych. Przenieś operacje tylko są generowane, gdy nie operacje przenoszenia lub kopiowania lub destruktor został zadeklarowany. Domyślny Konstruktor kopiujący generowany jest tylko, gdy nie Konstruktor kopiujący jest zadeklarowany. Niejawnie usunięciu, jeśli zadeklarowano operacji przenoszenia. Domyślny operator przypisania kopiowania jest generowany tylko wtedy, gdy żaden operator przypisania kopiowania jest jawnie zadeklarowana. Niejawnie usunięciu, jeśli zadeklarowano operacji przenoszenia.  
  
## <a name="see-also"></a>Zobacz też  
[Dokumentacja języka C++](cpp-language-reference.md)  



 

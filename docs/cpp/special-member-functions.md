---
title: Specjalne funkcje Członkowskie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/06/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdc9ed6f4cae208a7edae412debe0a07870ea06e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112086"
---
# <a name="special-member-functions"></a>Specjalne funkcje Członkowskie

*Specjalnych funkcji Członkowskich* są klasy (lub struktury) elementów członkowskich, że w niektórych przypadkach kompilator automatycznie generuje dla Ciebie. Te funkcje są [domyślnego konstruktora](constructors-cpp.md#default_constructors), [destruktor](destructors-cpp.md), [Konstruktor kopiujący i operator przypisania kopiowania](copy-constructors-and-copy-assignment-operators-cpp.md)i [Konstruktor przenoszący i operator przypisania przenoszenia](move-constructors-and-move-assignment-operators-cpp.md). Jeśli klasa nie definiuje jedną lub więcej funkcji specjalnych elementów członkowskich, kompilator może niejawnie deklarowania i definiowania funkcji, które są używane. Implementacje generowanych przez kompilator są nazywane *domyślne* funkcji specjalnych elementów członkowskich. Kompilator nie generuje funkcji, jeśli nie są wymagane.

Można jawnie zadeklarować domyślną specjalną funkcję członkowską, za pomocą **= default** — słowo kluczowe. To powoduje, że kompilator, aby zdefiniować funkcję tylko, jeśli jest to konieczne, w taki sam sposób jak, jeśli funkcja nie został zadeklarowany w ogóle.

W niektórych przypadkach, kompilator może wygenerować *usunięte* specjalnych funkcji Członkowskich, które nie są zdefiniowane i dlatego nie jest wywoływane. Może to nastąpić w przypadkach, w którym wywołanie konkretnego specjalną funkcję członkowską klasy nie ma sensu, biorąc pod uwagę inne właściwości klasy. Aby jawnie zapobiec automatycznego generowania funkcji specjalnych elementów członkowskich, można zadeklarować je jako usunięte za pomocą **= delete** — słowo kluczowe.

Kompilator generuje *domyślnego konstruktora*, Konstruktor, który nie przyjmuje żadnych argumentów, tylko wtedy, gdy nie zostanie zgłoszone dowolnego innego konstruktora. Jeśli zadeklarowano tylko konstruktora przyjmującego parametry kod, który próbuje wywołać konstruktora domyślnego powoduje, że kompilator generuje komunikat o błędzie. Konstruktor domyślny wygenerowany przez kompilator wykonuje prostą member-wise [domyślna Inicjalizacja](initializers.md#default_initialization) obiektu. Domyślna Inicjalizacja pozostawi wszystkie zmienne składowe w stanie nieokreślonym.

Domyślnym destruktorze wykonuje member-wise zniszczenia obiektu. Jest wirtualny tylko wtedy, gdy wirtualny destruktor klasy podstawowej.

Domyślne kopiowania i przenoszenia konstrukcja i operacji przypisania wykonać member-wise wzorca bitowego kopiuje lub przenosi dane niestatycznych elementów członkowskich. Operacje tylko są generowane, gdy są zadeklarowane nie destruktora ani przenosić ani kopiować operacji przenoszenia. Domyślny Konstruktor kopiujący jest generowany tylko w sytuacji, gdy żaden Konstruktor kopiujący jest zadeklarowany. Jest niejawnie usunięta, jeśli operacja przeniesienia jest zadeklarowany. Operator przypisania kopii domyślny jest generowany tylko wtedy, gdy żaden operator przypisywania kopiowania jest zadeklarowany w sposób jawny. Jest niejawnie usunięta, jeśli operacja przeniesienia jest zadeklarowany.

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](cpp-language-reference.md)
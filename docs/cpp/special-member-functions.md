---
title: Specjalne funkcje składowe
ms.date: 12/06/2016
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
ms.openlocfilehash: b15a0e50774bbc4e70912a31f9a57ea0439f2c12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178694"
---
# <a name="special-member-functions"></a>Specjalne funkcje składowe

*Specjalne funkcje członkowskie* to funkcje członkowskie klasy (lub struktury), które w niektórych przypadkach automatycznie generują kompilator. Te funkcje są [konstruktorem domyślnym](constructors-cpp.md#default_constructors), [destruktorem](destructors-cpp.md), [konstruktorem kopiującym i operatorem przypisania kopiowania](copy-constructors-and-copy-assignment-operators-cpp.md), a [konstruktorem przenoszenia i operatorem przypisania przenoszenia](move-constructors-and-move-assignment-operators-cpp.md). Jeśli Klasa nie definiuje co najmniej jednej specjalnej funkcji składowej, kompilator może niejawnie deklarować i zdefiniować funkcje, które są używane. Implementacje generowane przez kompilator są nazywane *domyślnymi* specjalnymi funkcjami składowymi. Kompilator nie generuje funkcji, jeśli nie są one zbędne.

Można jawnie zadeklarować domyślną specjalną funkcję członkowską za pomocą słowa kluczowego **= default** . Powoduje to, że kompilator definiuje funkcję tylko w razie potrzeby, w taki sam sposób, jak w przypadku, gdy funkcja nie została zadeklarowana w ogóle.

W niektórych przypadkach kompilator może generować *usunięte* specjalne funkcje członkowskie, które nie są zdefiniowane i w związku z tym nie są wywoływane. Może się tak zdarzyć w przypadkach, gdy wywołanie określonej specjalnej funkcji składowej w klasie nie ma sensu, pod kątem innych właściwości klasy. Aby jawnie zapobiec automatycznemu generowaniu specjalnej funkcji składowej, można zadeklarować ją jako usuniętą za pomocą słowa kluczowego **= delete** .

Kompilator generuje *Konstruktor domyślny*, Konstruktor, który nie przyjmuje argumentów, tylko wtedy, gdy nie został zadeklarowany żaden inny Konstruktor. Jeśli zadeklarowano tylko konstruktora, który pobiera parametry, kod, który próbuje wywołać Konstruktor domyślny powoduje, że kompilator tworzy komunikat o błędzie. Konstruktor domyślny wygenerowany przez kompilator wykonuje prostą [domyślną inicjalizację](initializers.md#default_initialization) obiektu. Domyślna Inicjalizacja pozostawia wszystkie zmienne Członkowskie w nieokreślonym stanie.

Domyślny destruktor wykonuje zniszczenie obiektu przez element. Jest ona wirtualna tylko wtedy, gdy destruktor klasy bazowej jest wirtualny.

Domyślne kopiowanie i przenoszenie oraz operacje tworzenia i przypisywania są wykonywane w ramach kopiowania wzorca bitowego lub przenoszenia niestatycznych elementów członkowskich danych. Operacje przenoszenia są generowane tylko wtedy, gdy nie są zadeklarowane żadne operacje wykonywania destruktora lub przenoszenia lub kopiowania. Domyślny konstruktor kopiujący jest generowany tylko wtedy, gdy żaden Konstruktor kopiowania nie jest zadeklarowany. Jest on niejawnie usuwany w przypadku zadeklarowania operacji przenoszenia. Domyślny operator przypisania kopii jest generowany tylko wtedy, gdy żaden operator przypisania kopiowania nie został jawnie zadeklarowany. Jest on niejawnie usuwany w przypadku zadeklarowania operacji przenoszenia.

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](cpp-language-reference.md)

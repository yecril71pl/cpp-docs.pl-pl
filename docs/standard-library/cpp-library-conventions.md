---
title: Konwencje biblioteki C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, conventions
- classes [C++]
- functions [C++], library naming conventions
- naming conventions [C++], C++ Standard Library
- conventions [C++], C++ Standard Library
- function names [C++]
- coding conventions, C++ Standard Library
- naming conventions [C++], C++ library
ms.assetid: bf41b79a-2d53-4f46-8d05-779358335146
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1140c5421f6b39498fa69199c4d7ff7ccdc2476
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844240"
---
# <a name="c-library-conventions"></a>Konwencje biblioteki C++

Biblioteka języka C++ przestrzega znacznie tej samej Konwencji jako standardowa biblioteka języka C, a także kilka kolejnych opisana w tym temacie.

Implementacja ma niektórych szerokości geograficznej w sposób deklaruje typy i funkcje w bibliotece C++:

- Może mieć nazwy funkcje biblioteki standardowe C, extern #"C++" lub powiązania "C" extern. Dołącz odpowiedni nagłówek Standard C zamiast zadeklarować wbudowanego jednostki biblioteki.

- Nazwy funkcji Członkowskich w klasie biblioteki może mieć sygnatur dodatkowych funkcji za pośrednictwem wymienione w tym dokumencie. Można mieć pewność, że wywołanie funkcji opisanych w tym miejscu działa zgodnie z oczekiwaniami, ale niezawodnie nie można przyjąć adresu funkcji członkowskiej biblioteki. (Typ może nie być oczekiwań.)

- Klasy biblioteki może mieć klas podstawowych nieudokumentowanej (niewirtualne). Klasa udokumentowane, która pochodzi z innej klasy w rzeczywistości może pochodzić z tej klasy przy użyciu innych klas nieudokumentowanej.

- Typ zdefiniowany jako synonim dla niektórych typu Liczba całkowita może być taki sam jak jeden z kilku różnymi typami.

- Typ maski można zaimplementować jako typu integer lub wyliczenia. W obu przypadkach można wykonywać operacje bitowe (takie jak `AND` i `OR`) dla wartości typu maski. Elementy `A` i `B` typu maski są niezerowe wartości tak, aby `A`  &  `B` wynosi zero.

- Funkcji biblioteki, która ma Brak specyfikacji wyjątku może zgłosić wyjątek dowolnego, chyba że jego definicji wyraźnie ogranicza taką możliwość.

Z drugiej strony istnieją pewne ograniczenia:

- Standardowa biblioteka języka C nie używa żadnych makr maskowania. Tylko określonych funkcji, podpisy są zarezerwowane, nie do nazw same funkcje.

- Nazwa funkcji biblioteki poza klasą nie będzie miał sygnatury funkcji dodatkowych, nieudokumentowanej. Adres niezawodnie może potrwać.

- Klasy podstawowe i funkcje Członkowskie opisanego jako wirtualne są assuredly wirtualnego podczas są opisane jako niewirtualne assuredly niewirtualna.

- Dwa typy zdefiniowane w bibliotece C++ różnią się zawsze chyba, że ten dokument jawnie sugestią, w przeciwnym razie wartość.

- Funkcje dostarczonych przez bibliotekę wersji domyślnej funkcji replaceable może zgłosić *co najwyżej* tych wyjątków na liście wszystkie Specyfikacja wyjątku. Nie destruktory dostarczonych przez bibliotekę zgłaszają wyjątki. Funkcje standardowej biblioteki C może propagowanie wyjątku, gdy `qsort` wywołania porównanie funkcji, która zgłasza wyjątek, ale ich nie inaczej zgłaszają wyjątki.

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

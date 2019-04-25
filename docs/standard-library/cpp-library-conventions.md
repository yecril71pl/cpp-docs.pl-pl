---
title: Konwencje biblioteki C++
ms.date: 11/04/2016
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
ms.openlocfilehash: f1790b75baea340d0b3ab1044290317055ac81d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62210778"
---
# <a name="c-library-conventions"></a>Konwencje biblioteki C++

Biblioteka języka C++ przestrzegają wiele tych samych konwencji jako standardowej biblioteki C, a także kilka innych opisana w tym temacie.

Implementacja ma niektórych szerokości, w jaki relacja ta stwierdza, typy i funkcje w bibliotece C++:

- Nazwy funkcje biblioteki standardowej C może być zewnętrzny #"C++" lub extern "C" powiązania. Dołącz odpowiedni nagłówek standardowy C, zamiast deklarowania wbudowanej jednostki biblioteki.

- Nazwy funkcji składowej w klasie biblioteki mogą mieć sygnatur dodatkowych funkcji za pośrednictwem tych wymienionych w niniejszym dokumencie. Można mieć pewność, że wywołanie funkcji, opisane w tym miejscu zachowuje się zgodnie z oczekiwaniami, ale niezawodnie nie można przyjąć adresu funkcji składowej biblioteki. (Typ może nie być oczekiwań).

- Klasa biblioteki może mieć klas bazowych nieudokumentowane (niewirtualne). Klasa udokumentowane, która pochodzi z innej klasy w rzeczywistości może pochodzić od tej klasy przy użyciu innych klas nieudokumentowane.

- Typ zdefiniowany jako synonim dla pewnego typu Liczba całkowita może być taki sam jak jeden z kilku różnymi typami całkowitymi.

- Typem maski bitów można zaimplementować jako typ liczby całkowitej lub wyliczenia. W obu przypadkach można wykonać operacje bitowe (takie jak `AND` i `OR`) dla wartości typu maski bitów. Elementy `A` i `B` typu maski bitów jest niezerowe wartości tak, aby `A`  &  `B` wynosi zero.

- Funkcja biblioteki, która ma bez określenia wyjątków może zgłosić wyjątek dowolnego, chyba że jego definicja wyraźnie ogranicza taką możliwość.

Z drugiej strony istnieją pewne ograniczenia:

- Standardowej biblioteki C używa makra nie maskowania. Tylko określonych funkcji, której podpisy są zarezerwowane, nie nazw same funkcje.

- Nazwa funkcji biblioteki poza klasą nie będzie miał sygnatur funkcji dodatkowych, nieudokumentowane. Możesz niezawodnie korzystać z adresu.

- Klasy podstawowe i określana jako wirtualnych elementów członkowskich są assuredly wirtualnego podczas są opisane jako niewirtualne assuredly niewirtualne.

- Dwa typy zdefiniowane przez bibliotekę języka C++ zawsze są różne, chyba że w tym dokumencie jawnie sugeruje, w przeciwnym razie.

- Funkcje dostarczone przez bibliotekę, w tym domyślne wersje funkcji wymienne, może zgłosić *co najwyżej* tych wyjątków wymienionych w dowolnym Specyfikacja wyjątku. Żadne destruktory dostarczonych przez bibliotekę zgłaszać wyjątki. Funkcje w standardowej biblioteki C może propagować wyjątek, gdy `qsort` wywołania porównanie funkcji, która zgłasza wyjątek, ale nie w przeciwnym razie zgłaszają wyjątki.

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

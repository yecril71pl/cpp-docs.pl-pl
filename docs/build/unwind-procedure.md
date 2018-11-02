---
title: Procedura Unwind
ms.date: 11/04/2016
ms.assetid: 82c5d0ca-70be-4d1a-a306-bfe01c29159f
ms.openlocfilehash: 2d68a5c3fb1cc2d18b587d1419b0103d02b35a7f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523115"
---
# <a name="unwind-procedure"></a>Procedura Unwind

Tablica kodu odwijania jest posortowana w kolejności malejącej. Gdy wystąpi wyjątek, pełnego kontekstu są przechowywane przez system operacyjny w rekordu kontekstu. Następnie wywoływana jest logiki wysyłania wyjątków, które regularnie wykonuje następujące kroki, aby znaleźć obsługi wyjątków.

1. Użyj bieżącego RIP, przechowywane w rekordu kontekstu, aby wyszukać RUNTIME_FUNCTION wpis tabeli, który opisuje bieżącą funkcję (lub jej część funkcja, przypadku łańcuchowych wpisy UNWIND_INFO).

1. Jeśli zostanie znaleziony żaden wpis tabeli funkcji, będzie ona wówczas w funkcji liścia i RSP sprostają bezpośrednio zwracana wskaźnika. Zwracany wskaźnik u [RSP] jest przechowywana w kontekście zaktualizowane symulowane RSP jest zwiększany o 8 i jest powtarzany w kroku 1.

1. Jeśli wpis tabeli funkcji zostanie znaleziony, RIP może znajdować się w trzech regionach, () w epilogu, (b) w prologu lub c) w kodzie, który może być objętych przez program obsługi wyjątku.

   - Wielkości liter) czy RPO w ramach epilogu, a następnie sterowania opuszcza funkcji, może być nie skojarzonych z tym wyjątkiem, dla tej funkcji program obsługi wyjątków, a skutki epilogu musi być kontynuowana do obliczenia kontekście wywołujący funkcję. Aby określić, jeśli protokół RIP mieści się w epilogu strumienia kodu z RIP na jest sprawdzany pod. Jeśli tego strumienia kodu można dopasować do końcowej części epilogu uzasadnione, to znajduje się w epilogu i pozostałej części epilogu jest symulowane, przy użyciu rekordu kontekstu aktualizować wraz z każdą instrukcję przetwarzania. Po tym kroku 1 jest powtarzany.

   - Przypadku b) Jeśli RPO znajduje się w prologu, wówczas formantu nie wprowadzono funkcji, może być nie skojarzonych z tym wyjątkiem, dla tej funkcji program obsługi wyjątków, a skutki prologu muszą zostać cofnięte do obliczenia kontekście wywołujący funkcję. Protokół RIP znajduje się w prologu, jeśli odległość od początku funkcji RPO jest mniejsza niż lub równy rozmiarowi prologu zakodowane w informacji unwind. Efekty prologu są odwinięty do przodu skanowania przez tablicę kody unwind do pierwszej pozycji z przesunięciem mniejsze niż lub równe przesunięcia RPO od początku funkcji, a następnie cofnięcie efekt wszystkie pozostałe elementy w tablicy kodu unwind. Krok 1 jest następnie powtarzany.

   - Wielkość c), jeśli RPO nie znajduje się w prologu i epilogu i funkcji ma program obsługi wyjątku (UNW_FLAG_EHANDLER jest ustawiona), a następnie jest wywoływana Obsługa określonego języka. Program obsługi skanuje dane i wywołania filtrowania funkcji zgodnie z potrzebami. Obsługa określonego języka może zwracać, czy wyjątek został obsłużony lub wyszukiwanie jest kontynuowane. Go może również inicjować unwind bezpośrednio.

1. Obsługa określonego języka zwraca obsługiwane stan, a następnie wykonywanie jest kontynuowane przy użyciu oryginalnego rekordu kontekstu.

1. Jeśli nie istnieje żadne Obsługa określonego języka lub program obsługi zwraca stan "Kontynuuj wyszukiwanie", rekordu kontekstu musi być rozwinięty do stanu obiektu wywołującego. Jest to realizowane przez wszystkie elementy tablicy unwind kodu, cofnięcie efektu każdej przetwarzanie. Krok 1 jest następnie powtarzany.

Gdy łańcuchowej unwind uczestniczy info, te proste kroki, nadal po nim. Jedyną różnicą jest to, że, gdy zalet tablicy kodu unwind na odpoczynek efekty prologu, po osiągnięciu końca tablicy, jego jest następnie łączony z informacji unwind nadrzędnego i zostaje przeprowadzony unwind całej tablicy kodu znalezione. To połączenie jest kontynuowany aż do otrzymywanych unwind info, bez flagi UNW_CHAINED_INFO i Zakończ zalet jego tablica kodu unwind.

Dane operacji unwind najmniejszy zestaw jest 8 bajtów. To reprezentuje funkcję, która tylko przydzielone 128 bajtów stosu lub mniej, a prawdopodobnie zapisywane jeden rejestr nieulotnej. Jest to również rozmiar łańcuchowych unwind info struktury prologu o zerowej długości z żadnych kodów unwind.

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków (x64)](../build/exception-handling-x64.md)
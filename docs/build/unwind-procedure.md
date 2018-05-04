---
title: Procedura unwind | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 82c5d0ca-70be-4d1a-a306-bfe01c29159f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e2a5af5d8db5974aa10595bbd3bac1cd032a0f4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="unwind-procedure"></a>Procedura Unwind
Tablica kodu unwind jest sortowany w kolejności malejącej. Po wystąpieniu wyjątku, pełną kontekst jest przechowywany przez system operacyjny w rekordu kontekstu. Następnie wywoływana jest logiki wysyłania wyjątek, który wielokrotnie wykonuje następujące czynności, aby znaleźć obsługi wyjątków.  
  
1.  Służy bieżącego RIP przechowywane w rekordu kontekstu do wyszukiwania dla wpisu tabeli RUNTIME_FUNCTION opisujący bieżącej funkcji (lub części funkcji, w przypadku wpisów UNWIND_INFO łańcuchowa).  
  
2.  Jeśli funkcja wpisu tabeli zostanie znaleziony, się ona w funkcją typu liść, a źródło bezpośrednio zajmie zwracany wskaźnika. Wskaźnik zwracany u [źródło] jest przechowywana w kontekście zaktualizowane, symulowane źródło jest zwiększany o 8 i jest powtarzany w kroku 1.  
  
3.  Jeśli zostanie znaleziony wpisu tabeli funkcji, RIP może znajdować się w obrębie trzech regionów, () w epilogu, (b) w prologu lub c) w kodzie, który może być objętych przez program obsługi wyjątku.  
  
    -   Wielkość) Jeśli RIP mieści się w epilogu kontroli opuszcza funkcji, nie mogą istnieć bez obsługi wyjątków skojarzonych z tym wyjątkiem dla tej funkcji i skutków epilogu musi być kontynuowana do obliczenia kontekście funkcji wywołującego. Do ustalenia, czy protokół RIP jest w obrębie epilogu strumień kodu z RIP na się zbadana. Jeśli strumieniu kodu można dopasować do końcowej części epilogu uzasadnione, to w epilogu i symulacji pozostałej części epilogu, z rekordu kontekstu zaktualizowany po każdej instrukcji przetworzeniem. Po tym kroku 1 jest powtarzany.  
  
    -   Przypadek b), jeśli protokół RIP mieści się w prologu, a następnie formant nie ma wprowadzona funkcja, nie mogą istnieć bez obsługi wyjątków skojarzonych z tym wyjątkiem dla tej funkcji i skutków prologu musi zostać cofnięte do obliczenia kontekście funkcji wywołującego. Protokół RIP znajduje się w prologu, jeśli odległość od początku funkcji RIP jest mniejsze lub równe rozmiarowi prologu zakodowane informacji unwind. Efekty prologu są odwinięty do przodu skanowanie za pomocą tablicy kody unwind dla pierwszej pozycji z przesunięciem mniejsze niż lub równe przesunięcie RIP od początku funkcji, a następnie cofanie efekt wszystkich pozostałych elementów w tablicy unwind kodu. Krok 1 jest następnie powtarzany.  
  
    -   Wielkość c) czy RPO nie znajduje się w prologu lub epilogu i funkcję, ma obsługi wyjątków (Ustaw UNW_FLAG_EHANDLER), a następnie jest nazywany Obsługa określonego języka. Program obsługi skanuje dane i wywołania filtru funkcji zależnie od potrzeb. Obsługa określonego języka może zwrócić, czy wyjątek został obsłużony, lub czy wyszukiwanie ma być kontynuowane. Go można także zainicjować unwind bezpośrednio.  
  
4.  Jeśli obsługa określonego języka zwraca stan obsługiwany, a następnie wykonanie jest kontynuowane przy użyciu oryginalnego rekordu kontekstu.  
  
5.  Jeśli nie istnieje żadne Obsługa określonego języka lub program obsługi zwraca stan "continue wyszukiwania", rekordu kontekstu musi być oddzielić stan obiektu wywołującego. Jest to osiągane przez wszystkie elementy tablicy unwind kodu, cofanie efekt każdego przetwarzania. Krok 1 jest następnie powtarzany.  
  
 Gdy łańcuchowej unwind uczestniczy info, nadal zostaną wykonane następujące czynności. Jedyną różnicą jest to, że, przejście tablicy kodu unwind cofnąć prologu efekty, gdy zostanie osiągnięty koniec tablicy, jest następnie połączony informacji unwind nadrzędnej i jest udał tablicy kodu całego unwind Brak znaleziono. To połączenie jest kontynuowane do otrzymywanych informacji unwind bez flagi UNW_CHAINED_INFO i Zakończ przejście jego unwind kodu tablicy.  
  
 Dane operacji unwind najmniejszy zestaw jest 8 bajtów. Spowoduje to reprezentuje funkcję, która tylko przydzielone 128 bajtów stosu lub mniej i prawdopodobnie zapisane jednego nieulotnej rejestru. Dotyczy to również rozmiar łańcuchowa unwind struktury informacji z żadnych kodów unwind prologu o zerowej długości.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków (x64)](../build/exception-handling-x64.md)
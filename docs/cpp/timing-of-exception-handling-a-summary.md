---
title: 'Czas obsługi wyjątków: Podsumowanie'
ms.date: 05/07/2019
helpviewer_keywords:
- sequence [C++]
- sequence, of handlers
- exception handling [C++], timing
- setjmpex.h
- termination handlers [C++], timing
- setjmp.h
- handlers [C++], order of exception
- structured exception handling [C++], timing
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
ms.openlocfilehash: 17d1c250a98afc2b86c198735602df7d80118bd4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316595"
---
# <a name="timing-of-exception-handling-a-summary"></a>Czas obsługi wyjątków: Podsumowanie

Program obsługi zakończenia jest wykonywany bez względu na to, jak blok instrukcji **__try** zostanie zakończony. Przyczyny obejmują wyskakiwanie z bloku `longjmp` **__try,** instrukcja, która przenosi kontrolę z bloku i odwijanie stosu z powodu obsługi wyjątków.

> [!NOTE]
> Kompilator Microsoft C++ obsługuje `setjmp` dwie `longjmp` formy i instrukcji. Szybka wersja omija obsługę przerwania, ale jest bardziej wydajna. Aby użyć tej wersji, \<dołącz plik setjmp.h>. Druga wersja zapewnia obsługę przerwania opisaną w poprzednim akapicie. Aby użyć tej wersji, \<dołącz plik setjmpex.h>. Wzrost wydajności z użycia wersji szybkiej zależy od konfiguracji sprzętowej.

System operacyjny wykonuje wszystkie programy obsługi przerwania w odpowiedniej kolejności, zanim wykonany będzie jakikolwiek inny kod, włączając w to treść programu obsługi wyjątków.

Gdy przyczyną przerwania jest wyjątek, system musi najpierw wykonać część filtru przynajmniej jednego programu obsługi wyjątku, zanim zdecyduje co przerwać. Kolejność zdarzeń jest następująca:

1. Zgłaszany jest wyjątek.

1. System przeszukuje hierarchię aktywnych programów obsługi wyjątków i wykonuje filtr programu obsługi o najwyższym priorytecie; jest to ostatnio zainstalowany, najgłębiej zagnieżdżony względem bloków i wywołań funkcji, program obsługi wyjątków.

1. Jeśli filtr przekaże sterowanie (zwróci 0), proces jest kontynuowany, dopóki nie zostanie znaleziony filtr, który nie przekaże sterowania.

1. Jeśli ten filtr zwraca -1, wykonanie jest kontynuowane, gdzie wyjątek został zgłoszony i nie ma miejsca zakończenie.

1. Jeśli filtr zwróci 1, zachodzą następujące zdarzenia:

   - System rozwija stos, czyszcząc wszystkie ramki stosu między kodem wykonywanym w bieżącym momencie (w którym został zgłoszony wyjątek), a ramką stosu, która zawiera program obsługi wyjątków uzyskujący kontrolę.

   - Gdy stos jest rozwinięty, wykonywany jest każdy znajdujący się na nim program obsługi przerwania.

   - Wykonywany jest właściwy program obsługi przerwania.

   - Sterowanie jest przekazywane do wiersza kodu następującego po programie obsługi wyjątków.

## <a name="see-also"></a>Zobacz też

[Zapisywanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

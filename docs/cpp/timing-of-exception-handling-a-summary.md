---
title: 'Chronometraż dla obsługi wyjątków: Podsumowanie'
description: Chronometraż i kolejność wykonywania obsługi wyjątków w programie Microsoft C++.
ms.date: 08/24/2020
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
ms.openlocfilehash: 2ce501d8d74b6f0f7ca92e193c39f8ce58a66053
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898360"
---
# <a name="timing-of-exception-handling-a-summary"></a>Chronometraż dla obsługi wyjątków: Podsumowanie

Procedura obsługi zakończenia jest wykonywana niezależnie od sposobu **`__try`** zakończenia bloku instrukcji. Przyczyny obejmują przeskoczenie z **`__try`** bloku, `longjmp` instrukcję, która przenosi kontrolkę z bloku i odwraca stos ze względu na obsługę wyjątków.

> [!NOTE]
> Kompilator języka Microsoft C++ obsługuje dwie formy `setjmp` `longjmp` instrukcji i. Szybka wersja omija obsługę przerwania, ale jest bardziej wydajna. Aby użyć tej wersji, Dołącz plik \<setjmp.h> . Druga wersja zapewnia obsługę przerwania opisaną w poprzednim akapicie. Aby użyć tej wersji, Dołącz plik \<setjmpex.h> . Wzrost wydajności z użycia wersji szybkiej zależy od konfiguracji sprzętowej.

System operacyjny wykonuje wszystkie programy obsługi przerwania w odpowiedniej kolejności, zanim wykonany będzie jakikolwiek inny kod, włączając w to treść programu obsługi wyjątków.

Gdy przyczyną przerwania jest wyjątek, system musi najpierw wykonać część filtru przynajmniej jednego programu obsługi wyjątku, zanim zdecyduje co przerwać. Kolejność zdarzeń jest następująca:

1. Zgłaszany jest wyjątek.

1. System przegląda hierarchię aktywnych programów obsługi wyjątków i wykonuje filtr programu obsługi z najwyższym priorytetem. Jest to program obsługi wyjątków ostatnio zainstalowany i najbardziej głęboko zagnieżdżony, przechodzący przez bloki i wywołania funkcji.

1. Jeśli ten filtr przekazuje kontrolę (zwraca 0), proces jest kontynuowany do momentu znalezienia filtru, który nie przeszedł kontroli.

1. Jeśli ten filtr zwróci wartość-1, wykonywanie jest kontynuowane, gdy wyjątek został zgłoszony i nie ma żadnych przerw.

1. Jeśli filtr zwróci 1, zachodzą następujące zdarzenia:

   - System rozwinięcia stosu: czyści wszystkie ramki stosu między miejscem, w którym został zgłoszony wyjątek, a ramką stosu, która zawiera program obsługi wyjątków.

   - Gdy stos jest rozwinięty, wykonywany jest każdy znajdujący się na nim program obsługi przerwania.

   - Wykonywany jest właściwy program obsługi przerwania.

   - Sterowanie jest przekazywane do wiersza kodu następującego po programie obsługi wyjątków.

## <a name="see-also"></a>Zobacz też

[Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

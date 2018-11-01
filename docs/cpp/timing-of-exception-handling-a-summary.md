---
title: 'Chronometraż dla obsługi wyjątków: podsumowanie'
ms.date: 11/04/2016
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
ms.openlocfilehash: cbff7c4153646fcb3471e18d20a0e633fbd1307f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477431"
---
# <a name="timing-of-exception-handling-a-summary"></a>Chronometraż dla obsługi wyjątków: podsumowanie

Program obsługi przerwania jest wykonywany niezależnie od tego, jak **__try** został przerwany blok instrukcji. Przyczyny obejmują skok na zewnątrz **__try** bloku `longjmp` instrukcję, która przenosi sterowanie na zewnątrz bloku i odwinięcie stosu wskutek obsługi wyjątku.

> [!NOTE]
>  Język Visual C++ obsługuje dwie postacie instrukcji `setjmp` i `longjmp`. Szybka wersja omija obsługę przerwania, ale jest bardziej wydajna. Aby użyć tej wersji, Dołącz plik \<setjmp.h >. Druga wersja zapewnia obsługę przerwania opisaną w poprzednim akapicie. Aby użyć tej wersji, Dołącz plik \<setjmpex.h >. Wzrost wydajności z użycia wersji szybkiej zależy od konfiguracji sprzętowej.

System operacyjny wykonuje wszystkie programy obsługi przerwania w odpowiedniej kolejności, zanim wykonany będzie jakikolwiek inny kod, włączając w to treść programu obsługi wyjątków.

Gdy przyczyną przerwania jest wyjątek, system musi najpierw wykonać część filtru przynajmniej jednego programu obsługi wyjątku, zanim zdecyduje co przerwać. Kolejność zdarzeń jest następująca:

1. Zgłaszany jest wyjątek.

1. System przeszukuje hierarchię aktywnych programów obsługi wyjątków i wykonuje filtr programu obsługi o najwyższym priorytecie; jest to ostatnio zainstalowany, najgłębiej zagnieżdżony względem bloków i wywołań funkcji, program obsługi wyjątków.

1. Jeśli filtr przekaże sterowanie (zwróci 0), proces jest kontynuowany, dopóki nie zostanie znaleziony filtr, który nie przekaże sterowania.

1. Jeśli filtr zwróci wartość -1, wykonywanie jest kontynuowane, gdy wyjątek został zgłoszony, a przerwanie nie zachodzi miejsce.

1. Jeśli filtr zwróci 1, zachodzą następujące zdarzenia:

   - System rozwija stos, czyszcząc wszystkie ramki stosu między kodem wykonywanym w bieżącym momencie (w którym został zgłoszony wyjątek), a ramką stosu, która zawiera program obsługi wyjątków uzyskujący kontrolę.

   - Gdy stos jest rozwinięty, wykonywany jest każdy znajdujący się na nim program obsługi przerwania.

   - Wykonywany jest właściwy program obsługi przerwania.

   - Sterowanie jest przekazywane do wiersza kodu następującego po programie obsługi wyjątków.

## <a name="see-also"></a>Zobacz także

[Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
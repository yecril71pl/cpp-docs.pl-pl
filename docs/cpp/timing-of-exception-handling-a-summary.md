---
title: 'Chronometraż obsługi wyjątków: Podsumowanie'
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
ms.openlocfilehash: 870606c3661df3654581760214e48ef2bdfb1987
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246333"
---
# <a name="timing-of-exception-handling-a-summary"></a>Chronometraż obsługi wyjątków: Podsumowanie

Procedura obsługi zakończenia jest wykonywana niezależnie od sposobu przerwania bloku instrukcji **__try** . Przyczyny obejmują wyskoczenie z bloku **__try** , instrukcję `longjmp`, która przenosi kontrolę z bloku i odblokowuje stos ze względu na obsługę wyjątków.

> [!NOTE]
>  Kompilator firmy C++ Microsoft obsługuje dwie formy `setjmp` i `longjmp` instrukcji. Szybka wersja omija obsługę przerwania, ale jest bardziej wydajna. Aby użyć tej wersji, Dołącz plik \<setjmp. h >. Druga wersja zapewnia obsługę przerwania opisaną w poprzednim akapicie. Aby użyć tej wersji, Dołącz plik \<SETJMPEX. h >. Wzrost wydajności z użycia wersji szybkiej zależy od konfiguracji sprzętowej.

System operacyjny wykonuje wszystkie programy obsługi przerwania w odpowiedniej kolejności, zanim wykonany będzie jakikolwiek inny kod, włączając w to treść programu obsługi wyjątków.

Gdy przyczyną przerwania jest wyjątek, system musi najpierw wykonać część filtru przynajmniej jednego programu obsługi wyjątku, zanim zdecyduje co przerwać. Kolejność zdarzeń jest następująca:

1. Zgłaszany jest wyjątek.

1. System przeszukuje hierarchię aktywnych programów obsługi wyjątków i wykonuje filtr programu obsługi o najwyższym priorytecie; jest to ostatnio zainstalowany, najgłębiej zagnieżdżony względem bloków i wywołań funkcji, program obsługi wyjątków.

1. Jeśli filtr przekaże sterowanie (zwróci 0), proces jest kontynuowany, dopóki nie zostanie znaleziony filtr, który nie przekaże sterowania.

1. Jeśli ten filtr zwróci wartość-1, wykonywanie jest kontynuowane, gdy wyjątek został zgłoszony i nie ma żadnych przerw.

1. Jeśli filtr zwróci 1, zachodzą następujące zdarzenia:

   - System rozwija stos, czyszcząc wszystkie ramki stosu między kodem wykonywanym w bieżącym momencie (w którym został zgłoszony wyjątek), a ramką stosu, która zawiera program obsługi wyjątków uzyskujący kontrolę.

   - Gdy stos jest rozwinięty, wykonywany jest każdy znajdujący się na nim program obsługi przerwania.

   - Wykonywany jest właściwy program obsługi przerwania.

   - Sterowanie jest przekazywane do wiersza kodu następującego po programie obsługi wyjątków.

## <a name="see-also"></a>Zobacz także

[Pisanie procedury obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
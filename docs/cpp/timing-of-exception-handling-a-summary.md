---
title: 'Chronometraż dla obsługi wyjątków: Podsumowanie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff2ac5abb13ae700e464635efc90a91c4a5835ab
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939419"
---
# <a name="timing-of-exception-handling-a-summary"></a>Chronometraż dla obsługi wyjątków: podsumowanie
Program obsługi przerwania jest wykonywany niezależnie od tego, jak **__try** został przerwany blok instrukcji. Przyczyny obejmują skok na zewnątrz **__try** bloku `longjmp` instrukcję, która przenosi sterowanie na zewnątrz bloku i odwinięcie stosu wskutek obsługi wyjątku.  
  
> [!NOTE]
>  Język Visual C++ obsługuje dwie postacie instrukcji `setjmp` i `longjmp`. Szybka wersja omija obsługę przerwania, ale jest bardziej wydajna. Aby użyć tej wersji, Dołącz plik \<setjmp.h >. Druga wersja zapewnia obsługę przerwania opisaną w poprzednim akapicie. Aby użyć tej wersji, Dołącz plik \<setjmpex.h >. Wzrost wydajności z użycia wersji szybkiej zależy od konfiguracji sprzętowej.  
  
 System operacyjny wykonuje wszystkie programy obsługi przerwania w odpowiedniej kolejności, zanim wykonany będzie jakikolwiek inny kod, włączając w to treść programu obsługi wyjątków.  
  
 Gdy przyczyną przerwania jest wyjątek, system musi najpierw wykonać część filtru przynajmniej jednego programu obsługi wyjątku, zanim zdecyduje co przerwać. Kolejność zdarzeń jest następująca:  
  
1.  Zgłaszany jest wyjątek.  
  
2.  System przeszukuje hierarchię aktywnych programów obsługi wyjątków i wykonuje filtr programu obsługi o najwyższym priorytecie; jest to ostatnio zainstalowany, najgłębiej zagnieżdżony względem bloków i wywołań funkcji, program obsługi wyjątków.  
  
3.  Jeśli filtr przekaże sterowanie (zwróci 0), proces jest kontynuowany, dopóki nie zostanie znaleziony filtr, który nie przekaże sterowania.  
  
4.  Jeśli filtr zwróci wartość -1, wykonywanie jest kontynuowane, gdy wyjątek został zgłoszony, a przerwanie nie zachodzi miejsce.  
  
5.  Jeśli filtr zwróci 1, zachodzą następujące zdarzenia:  
  
    -   System rozwija stos, czyszcząc wszystkie ramki stosu między kodem wykonywanym w bieżącym momencie (w którym został zgłoszony wyjątek), a ramką stosu, która zawiera program obsługi wyjątków uzyskujący kontrolę.  
  
    -   Gdy stos jest rozwinięty, wykonywany jest każdy znajdujący się na nim program obsługi przerwania.  
  
    -   Wykonywany jest właściwy program obsługi przerwania.  
  
    -   Sterowanie jest przekazywane do wiersza kodu następującego po programie obsługi wyjątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)   
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
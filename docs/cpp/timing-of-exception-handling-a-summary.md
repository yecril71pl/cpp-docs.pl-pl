---
title: "Chronometraż dla obsługi wyjątków: Podsumowanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- sequence [C++]
- sequence, of handlers
- exception handling [C++], timing
- SETJMPEX.H
- termination handlers [C++], timing
- SETJMP.H
- handlers [C++], order of exception
- structured exception handling [C++], timing
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d4b522286a727f428cd445bf67d12a1360b49b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="timing-of-exception-handling-a-summary"></a>Chronometraż dla obsługi wyjątków: podsumowanie
Program obsługi przerwania jest wykonywany niezależnie od tego, w jaki sposób został przerwany blok instrukcji `__try`. Przyczyny obejmują skok na zewnątrz bloku `__try`, instrukcję `longjmp`, która przenosi sterowanie na zewnątrz bloku i odwinięcie stosu wskutek obsługi wyjątku.  
  
> [!NOTE]
>  Język Visual C++ obsługuje dwie postacie instrukcji `setjmp` i `longjmp`. Szybka wersja omija obsługę przerwania, ale jest bardziej wydajna. Aby użyć tej wersji, dołącz plik SETJMP.H. Druga wersja zapewnia obsługę przerwania opisaną w poprzednim akapicie. Aby użyć tej wersji, dołącz plik SETJMPEX.H. Wzrost wydajności z użycia wersji szybkiej zależy od konfiguracji sprzętowej.  
  
 System operacyjny wykonuje wszystkie programy obsługi przerwania w odpowiedniej kolejności, zanim wykonany będzie jakikolwiek inny kod, włączając w to treść programu obsługi wyjątków.  
  
 Gdy przyczyną przerwania jest wyjątek, system musi najpierw wykonać część filtru przynajmniej jednego programu obsługi wyjątku, zanim zdecyduje co przerwać. Kolejność zdarzeń jest następująca:  
  
1.  Zgłaszany jest wyjątek.  
  
2.  System przeszukuje hierarchię aktywnych programów obsługi wyjątków i wykonuje filtr programu obsługi o najwyższym priorytecie; jest to ostatnio zainstalowany, najgłębiej zagnieżdżony względem bloków i wywołań funkcji, program obsługi wyjątków.  
  
3.  Jeśli filtr przekaże sterowanie (zwróci 0), proces jest kontynuowany, dopóki nie zostanie znaleziony filtr, który nie przekaże sterowania.  
  
4.  Jeśli filtr zwróci wartość -1, wykonywanie będzie kontynuowane, gdzie został zgłoszony wyjątek, a nie zakończenia ma miejsce.  
  
5.  Jeśli filtr zwróci 1, zachodzą następujące zdarzenia:  
  
    -   System rozwija stos, czyszcząc wszystkie ramki stosu między kodem wykonywanym w bieżącym momencie (w którym został zgłoszony wyjątek), a ramką stosu, która zawiera program obsługi wyjątków uzyskujący kontrolę.  
  
    -   Gdy stos jest rozwinięty, wykonywany jest każdy znajdujący się na nim program obsługi przerwania.  
  
    -   Wykonywany jest właściwy program obsługi przerwania.  
  
    -   Sterowanie jest przekazywane do wiersza kodu następującego po programie obsługi wyjątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)   
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
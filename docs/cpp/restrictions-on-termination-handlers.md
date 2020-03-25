---
title: Ograniczenia dotyczące programu obsługi zakończenia
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: befe181a41ed418a4a824b131e741a9f02f90e38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179071"
---
# <a name="restrictions-on-termination-handlers"></a>Ograniczenia dotyczące programu obsługi zakończenia

Nie można użyć instrukcji **goto** , aby przejść do bloku instrukcji **__try** lub bloku instrukcji **__finally** . Zamiast tego należy wprowadzić blok instrukcji za pomocą normalnego przepływu sterowania. (Można jednak wyskoczyć z bloku instrukcji **__try** ). Ponadto nie można zagnieżdżać procedury obsługi wyjątku ani procedury zakończenia w bloku **__finally** .

Ponadto niektóre rodzaje kodu dozwolone w programie obsługi zakończenia dają wyniki z pytaniami, dlatego należy ich używać ostrożnie, jeśli w ogóle. Jednym z nich jest instrukcja **goto** , która przeskakuje z bloku instrukcji **__finally** . Jeśli blok jest wykonywany w ramach normalnego zakończenia, nic się nie dzieje. Ale jeśli system wychodzi z odwinięcia stosu, to odwracanie zostanie zatrzymane, a bieżąca funkcja uzyskuje kontrolę tak, jakby nie było nietypowego zakończenia.

Instrukcja **Return** w bloku instrukcji **__finally** przedstawia przybliżoną taką samą sytuację. Kontrolka powraca do bezpośredniego obiektu wywołującego funkcji, która zawiera procedurę obsługi zakończenia. Jeśli system spowodował odtworzenie stosu, ten proces jest zatrzymany, a program będzie kontynuował działanie tak, jakby nie został zgłoszony wyjątek.

## <a name="see-also"></a>Zobacz też

[Pisanie procedury obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

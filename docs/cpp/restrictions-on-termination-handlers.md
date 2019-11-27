---
title: Ograniczenia dotyczące programu obsługi zakończenia
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: 6c39407270037756c55dc42aed80e1d04616c9ee
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246384"
---
# <a name="restrictions-on-termination-handlers"></a>Ograniczenia dotyczące programu obsługi zakończenia

Nie można użyć instrukcji **goto** , aby przejść do bloku instrukcji **__try** lub bloku instrukcji **__finally** . Zamiast tego należy wprowadzić blok instrukcji za pomocą normalnego przepływu sterowania. (Można jednak wyskoczyć z bloku instrukcji **__try** ). Ponadto nie można zagnieżdżać procedury obsługi wyjątku ani procedury zakończenia w bloku **__finally** .

Ponadto niektóre rodzaje kodu dozwolone w programie obsługi zakończenia dają wyniki z pytaniami, dlatego należy ich używać ostrożnie, jeśli w ogóle. Jednym z nich jest instrukcja **goto** , która przeskakuje z bloku instrukcji **__finally** . Jeśli blok jest wykonywany w ramach normalnego zakończenia, nic się nie dzieje. Ale jeśli system wychodzi z odwinięcia stosu, to odwracanie zostanie zatrzymane, a bieżąca funkcja uzyskuje kontrolę tak, jakby nie było nietypowego zakończenia.

Instrukcja **Return** w bloku instrukcji **__finally** przedstawia przybliżoną taką samą sytuację. Kontrolka powraca do bezpośredniego obiektu wywołującego funkcji, która zawiera procedurę obsługi zakończenia. Jeśli system spowodował odtworzenie stosu, ten proces jest zatrzymany, a program będzie kontynuował działanie tak, jakby nie został zgłoszony wyjątek.

## <a name="see-also"></a>Zobacz także

[Pisanie procedury obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
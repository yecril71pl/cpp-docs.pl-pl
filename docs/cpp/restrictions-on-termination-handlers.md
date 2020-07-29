---
title: Ograniczenia dotyczące programu obsługi zakończenia
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: d53792afbc3d25fb21edafa7817919b63b79ab65
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225894"
---
# <a name="restrictions-on-termination-handlers"></a>Ograniczenia dotyczące programu obsługi zakończenia

Nie można użyć **`goto`** instrukcji, aby przeskoczyć do bloku instrukcji **__try** lub **`__finally`** bloku instrukcji. Zamiast tego należy wprowadzić blok instrukcji za pomocą normalnego przepływu sterowania. (Można jednak wyskoczyć z bloku instrukcji **__try** ). Ponadto nie można zagnieżdżać procedury obsługi wyjątku ani procedury zakończenia w **`__finally`** bloku.

Ponadto niektóre rodzaje kodu dozwolone w programie obsługi zakończenia dają wyniki z pytaniami, dlatego należy ich używać ostrożnie, jeśli w ogóle. Jeden jest **`goto`** instrukcją, która przechodzi z **`__finally`** bloku instrukcji. Jeśli blok jest wykonywany w ramach normalnego zakończenia, nic się nie dzieje. Ale jeśli system wychodzi z odwinięcia stosu, to odwracanie zostanie zatrzymane, a bieżąca funkcja uzyskuje kontrolę tak, jakby nie było nietypowego zakończenia.

**`return`** Instrukcja wewnątrz **`__finally`** bloku instrukcji przedstawia przybliżoną taką samą sytuację. Kontrolka powraca do bezpośredniego obiektu wywołującego funkcji, która zawiera procedurę obsługi zakończenia. Jeśli system spowodował odtworzenie stosu, ten proces jest zatrzymany, a program będzie kontynuował działanie tak, jakby nie został zgłoszony wyjątek.

## <a name="see-also"></a>Zobacz także

[Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

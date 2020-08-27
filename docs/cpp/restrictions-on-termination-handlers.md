---
title: Ograniczenia dotyczące programu obsługi zakończenia
description: Ograniczenia dotyczące obsługi wyjątków o określonej strukturze.
ms.date: 08/24/2020
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: 60fdb4c2a105f2fce4a32f475563a04f8e7bfaf9
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898269"
---
# <a name="restrictions-on-termination-handlers"></a>Ograniczenia dotyczące programu obsługi zakończenia

Nie można użyć **`goto`** instrukcji, aby przeskoczyć do **`__try`** bloku instrukcji lub **`__finally`** bloku instrukcji. Zamiast tego należy wprowadzić blok instrukcji za pomocą normalnego przepływu sterowania. (Można jednak wyskoczyć z **`__try`** bloku instrukcji). Ponadto nie można zagnieżdżać programu obsługi wyjątków ani procedury obsługi zakończenia wewnątrz **`__finally`** bloku.

Niektóre rodzaje kodu dozwolone w programie obsługi zakończenia dają wyniki z pytaniami, dlatego należy ich używać ostrożnie, jeśli w ogóle. Jeden jest **`goto`** instrukcją, która przechodzi z **`__finally`** bloku instrukcji. Jeśli blok jest wykonywany w ramach normalnego zakończenia, nic się nie dzieje. Ale jeśli system nie powoduje odwinięcia stosu, zostanie zatrzymane. Następnie bieżąca funkcja uzyskuje kontrolę tak, jakby nie było nietypowego zakończenia.

**`return`** Instrukcja wewnątrz **`__finally`** bloku instrukcji przedstawia przybliżoną taką samą sytuację. Kontrolka powraca do bezpośredniego obiektu wywołującego funkcji, która zawiera program obsługi zakończenia. Jeśli system został rozwinięcia stosu, ten proces jest zatrzymany. Następnie program będzie kontynuował pracę, tak jakby nie został zgłoszony żaden wyjątek.

## <a name="see-also"></a>Zobacz też

[Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

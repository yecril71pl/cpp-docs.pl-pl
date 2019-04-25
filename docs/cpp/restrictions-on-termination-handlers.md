---
title: Ograniczenia dotyczące programu obsługi zakończenia
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: 7b092ee8682dfeef0c8151c56544e36427f40da0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244492"
---
# <a name="restrictions-on-termination-handlers"></a>Ograniczenia dotyczące programu obsługi zakończenia

Nie można użyć **goto** instrukcję, aby przejść do **__try** blok instrukcji lub **__finally** blok instrukcji. Zamiast tego musisz wprowadzić blok instrukcji za pomocą Normalny przepływ sterowania. (Możesz jednak przejść z **__try** blok instrukcji.) Ponadto nie można zagnieździć obsługi wyjątków lub program obsługi przerwania wewnątrz **__finally** bloku.

Ponadto niektóre rodzaje kodu, dozwolone w programu obsługi zakończenia dać wątpliwe wyników, więc należy ich używać z rozwagą, jeśli w ogóle. Jeden jest **goto** instrukcję, która przechodzi z **__finally** blok instrukcji. Jeśli blok jest wykonywany jako część normalnego zakończenia, nic nietypowe się nie dzieje. Ale jeśli system jest odwinięciu stosu, który zatrzymuje odwijania i bieżącą funkcję uzyska kontrolować tak, jakby nie było żadnych Nienormalne zakończenie.

A **zwracają** instrukcji wewnątrz **__finally** blok instrukcji przedstawia informacje o około samej sytuacji. Formant powraca do bezpośredniego obiektu wywołującego funkcji zawierający programu obsługi zakończenia. Jeśli system został odwinięciu stosu, ten proces jest zatrzymywane, a program będzie kontynuowane tak, jakby była nie wystąpił wyjątek.

## <a name="see-also"></a>Zobacz także

[Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
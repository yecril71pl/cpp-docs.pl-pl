---
title: Ograniczenia dotyczące programu obsługi zakończenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ab3e361fb8d1c0478ec019a9ed0a6ea4fec704e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059943"
---
# <a name="restrictions-on-termination-handlers"></a>Ograniczenia dotyczące programu obsługi zakończenia

Nie można użyć **goto** instrukcję, aby przejść do **__try** blok instrukcji lub **__finally** blok instrukcji. Zamiast tego musisz wprowadzić blok instrukcji za pomocą Normalny przepływ sterowania. (Możesz jednak przejść z **__try** blok instrukcji.) Ponadto nie można zagnieździć obsługi wyjątków lub program obsługi przerwania wewnątrz **__finally** bloku.

Ponadto niektóre rodzaje kodu, dozwolone w programu obsługi zakończenia dać wątpliwe wyników, więc należy ich używać z rozwagą, jeśli w ogóle. Jeden jest **goto** instrukcję, która przechodzi z **__finally** blok instrukcji. Jeśli blok jest wykonywany jako część normalnego zakończenia, nic nietypowe się nie dzieje. Ale jeśli system jest odwinięciu stosu, który zatrzymuje odwijania i bieżącą funkcję uzyska kontrolować tak, jakby nie było żadnych Nienormalne zakończenie.

A **zwracają** instrukcji wewnątrz **__finally** blok instrukcji przedstawia informacje o około samej sytuacji. Formant powraca do bezpośredniego obiektu wywołującego funkcji zawierający programu obsługi zakończenia. Jeśli system został odwinięciu stosu, ten proces jest zatrzymywane, a program będzie kontynuowane tak, jakby była nie wystąpił wyjątek.

## <a name="see-also"></a>Zobacz także

[Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
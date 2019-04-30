---
title: Ograniczenia dotyczące obsługi wyjątków
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 7d5bf20da61f4b9f5012b7f2aab932dfc904c302
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403363"
---
# <a name="restrictions-on-exception-handlers"></a>Ograniczenia dotyczące obsługi wyjątków

Główne ograniczenie używania programów obsługi wyjątków w kodzie jest, że nie można użyć **goto** instrukcję, aby przejść do **__try** blok instrukcji. Zamiast tego musisz wprowadzić blok instrukcji za pomocą Normalny przepływ sterowania. Możesz przejść z **__try** instrukcji zablokować, a także zagnieżdżać obsługi wyjątków, jak możesz wybrać.

## <a name="see-also"></a>Zobacz także

[Pisanie programu do obsługi wyjątku](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
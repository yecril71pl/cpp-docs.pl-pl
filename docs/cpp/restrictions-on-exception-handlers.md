---
title: Ograniczenia dotyczące obsługi wyjątków
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 1f80cb1574cbfef0783c7e55dcd198dfb822f566
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225907"
---
# <a name="restrictions-on-exception-handlers"></a>Ograniczenia dotyczące obsługi wyjątków

Głównym ograniczeniem korzystania z obsługi wyjątków w kodzie jest to, że nie można użyć **`goto`** instrukcji, aby przeskoczyć do bloku instrukcji **__try** . Zamiast tego należy wprowadzić blok instrukcji za pomocą normalnego przepływu sterowania. Możesz wyskoczyć z bloku instrukcji **__try** i zagnieździć obsługę wyjątków w miarę zaznaczania.

## <a name="see-also"></a>Zobacz także

[Pisanie procedury obsługi wyjątków](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

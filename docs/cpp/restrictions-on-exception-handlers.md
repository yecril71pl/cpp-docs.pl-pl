---
title: Ograniczenia dotyczące obsługi wyjątków
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 54bf4a44d06eacd22dc4b9819d160d3c6a66c684
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179084"
---
# <a name="restrictions-on-exception-handlers"></a>Ograniczenia dotyczące obsługi wyjątków

Głównym ograniczeniem do korzystania z obsługi wyjątków w kodzie jest to, że nie można użyć instrukcji **goto** , aby przejść do bloku instrukcji **__try** . Zamiast tego należy wprowadzić blok instrukcji za pomocą normalnego przepływu sterowania. Możesz wyskoczyć z bloku instrukcji **__try** i zagnieździć obsługę wyjątków w miarę zaznaczania.

## <a name="see-also"></a>Zobacz też

[Pisanie programu do obsługi wyjątku](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

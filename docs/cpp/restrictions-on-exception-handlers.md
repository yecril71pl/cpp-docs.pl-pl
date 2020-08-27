---
title: Ograniczenia dotyczące obsługi wyjątków
description: Opisuje ograniczenia dotyczące przechodzenia do bloków obsługi wyjątków strukturalnych.
ms.date: 08/24/2020
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: c4182f065789533bf7599621d8d2829b2d52d6ed
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898448"
---
# <a name="restrictions-on-exception-handlers"></a>Ograniczenia dotyczące obsługi wyjątków

Głównym ograniczeniem do korzystania z obsługi wyjątków w kodzie jest to, że nie można użyć **`goto`** instrukcji, aby przeskoczyć do **`__try`** bloku instrukcji. Zamiast tego należy wprowadzić blok instrukcji za pomocą normalnego przepływu sterowania. Możesz wyskoczyć z **`__try`** bloku instrukcji i zagnieżdżać obsługę wyjątków w miarę wyboru.

## <a name="see-also"></a>Zobacz też

[Pisanie programu do obsługi wyjątku](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

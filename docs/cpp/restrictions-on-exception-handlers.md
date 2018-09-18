---
title: Ograniczenia dotyczące obsługi wyjątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29a462f83bff3bab158e9bcf9fa7947efb56a79b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074477"
---
# <a name="restrictions-on-exception-handlers"></a>Ograniczenia dotyczące obsługi wyjątków

Główne ograniczenie używania programów obsługi wyjątków w kodzie jest, że nie można użyć **goto** instrukcję, aby przejść do **__try** blok instrukcji. Zamiast tego musisz wprowadzić blok instrukcji za pomocą Normalny przepływ sterowania. Możesz przejść z **__try** instrukcji zablokować, a także zagnieżdżać obsługi wyjątków, jak możesz wybrać.

## <a name="see-also"></a>Zobacz także

[Pisanie programu do obsługi wyjątku](../cpp/writing-an-exception-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
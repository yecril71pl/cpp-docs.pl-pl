---
title: Błąd matematyczny M6203 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6203
dev_langs:
- C++
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8474c91802b4756207676c466fdd28d66d911b3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022672"
---
# <a name="math-error-m6203"></a>Błąd matematyczny M6203

'Funkcja': błąd _OVERFLOW

Wynik daną funkcję była zbyt duża, aby mogły być reprezentowane.

Ten błąd wywołania `_matherr` funkcję z nazwy funkcji, argumentów i typ błędu. Można napisać ponownie `_matherr` funkcję, aby dostosować obsługi niektórych błędów zmiennoprzecinkowym zapisu matematycznego w czasie wykonywania.
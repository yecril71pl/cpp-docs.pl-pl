---
title: Błąd matematyczny M6202
ms.date: 11/04/2016
f1_keywords:
- M6202
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
ms.openlocfilehash: c216c4d01513868dd56f47c7d5ca7f8b734d1797
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393236"
---
# <a name="math-error-m6202"></a>Błąd matematyczny M6202

'Funkcja': błąd

Argument do danej funkcji była wartość singularity dla tej funkcji. Funkcja nie jest zdefiniowany dla tego argumentu.

Ten błąd wywołania `_matherr` funkcję z nazwy funkcji, argumentów i typ błędu. Można napisać ponownie `_matherr` funkcję, aby dostosować obsługi niektórych błędów zmiennoprzecinkowym zapisu matematycznego w czasie wykonywania.
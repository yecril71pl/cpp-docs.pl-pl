---
title: Błąd matematyczny M6108 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6108
dev_langs:
- C++
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1624a89b472733b4adb5563c8ba52e0b03dcaa2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048620"
---
# <a name="math-error-m6108"></a>Błąd matematyczny M6108

Pierwiastek kwadratowy

Argument operacji pierwiastek kwadratowy była ujemna.

Program kończy się z kodem zakończenia 136.

> [!NOTE]
>  `sqrt` Funkcji biblioteki wykonawczej C i Wewnętrzna funkcja FORTRAN **SQRT** nie generują tego błędu. C `sqrt` funkcja sprawdza, czy argument przed wykonaniem tej operacji i zwraca wartość błędu, jeśli argument jest ujemna. FORTRAN **SQRT** funkcja generuje błąd domeny [M6201](../../error-messages/tool-errors/math-error-m6201.md) zamiast tego błędu.
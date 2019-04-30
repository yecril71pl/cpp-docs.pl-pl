---
title: Błąd matematyczny M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: d60e9b6284c79828fda1f7af542fcf197f189ad0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393275"
---
# <a name="math-error-m6108"></a>Błąd matematyczny M6108

Pierwiastek kwadratowy

Argument operacji pierwiastek kwadratowy była ujemna.

Program kończy się z kodem zakończenia 136.

> [!NOTE]
>  `sqrt` Funkcji biblioteki wykonawczej C i Wewnętrzna funkcja FORTRAN **SQRT** nie generują tego błędu. C `sqrt` funkcja sprawdza, czy argument przed wykonaniem tej operacji i zwraca wartość błędu, jeśli argument jest ujemna. FORTRAN **SQRT** funkcja generuje błąd domeny [M6201](../../error-messages/tool-errors/math-error-m6201.md) zamiast tego błędu.
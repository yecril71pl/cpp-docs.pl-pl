---
title: Błąd matematyczny M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: c6bd403437ee5e55eaf4add288995d0e4aa76c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361969"
---
# <a name="math-error-m6108"></a>Błąd matematyczny M6108

pierwiastek kwadratowy

Operand w operacji pierwiastek kwadratowy był ujemny.

Program kończy się kodem zakończenia 136.

> [!NOTE]
> Funkcja `sqrt` w bibliotece czasu wykonywania języka C i funkcji wewnętrznej **FORTRAN SQRT** nie generuje tego błędu. Funkcja `sqrt` C sprawdza argument przed wykonaniem operacji i zwraca wartość błędu, jeśli argument jest ujemny. Funkcja FORTRAN **SQRT** generuje błąd domeny [M6201](../../error-messages/tool-errors/math-error-m6201.md) zamiast tego błędu.

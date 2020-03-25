---
title: Błąd matematyczny M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: 68e6ae823613d87eb01c443b564b46746259cd7b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173728"
---
# <a name="math-error-m6108"></a>Błąd matematyczny M6108

pierwiastek kwadratowy

Operand w operacji typu kwadratowego jest ujemny.

Program kończy pracę z kodem zakończenia 136.

> [!NOTE]
>  Funkcja `sqrt` w bibliotece środowiska uruchomieniowego C i Pascal wewnętrzna funkcja **sqrt** nie generują tego błędu. Funkcja C `sqrt` sprawdza argument przed wykonaniem operacji i zwraca wartość błędu, jeśli operand jest ujemny. Funkcja Pascal **sqrt** GENERUJE błąd domeny [matematyczny M6201](../../error-messages/tool-errors/math-error-m6201.md) zamiast tego błędu.

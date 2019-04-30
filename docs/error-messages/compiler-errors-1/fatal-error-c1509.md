---
title: Błąd krytyczny C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: efd5b9dd5cdd7ee174bc786c38d9dd841e2ad6ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397487"
---
# <a name="fatal-error-c1509"></a>Błąd krytyczny C1509

ograniczenie kompilatora: zbyt wiele stanów obsługi wyjątków w funkcji "function". Uprość funkcję

Kod przekracza limit wewnętrzny stanów obsługi wyjątków (32 768 stany).

Najczęstszą przyczyną jest to, czy funkcja zawiera złożone wyrażenie zmienne klasy zdefiniowane przez użytkownika i operatorów arytmetycznych.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Uprość wyrażenia przez przypisywanie typowych podwyrażenia zmiennych tymczasowych.

1. Funkcja split na mniejsze.
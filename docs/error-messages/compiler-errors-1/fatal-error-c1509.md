---
title: Błąd krytyczny C1509 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1509
dev_langs:
- C++
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 837ab5b7cf76b724726c6c52fbfe974d4da6ca85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033137"
---
# <a name="fatal-error-c1509"></a>Błąd krytyczny C1509

ograniczenie kompilatora: zbyt wiele stanów obsługi wyjątków w funkcji "function". Uprość funkcję

Kod przekracza limit wewnętrzny stanów obsługi wyjątków (32 768 stany).

Najczęstszą przyczyną jest to, czy funkcja zawiera złożone wyrażenie zmienne klasy zdefiniowane przez użytkownika i operatorów arytmetycznych.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Uprość wyrażenia przez przypisywanie typowych podwyrażenia zmiennych tymczasowych.

1. Funkcja split na mniejsze.
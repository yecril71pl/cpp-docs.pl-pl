---
title: Błąd krytyczny C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: f8fe301e25d9ecb5cc67397f9537e0bbd86c0627
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595627"
---
# <a name="fatal-error-c1067"></a>Błąd krytyczny C1067

ograniczenie kompilatora: Przekroczono limit 64 KB rozmiaru typu rekordu

Ten błąd może wystąpić, jeśli symbol ma również nazwę uzupełnioną przekraczającej 247 znaków.  Aby rozwiązać problem, Skróć nazwę symbolu.

Gdy kompilator generuje informacje o debugowaniu, emituje rekordów typu do definiowania typów w kodzie źródłowym.  Na przykład rekordów typu obejmują struktur proste i listy argumentów funkcji.  Niektóre z tych rekordów typu mogą być duże listy.

Obowiązuje limit 64 KB rozmiaru dowolnego typu rekordu.  Po przekroczeniu tego limitu 64K ten błąd będzie występować.

C1067 może również wystąpić, jeśli istnieje wiele symboli o długich nazwach, lub jeśli klasy, struktury lub Unii ma zbyt wiele elementów członkowskich.
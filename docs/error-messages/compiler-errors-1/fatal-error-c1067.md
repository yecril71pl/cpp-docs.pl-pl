---
title: Błąd krytyczny C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: f8fe301e25d9ecb5cc67397f9537e0bbd86c0627
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165856"
---
# <a name="fatal-error-c1067"></a>Błąd krytyczny C1067

ograniczenie kompilatora: Przekroczono limit 64 KB rozmiaru typu rekordu

Ten błąd może wystąpić, jeśli symbol ma również nazwę uzupełnioną przekraczającej 247 znaków.  Aby rozwiązać problem, Skróć nazwę symbolu.

Gdy kompilator generuje informacje o debugowaniu, emituje rekordów typu do definiowania typów w kodzie źródłowym.  Na przykład rekordów typu obejmują struktur proste i listy argumentów funkcji.  Niektóre z tych rekordów typu mogą być duże listy.

Obowiązuje limit 64 KB rozmiaru dowolnego typu rekordu.  Po przekroczeniu tego limitu 64K ten błąd będzie występować.

C1067 może również wystąpić, jeśli istnieje wiele symboli o długich nazwach, lub jeśli klasy, struktury lub Unii ma zbyt wiele elementów członkowskich.
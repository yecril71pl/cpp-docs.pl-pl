---
title: Błąd krytyczny C1067 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1067
dev_langs:
- C++
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f267e58617fbc68835fd3a387c4b635de4fd0530
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077675"
---
# <a name="fatal-error-c1067"></a>Błąd krytyczny C1067

ograniczenie kompilatora: Przekroczono limit 64 KB rozmiaru typu rekordu

Ten błąd może wystąpić, jeśli symbol ma również nazwę uzupełnioną przekraczającej 247 znaków.  Aby rozwiązać problem, Skróć nazwę symbolu.

Gdy kompilator generuje informacje o debugowaniu, emituje rekordów typu do definiowania typów w kodzie źródłowym.  Na przykład rekordów typu obejmują struktur proste i listy argumentów funkcji.  Niektóre z tych rekordów typu mogą być duże listy.

Obowiązuje limit 64 KB rozmiaru dowolnego typu rekordu.  Po przekroczeniu tego limitu 64K ten błąd będzie występować.

C1067 może również wystąpić, jeśli istnieje wiele symboli o długich nazwach, lub jeśli klasy, struktury lub Unii ma zbyt wiele elementów członkowskich.
---
title: Błąd krytyczny kompilatora zasobów RC1120 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1120
dev_langs:
- C++
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62f28e381d4eac0bfd1f010ef3919452635a1b96
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057005"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Błąd krytyczny kompilatora zasobów RC1120

za mało pamięci potrzebne liczba bajtów

Kompilator zasobów za mało pamięci masowej dla elementów, które przechowuje w swojej sterty. Zazwyczaj jest to wynikiem o zbyt wiele symboli.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Zwiększ obszar pliku wymiany Windows. Aby uzyskać więcej informacji na temat zwiększeniu ilości miejsca na plik wymiany Zobacz pamięci wirtualnej w Pomocy Windows.

1. Wyeliminuj niepotrzebne plików dołączanych, szczególnie niepotrzebne `#define`prototypy s i funkcji.

1. Podziel bieżący plik na dwa lub więcej plików i skompilować je oddzielnie.

1. Usuń inne programy lub sterowniki w systemie, który może być wykorzystywanie znacznej ilości pamięci.
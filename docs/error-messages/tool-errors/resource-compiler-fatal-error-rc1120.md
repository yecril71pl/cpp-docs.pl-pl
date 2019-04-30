---
title: Błąd krytyczny kompilatora zasobów RC1120
ms.date: 11/04/2016
f1_keywords:
- RC1120
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
ms.openlocfilehash: eff46ddee118c3355e548c73220b407db0561e36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374260"
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Błąd krytyczny kompilatora zasobów RC1120

za mało pamięci potrzebne liczba bajtów

Kompilator zasobów za mało pamięci masowej dla elementów, które przechowuje w swojej sterty. Zazwyczaj jest to wynikiem o zbyt wiele symboli.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Zwiększ obszar pliku wymiany Windows. Aby uzyskać więcej informacji na temat zwiększeniu ilości miejsca na plik wymiany Zobacz pamięci wirtualnej w Pomocy Windows.

1. Wyeliminuj niepotrzebne plików dołączanych, szczególnie niepotrzebne `#define`prototypy s i funkcji.

1. Podziel bieżący plik na dwa lub więcej plików i skompilować je oddzielnie.

1. Usuń inne programy lub sterowniki w systemie, który może być wykorzystywanie znacznej ilości pamięci.
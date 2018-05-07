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
ms.openlocfilehash: d117f7b106e14cde2def5477fab5ad0fc92a6411
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rc1120"></a>Błąd krytyczny kompilatora zasobów RC1120
za mało pamięci potrzebne liczba bajtów  
  
 Kompilator zasobów zabrakło pamięci masowej dla elementów, które są przechowywane w sterty. Zazwyczaj jest to wynik o zbyt wiele symboli.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Zwiększ miejsce pliku wymiany systemu Windows. Aby uzyskać więcej informacji o zwiększenie rozmiaru pliku wymiany Zobacz pamięci wirtualnej w Pomocy systemu Windows.  
  
2.  Usunąć niepotrzebne Dołącz pliki, zwłaszcza niepotrzebne `#define`prototypy s i funkcji.  
  
3.  Podziel bieżący plik na dwóch lub więcej plików i kompilowania ich osobno.  
  
4.  Usuń inne programy lub sterowniki uruchomiony w systemie, w którym można korzystać z znacznych ilości pamięci.
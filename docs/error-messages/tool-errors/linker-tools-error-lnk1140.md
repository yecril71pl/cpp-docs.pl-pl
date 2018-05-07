---
title: Błąd narzędzi konsolidatora LNK1140 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1140
dev_langs:
- C++
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc0d59589a1882aca4ef2deb419e1e4f1081e52b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1140"></a>Błąd narzędzi konsolidatora LNK1140
za dużo modułów dla bazy danych programu; Połącz z opcją/PDB: NONE  
  
 Projekt zawiera więcej niż 4096 modułów.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Połącz ponownie przy użyciu [/PDB: NONE](../../build/reference/pdb-use-program-database.md).  
  
2.  Kompiluj niektóre moduły bez informacji debugowania.  
  
3.  Zmniejsz liczbę modułów.
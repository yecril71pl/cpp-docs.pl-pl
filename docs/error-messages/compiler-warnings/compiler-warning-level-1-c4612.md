---
title: Kompilatora (poziom 1) ostrzeżenie C4612 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4612
dev_langs:
- C++
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0983f5d0bb89eaf1daee94468b318557bc83cd05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281885"
---
# <a name="compiler-warning-level-1-c4612"></a>Kompilator C4612 ostrzegawcze (poziom 1)
Błąd w nazwie pliku dołączanego  
  
 To ostrzeżenie występuje z **#pragma include_alias** gdy nazwa pliku jest nieprawidłowe lub niekompletne.  
  
 Argumenty **#pragma include_alias** instrukcji można użyć oferty z (**"***filename***"**) lub formularza nawiasu ostrego ( **\< ***filename***>**), ale jednocześnie muszą używać tego samego formularza.  
  
## <a name="example"></a>Przykład  
  
```  
// C4612.cpp  
// compile with: /W1 /LD  
#pragma include_alias("StandardIO", <stdio.h>) // C4612  
```
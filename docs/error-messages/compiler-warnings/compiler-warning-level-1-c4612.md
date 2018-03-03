---
title: "Kompilatora (poziom 1) ostrzeżenie C4612 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4612
dev_langs:
- C++
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 922da98a54a572462d2b247f6211a39bcaed9ec6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4612"></a>Kompilator C4612 ostrzegawcze (poziom 1)
Błąd w nazwie pliku dołączanego  
  
 To ostrzeżenie występuje z **#pragma include_alias** gdy nazwa pliku jest nieprawidłowe lub niekompletne.  
  
 Argumenty **#pragma include_alias** instrukcji można użyć oferty z (**"***filename***"**) lub formularza nawiasu ostrego ( **\<**  *filename***>**), ale jednocześnie muszą używać tego samego formularza.  
  
## <a name="example"></a>Przykład  
  
```  
// C4612.cpp  
// compile with: /W1 /LD  
#pragma include_alias("StandardIO", <stdio.h>) // C4612  
```
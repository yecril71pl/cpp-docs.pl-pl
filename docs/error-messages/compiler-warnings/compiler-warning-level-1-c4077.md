---
title: Kompilatora (poziom 1) ostrzeżenie C4077 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4077
dev_langs:
- C++
helpviewer_keywords:
- C4077
ms.assetid: c2d28805-b33f-41ad-afba-33b3f788c649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a558ff0ae3c33f25c4f07dc642607fd8a840c70c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4077"></a>Kompilator C4077 ostrzegawcze (poziom 1)
Nieznany check_stack — opcja  
  
 Stary formę **check_stack —** pragma jest używany z Nieznany argument. Argument musi być `+`, `-`, `(on)`, `(off)`, ani być pusta.  
  
 Kompilator ignoruje pragma i pozostawia sprawdzania stosu bez zmian.  
  
## <a name="example"></a>Przykład  
  
```  
// C4077.cpp  
// compile with: /W1 /LD  
#pragma check_stack yes // C4077  
#pragma check_stack +    // Correct old form  
#pragma check_stack (on) // Correct new form  
```
---
title: Kompilatora (poziom 1) ostrzeżenie C4606 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4606
dev_langs:
- C++
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf9f0a954b48e2c8bd036651efa3e8a3e65b8e68
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279461"
---
# <a name="compiler-warning-level-1-c4606"></a>Kompilator C4606 ostrzegawcze (poziom 1)
\#warning elementu pragma: "warning_number" ignorowane. Ostrzeżenia analizy kodu nie są skojarzone z poziomami ostrzeżeń  
  
 Ostrzeżenia analizy kodu, tylko `error`, `once`, i `default` są obsługiwane z [ostrzeżenie](../../preprocessor/warning.md) pragma.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4606.  
  
```  
// C4606.cpp  
// compile with: /c /W1  
#pragma warning(1: 6001)   // C4606  
#pragma warning(once: 6001)   // OK  
```
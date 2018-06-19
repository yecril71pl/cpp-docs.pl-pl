---
title: C3874 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3874
dev_langs:
- C++
helpviewer_keywords:
- C3874
ms.assetid: fd55fc05-69a7-4237-b3b7-dca1d5400b4f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb1224b1e5b14c0f34e10b7eff972d4014cccdff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268258"
---
# <a name="compiler-error-c3874"></a>C3874 błąd kompilatora
zwracany typ "funkcji" powinien być "int" zamiast "type"  
  
 Funkcja nie ma typ zwracany był oczekiwany przez kompilator.  
  
 Poniższy przykład generuje C3874:  
  
```  
// C3874b.cpp  
double main()  
{   // C3874  
}  
```
---
title: Kompilatora (poziom 3) ostrzeżenie C4646 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4646
dev_langs:
- C++
helpviewer_keywords:
- C4646
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36ff770877333042319b2a91dc5006e2ceb4118f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291219"
---
# <a name="compiler-warning-level-3-c4646"></a>Kompilator C4646 ostrzegawcze (poziom 3)
Funkcja zadeklarowana ze __declspec(noreturn) ma typ zwracany inny niż void  
  
 Funkcja oznaczona atrybutem [noreturn](../../cpp/noreturn.md) `__declspec` powinien mieć modyfikatora [void](../../cpp/void-cpp.md) typ zwracany.  
  
 Poniższy przykład generuje C4646:  
  
```  
// C4646.cpp  
// compile with: /W3 /WX  
int __declspec(noreturn) TestFunction()  
{   // C4646  make return type void  
}  
```
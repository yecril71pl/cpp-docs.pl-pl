---
title: "C3295 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3295
dev_langs: C++
helpviewer_keywords: C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b72e4839341006d2058c21a1523b0d7567f51696
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3295"></a>C3295 błąd kompilatora
"#pragma pragma" można używać tylko globalnie lub zakresie przestrzeni nazw  
  
 Nie można używać niektórych pragm w funkcji.  Zobacz [dyrektywy Pragma i słowo kluczowe __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3295.  
  
```  
// C3295.cpp  
int main() {  
   #pragma managed   // C3295  
}  
```
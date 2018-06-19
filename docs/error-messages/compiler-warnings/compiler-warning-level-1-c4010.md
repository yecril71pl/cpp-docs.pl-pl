---
title: Kompilatora (poziom 1) ostrzeżenie C4010 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4010
dev_langs:
- C++
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06ab6307a34887fe2d8a8719e20c31da9728664b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274657"
---
# <a name="compiler-warning-level-1-c4010"></a>Kompilator C4010 ostrzegawcze (poziom 1)
komentarz jednowierszowy zawiera znak kontynuacji wiersza  
  
 Komentarz jednowierszowy wprowadzone przez / / zawiera ukośnik odwrotny (\\) służy jako znak kontynuacji wiersza. Kompilator uwzględnia następnego wiersza kontynuacja i traktuje je jako komentarz.  
  
 Niektóre składni skierowane edytory nie wskazują wiersza po znaku kontynuacji jako komentarz. Ignoruj kolorowania na wszystkie wiersze, które powodują to ostrzeżenie.  
  
 Poniższy przykład generuje C4010:  
  
```  
// C4010.cpp  
// compile with: /WX  
int main() {  
   // the next line is also a comment because of the backslash \  
   int a = 3; // C4010  
   a++;  
}  
```
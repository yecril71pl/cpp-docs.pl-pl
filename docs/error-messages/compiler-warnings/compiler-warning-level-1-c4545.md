---
title: Kompilatora (poziom 1) ostrzeżenie C4545 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4545
dev_langs:
- C++
helpviewer_keywords:
- C4545
ms.assetid: 43f8f34f-ed46-4661-95c0-c588c577ff73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5f34dbdb420fffefdd07f79ae651002cfe67598
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278278"
---
# <a name="compiler-warning-level-1-c4545"></a>Kompilator C4545 ostrzegawcze (poziom 1)
wyrażenie przed przecinkiem daje w wyniku funkcję, dla której brakuje listy argumentów  
  
 Kompilator wykryto wyrażenie źle sformułowane przecinkami.  
  
 To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 Poniższy przykład generuje C4545:  
  
```  
// C4545.cpp  
// compile with: /W1  
#pragma warning (default : 4545)  
  
void f() { }  
  
int main()  
{  
   *(&f), 10;   // C4545  
   // try the following line instead  
   // (*(&f))(), 10;  
}  
```
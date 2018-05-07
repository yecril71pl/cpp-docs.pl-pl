---
title: Kompilatora (poziom 4) ostrzeżenie C4400 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4400
dev_langs:
- C++
helpviewer_keywords:
- C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7164b323e5108b44ea40da699ffb906508f731a2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4400"></a>Kompilator C4400 ostrzegawcze (poziom 4)
"type": kwalifikatory const/volatile dla tego typu nie są obsługiwane.  
  
 [Const](../../cpp/const-cpp.md)i [volatile](../../cpp/volatile-cpp.md)kwalifikatory nie będzie działać z zmiennymi popularnych typów środowiska wykonawczego języka.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4400.  
  
```  
// C4400.cpp  
// compile with: /clr /W4  
// C4401 expected  
using namespace System;  
#pragma warning (disable : 4101)  
int main() {  
   const String^ str;   // C4400  
   volatile String^ str2;   // C4400  
}  
```
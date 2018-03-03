---
title: "Kompilatora (poziom 4) ostrzeżenie C4400 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4400
dev_langs:
- C++
helpviewer_keywords:
- C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 615a315ff2d9ff3f517c0b046317400792760b73
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
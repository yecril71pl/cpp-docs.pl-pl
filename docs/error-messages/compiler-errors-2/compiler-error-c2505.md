---
title: "C2505 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2505
dev_langs: C++
helpviewer_keywords: C2505
ms.assetid: b19f5c53-399d-425e-90db-fe3ca9b40858
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e703a5f36a5edd5febbcfaf4b75394bbbb28ee4d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2505"></a>C2505 błąd kompilatora
"symbol": "__declspec(modifer)" można stosować do deklaracji lub definicji obiektów globalnych lub statyczne elementy członkowskie danych  
  
 A `__declspec` modyfikator, który ma być używane tylko w zakresie globalnym został użyty w funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [elementu appdomain](../../cpp/appdomain.md) i [procesu](../../cpp/process.md).  
  
 Poniższy przykład generuje C2505:  
  
```  
// C2505.cpp  
// compile with: /clr  
  
// OK  
__declspec(process) int ii;  
__declspec(appdomain) int jj;  
  
int main() {  
   __declspec(process) int i;   // C2505  
   __declspec(appdomain) int j;   // C2505  
}  
```
---
title: "C3890 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3890
dev_langs: C++
helpviewer_keywords: C3890
ms.assetid: 2f22c2fd-c14e-45e1-b936-b739ffc0b135
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3f98846bc8a361bd03d453f2115e2063f37423f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3890"></a>C3890 błąd kompilatora
"var": nie można przyjąć adresu literału elementu członkowskiego danych  
  
 Literał elementu członkowskiego danych istnieje na stercie zbierane pamięci.  Można przenieść obiektu na stercie zbierane pamięci, dlatego pobieranie adresu nie jest przydatne.  
  
 Poniższy przykład generuje C3890:  
  
```  
// C3890.cpp  
// compile with: /clr  
ref struct Y1 {  
   literal int staticConst = 9;  
};  
  
int main() {  
   int p = &Y1::staticConst;   // C3890  
   int p2 = Y1::staticConst;   // OK  
}  
```
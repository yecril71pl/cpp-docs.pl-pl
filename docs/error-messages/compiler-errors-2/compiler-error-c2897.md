---
title: "C2897 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2897
dev_langs: C++
helpviewer_keywords: C2897
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d3aa9ae6c79d3320104d9689f82b894cf2b76d9c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2897"></a>C2897 błąd kompilatora
destruktor/finalizator nie może być szablonem funkcji  
  
 Destruktory i finalizatory nie może zostać przeciążony, więc zadeklarowanie destruktora jako szablon (co może zdefiniować zestaw destruktory) nie jest dozwolone.  
  
 Poniższy przykład generuje C2897:  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2897.  
  
```  
// C2897.cpp  
// compile with: /c  
class X {  
public:  
   template<typename T> ~X() {}   // C2897  
};  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2897.  
  
```  
// C2897_b.cpp  
// compile with: /c /clr  
ref struct R2 {  
protected:  
   template<typename T> !R2(){}   // C2897 error  
};  
```
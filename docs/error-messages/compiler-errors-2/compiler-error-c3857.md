---
title: "C3857 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3857
dev_langs: C++
helpviewer_keywords: C3857
ms.assetid: 9f746d1e-9708-4945-bc29-3150d5371d3c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e9c553adf8eb9b326bcb2b3b35a381973c9c4a50
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3857"></a>C3857 błąd kompilatora
'type': wiele listy parametrów typu są niedozwolone.  
  
 Więcej niż jeden szablon lub ogólny został określony dla tego samego typu, co jest niedozwolone.  
  
 Poniższy przykład generuje C3857:  
  
```  
// C3857.cpp  
template <class T, class TT>  
template <class T2>    // C3857  
struct B {};  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C3857b.cpp  
// compile with: /c  
template <class T, class TT, class T2>   
struct B {};  
```  
  
 C3857 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C3857c.cpp  
// compile with: /clr  
generic <typename T>  
generic <typename U>  
ref class GC;   // C3857  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C3857d.cpp  
// compile with: /clr /c  
generic <typename U>  
ref class GC;  
```
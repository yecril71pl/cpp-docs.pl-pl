---
title: "Kompilatora (poziom 1) ostrzeżenie C4806 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4806
dev_langs:
- C++
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5bddda6bd683133f278f79544b2bf13aa132e131
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4806"></a>Kompilator C4806 ostrzegawcze (poziom 1)
"operacji": niebezpieczna operacja: żadna wartość typu "type", po której poziom jest podwyższany do typu "type" nie może być równa podanej stałej  
  
 Ten komunikat ostrzega względem kodu, takie jak `b == 3`, gdzie `b` ma typ `bool`. Wspieranie zasady Przyczyna `bool` się dopiero `int`. To jest dozwolony, ale nigdy nie może być **true**. Poniższy przykład generuje C4806:  
  
```  
// C4806.cpp  
// compile with: /W1  
int main()  
{  
   bool b = true;  
   // try..  
   // int b = true;  
  
   if (b == 3)   // C4806  
   {  
      b = false;  
   }  
}  
```
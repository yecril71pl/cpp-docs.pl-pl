---
title: "C3218 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3218
dev_langs: C++
helpviewer_keywords: C3218
ms.assetid: 0eea19e0-503e-4e07-ae8b-2cb2e95922cd
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 69ee49ece7354ce713fcfb86368aaca35b06cda7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3218"></a>C3218 błąd kompilatora
'type': typ nie jest dozwolony jako ograniczenia  
  
 Dla typu jako ograniczenie musi być typem wartości lub odwołania do zarządzanej klasy lub interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3218.  
  
```  
// C3218.cpp  
// compile with: /clr /c  
class A {};  
ref class B {};  
  
// Delete the following 3 lines to resolve.  
generic <class T>  
where T : A   // C3218  
ref class C {};  
  
// OK  
generic <class T>  
where  T : B  
ref class D {};  
```
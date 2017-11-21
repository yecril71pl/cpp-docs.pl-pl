---
title: "C3753 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3753
dev_langs: C++
helpviewer_keywords: C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 93150c018159a649e772406a5a9a96836b87da8a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3753"></a>C3753 błąd kompilatora
Właściwość generyczna nie jest dozwolone.  
  
 Listy generyczne parametrów może występować tylko w zarządzanej klasy, struktury lub funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [ogólne](../../windows/generics-cpp-component-extensions.md) i [właściwości](../../windows/property-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3753.  
  
```  
// C3753.cpp  
// compile with: /clr /c  
ref struct A {  
   generic <typename T>  
   property int i;   // C3753 error  
};  
```
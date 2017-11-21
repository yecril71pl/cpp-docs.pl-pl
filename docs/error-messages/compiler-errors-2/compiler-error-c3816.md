---
title: "C3816 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3816
dev_langs: C++
helpviewer_keywords: C3816
ms.assetid: 2e52cc7f-e31c-41a3-8d6f-9f5fab3648c0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 866a12639507488d8b9c34ab13ea72cf2239b5fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3816"></a>C3816 błąd kompilatora
poprzednio zadeklarowany lub zdefiniowane przy użyciu różnych zarządzane lub WinRTmodifier "deklaracją"  
  
 Deklaracja przekazująca dalej i rzeczywista deklaracja wymaga, aby nie istnieć żadne konflikty lub niespójności w deklaracji atrybutów.  
  
 Poniższy przykład generuje C3816 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C3816a.cpp  
// compile with: /clr /c  
class C1;  
// try the following line instead  
// ref class C1;  
  
ref class C1{  // C3816, forward declaration does not use ref  
};  
```
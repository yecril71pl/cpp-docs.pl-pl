---
title: "C3139 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3139
dev_langs: C++
helpviewer_keywords: C3139
ms.assetid: 95c92263-10ac-4ff3-b385-6312dd92adbc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2982e615e2e99bfa64cb73a707af703f04d1ebf0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3139"></a>C3139 błąd kompilatora
"struct": nie można eksportować UDT bez członków  
  
 Próbowano zastosować [wyeksportować](../../windows/export.md) atrybutu pusty UDT (typ zdefiniowany przez użytkownika). Na przykład:  
  
```  
// C3139.cpp  
#include "unknwn.h"  
[emitidl];  
[module(name=xx)];  
  
[export] struct MyStruct {   // C3139 empty type  
};  
int main(){}  
```
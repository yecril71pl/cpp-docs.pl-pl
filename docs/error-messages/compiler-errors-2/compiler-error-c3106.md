---
title: "C3106 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3106
dev_langs: C++
helpviewer_keywords: C3106
ms.assetid: 39d97a32-0905-4702-87d3-7f8ce473fb93
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 451c7dc0acc1d76e574ac64b9d40c2fae7ceb4ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3106"></a>C3106 błąd kompilatora
"attribute": nienazwane argumenty muszą poprzedzać nazwane argumenty  
  
 Nienazwane argumenty muszą być przekazywane do atrybutu przed nazwanymi argumentami.  
  
 Aby uzyskać więcej informacji, zobacz [zdefiniowane przez użytkownika atrybuty](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3106.  
  
```  
// C3106.cpp  
// compile with: /c  
[module(name="MyLib", dll)];   // C3106  
[module(dll, name="MyLib")];   // OK  
```
---
title: "C2581 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2581
dev_langs: C++
helpviewer_keywords: C2581
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 205d972237a71a05839dbc4236d248a11e6ee53d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2581"></a>C2581 błąd kompilatora
'type': statyczny "operator =" funkcji jest niedozwolone  
  
 Przypisanie (`=`) — operator jest niepoprawnie zadeklarowany jako `static`. Operatory przypisania nie może być `static`. Aby uzyskać więcej informacji, zobacz [operatory zdefiniowane przez użytkownika (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2581.  
  
```  
// C2581.cpp  
// compile with: /clr /c  
ref struct Y {  
   static Y ^ operator = (Y^ me, int i);   // C2581  
   Y^ operator =(int i);   // OK  
};  
```
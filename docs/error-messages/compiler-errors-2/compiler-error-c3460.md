---
title: "C3460 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3460
dev_langs:
- C++
helpviewer_keywords:
- C3460
ms.assetid: adbf8775-10ca-4654-acdf-58dd765351cd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a1184cc382a6c7f19e9a3b080e9850fdf7df74be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3460"></a>C3460 błąd kompilatora
'type': może być przekazywany tylko typ zdefiniowany przez użytkownika  
  
 Aby uzyskać więcej informacji, zobacz [przesyłania dalej typu (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy składnik.  
  
```  
// C3460.cpp  
// compile with: /LD /clr  
public ref class R {};  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3460.  
  
```  
// C3460_b.cpp  
// compile with: /clr /c  
#using "C3460.dll"  
[assembly:TypeForwardedTo(int::typeid)];   // C3460  
[assembly:TypeForwardedTo(R::typeid)];  
```
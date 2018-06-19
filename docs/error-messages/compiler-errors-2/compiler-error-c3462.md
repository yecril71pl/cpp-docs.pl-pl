---
title: C3462 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3462
dev_langs:
- C++
helpviewer_keywords:
- C3462
ms.assetid: 56b75f35-9fad-42d9-a969-eeca5d709bec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb5cfe5bc95c3530746bf263e340c5e3923abb42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254183"
---
# <a name="compiler-error-c3462"></a>C3462 błąd kompilatora
'type': tylko typu zaimportowany może być przekazywany  
  
 Atrybutu TypeForwardedTo należy zastosować do typu w metadanych do którego istnieje odwołanie.  
  
 Aby uzyskać więcej informacji, zobacz [przesyłania dalej typu (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy składnik.  
  
```  
// C3462.cpp  
// compile with: /clr /LD  
public ref class R {};  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3462.  
  
```  
// C3462b.cpp  
// compile with: /clr /c  
#using "C3462.dll"  
ref class N {};  
[assembly:TypeForwardedTo(N::typeid)];   // C3462  
[assembly:TypeForwardedTo(R::typeid)];  
```
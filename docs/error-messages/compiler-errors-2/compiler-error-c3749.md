---
title: C3749 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3749
dev_langs:
- C++
helpviewer_keywords:
- C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78de0c696123375c11e5c11e64223858b57451ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270778"
---
# <a name="compiler-error-c3749"></a>C3749 błąd kompilatora
'attribute': nie można użyć atrybutu niestandardowego wewnątrz funkcji  
  
 Atrybut niestandardowy nie można używać wewnątrz funkcji. Aby uzyskać więcej informacji dotyczących atrybutów niestandardowych, zobacz temat [atrybutu](../../windows/attribute.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3749:  
  
```  
// C3749a.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::All)]  
public ref struct ABC : public Attribute {  
   ABC() {}  
};  
  
void f1() { [ABC]; };  // C3749  
```  

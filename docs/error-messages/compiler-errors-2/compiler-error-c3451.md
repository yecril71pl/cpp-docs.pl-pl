---
title: C3451 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3451
dev_langs:
- C++
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a8aa09f0eb38364179be1608c3f230fe8059509
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250419"
---
# <a name="compiler-error-c3451"></a>C3451 błąd kompilatora
'attribute': nie można zastosować niezarządzanego atrybutu 'type'  
  
 Atrybut C++ nie można zastosować do typu CLR. Zobacz [atrybuty C++ — dokumentacja](../../windows/cpp-attributes-reference.md) Aby uzyskać więcej informacji.  
  
 Aby uzyskać więcej informacji, zobacz [zdefiniowane przez użytkownika atrybuty](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
 Ten błąd może być wygenerowanego w wyniku pracy zgodność kompilatora, która została wykonana dla Visual C++ 2005: [uuid](../../windows/uuid-cpp-attributes.md) atrybut nie jest dozwolony w atrybutem zdefiniowane przez użytkownika za pomocą programowania w języku środowiska CLR. Zamiast nich należy używać słów kluczowych <xref:System.Runtime.InteropServices.GuidAttribute>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3451.  
  
```  
// C3451.cpp  
// compile with: /clr /c  
using namespace System;  
[ attribute(AttributeTargets::All) ]  
public ref struct MyAttr {};  
  
[ MyAttr, helpstring("test") ]   // C3451  
// try the following line instead  
// [ MyAttr ]  
public ref struct ABC {};  
```
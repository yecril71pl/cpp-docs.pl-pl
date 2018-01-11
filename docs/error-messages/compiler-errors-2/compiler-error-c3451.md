---
title: "C3451 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3451
dev_langs: C++
helpviewer_keywords: C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb68c546a9064801c68844039b7de077d5ee7c17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
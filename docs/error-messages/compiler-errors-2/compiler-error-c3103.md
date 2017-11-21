---
title: "C3103 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3103
dev_langs: C++
helpviewer_keywords: C3103
ms.assetid: 7984bd3e-d51d-43e4-b6f4-08c1e9fb9704
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5bd4bdf877be1cb4af7ce8de82b6c16ae2c966f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3103"></a>C3103 błąd kompilatora
"argument": powtarzający się nazwany argument  
  
 Atrybut nie można powtórzyć nazwanych argumentów.  
  
 Aby uzyskać więcej informacji, zobacz [zdefiniowane przez użytkownika atrybuty](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3103.  
  
```  
// C3103.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::All)]  
public ref class Attr : public Attribute {  
public:  
   int m_t;  
};  
  
[Attr(m_t = 10, m_t = 1)]   // C3103  
// try the following line instead  
// [Attr(m_t = 10)]  
ref class A {};  
```
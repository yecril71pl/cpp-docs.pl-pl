---
title: "C3657 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3657
dev_langs: C++
helpviewer_keywords: C3657
ms.assetid: 89a28a18-4c17-43a1-bda6-deb52c32d203
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6b94c3388a3cdcdfaa4d450142e8cbb6ed4684d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3657"></a>C3657 błąd kompilatora
destruktory nie można jawnie przesłonić lub być jawnie przesłonięte  
  
 Destruktory i finalizatory nie może być jawnie przesłonięte. Aby uzyskać więcej informacji, zobacz [jawne zastąpienia](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3657.  
  
```  
// C3657.cpp  
// compile with: /clr  
public ref struct I {  
   virtual ~I() { }  
   virtual void a();  
};  
  
public ref struct D : I {  
   virtual ~D() = I::~I {}   // C3657  
   virtual void a() = I::a {}   // OK  
};  
```
---
title: "C3296 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3296
dev_langs: C++
helpviewer_keywords: C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 734f4e1e337833e26c60d4239a465818d8601ae5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3296"></a>C3296 błąd kompilatora
"właściwość": właściwość o tej nazwie już istnieje.  
  
 Kompilator Napotkano więcej niż jedną właściwość o tej samej nazwie. Każdej właściwości w typie musi mieć unikatową nazwę.  
  
 Aby uzyskać więcej informacji, zobacz [właściwości](../../windows/property-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3296.  
  
```  
// C3296.cpp  
// compile with: /clr /c  
using namespace System;  
  
ref class R {  
public:  
   property int MyProp[int] { int get(int); }  
  
   property String^ MyProp[int] { void set(int, String^); }   // C3296  
};  
```
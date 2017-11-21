---
title: "C3455 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3455
dev_langs: C++
helpviewer_keywords: C3455
ms.assetid: 218e5cfe-5391-4eeb-81c2-85c47e3a6cd2
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 98cdc956f93f7c0cdc2ae00fa1a0b6e5e26af75c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3455"></a>C3455 błąd kompilatora
"attribute": żaden z konstruktorów atrybutu nie pasuje argumentów  
  
 Nieprawidłowa wartość została użyta do zadeklarowania atrybutu.  Zobacz [atrybutu](../../windows/attribute.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3455.  
  
```  
// C3455.cpp  
// compile with: /clr /c  
using namespace System;  
  
[attribute("MyAt")]   // C3455  
// try the following line instead  
// [attribute(All)]  
ref struct MyAttr {  
   MyAttr() {}  
};  
```
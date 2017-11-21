---
title: "Kompilatora (poziom 3) ostrzeżenie C4570 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4570
dev_langs: C++
helpviewer_keywords: C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8bd962f6d8ada4a1241758b6c4ed726c7950159f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4570"></a>Kompilator C4570 ostrzegawcze (poziom 3)
'type': nie jest jawnie zadeklarowana jako abstrakcyjna, ale ma funkcje abstrakcyjne  
  
 Typ, który zawiera [abstrakcyjny](../../windows/abstract-cpp-component-extensions.md) funkcje powinien się być oznaczony jako abstrakcyjny.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4570.  
  
```  
// C4570.cpp  
// compile with: /clr /W3 /c  
ref struct X {   // C4570  
// try the following line instead  
// ref class X abstract {  
   virtual void f() abstract;  
};  
```
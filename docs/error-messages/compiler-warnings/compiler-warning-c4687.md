---
title: "C4687 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4687
dev_langs: C++
helpviewer_keywords: C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 266213deba94bdc925747d57dee184aca5f5f605
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4687"></a>C4687 ostrzeżenia kompilatora
"class": zapieczętowana klasa abstrakcyjna nie może implementować interfejsu "interface"  
  
 Zwykle typu zapieczętowanego "," abstract jest przydatna do przechowywania statycznych funkcji Członkowskich.  
  
 Aby uzyskać więcej informacji, zobacz [abstrakcyjny](../../windows/abstract-cpp-component-extensions.md)i [zapieczętowanego](../../windows/sealed-cpp-component-extensions.md).  
  
 Domyślnie C4687 jest wystawiana jako błąd. Można pominąć C4687 z [ostrzeżenie](../../preprocessor/warning.md) pragma. Jeśli chcesz implementować interfejs w typie zapieczętowanym, abstract, można pominąć C4687.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4687.  
  
```  
// C4687.cpp  
// compile with: /clr /c  
interface class A {};  
  
ref struct B sealed abstract : A {};   // C4687  
ref struct C sealed : A {};   // OK  
ref struct D abstract : A {};   // OK  
```
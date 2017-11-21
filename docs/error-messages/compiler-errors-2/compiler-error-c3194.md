---
title: "C3194 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3194
dev_langs: C++
helpviewer_keywords: C3194
ms.assetid: 49d3ffc6-eff6-4b46-865b-18811692a8bb
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4ddfc0c87f4f58850eec595dcf35436590177283
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3194"></a>C3194 błąd kompilatora
"członek": typ wartościowy nie może mieć operatora przypisania  
  
 Specjalne funkcje Członkowskie wymagające automatycznego wywołania przez kompilator, takich jak Konstruktor kopiujący lub kopia operatora przypisania nie są obsługiwane w klasie wartości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3194.  
  
```  
// C3194.cpp  
// compile with: /clr /c  
value struct MyStruct {  
   MyStruct& operator= (const MyStruct& i) { return *this; }   // C3194  
};  
  
ref struct MyStruct2 {  
   MyStruct2% operator= (const MyStruct2% i) { return *this; }   // OK  
};  
```
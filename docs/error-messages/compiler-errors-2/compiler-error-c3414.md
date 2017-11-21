---
title: "C3414 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3414
dev_langs: C++
helpviewer_keywords: C3414
ms.assetid: 715f5432-b509-4f8f-84f5-e1463bac490f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dff7fc5162fb84a4878553ec74953d8b7d42ddea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3414"></a>C3414 błąd kompilatora
"członek": nie można zdefiniować importowanej funkcji członkowskiej  
  
 Element członkowski został zdefiniowany w kodzie, który jest też definiowany w przywoływanym zestawie.  
  
 Poniższy przykład generuje C3414:  
  
```  
// C3414a2.cpp  
// compile with: /clr /LD  
public ref class MyClass {  
public:  
   void Test(){}  
};  
```  
  
 a następnie:  
  
```  
// C3414b2.cpp  
// compile with: /clr  
#using <C3414a2.dll>  
  
void MyClass::Test() {    // C3414  
}  
  
System::Object::Object() {    // C3414  
}  
```  

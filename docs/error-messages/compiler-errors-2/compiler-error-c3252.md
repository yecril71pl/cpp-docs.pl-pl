---
title: "C3252 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3252
dev_langs: C++
helpviewer_keywords: C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2123ad376530868afa1bacc987341905617e766b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3252"></a>C3252 błąd kompilatora
"metoda": nie można zredukować dostępności wirtualnej metody w zarządzanych lub typu WinRT  
  
 Klasa, która implementuje metody wirtualnej po klasie podstawowej lub dowolnej metody z interfejsu nie można zmniejszyć dostęp do tej metody.  
  
 Należy pamiętać, że wszystkie metody w interfejsie są publiczne.  
  
 Poniższy przykład generuje C3252 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C3252.cpp  
// compile with: /clr /c  
ref class A {  
public:  
   virtual void f1() {}  
};  
  
ref class B : public A {  
// To fix, uncomment the following line:   
// public:      
   virtual void f1() override sealed {}   // C3252, make this method public  
};  
```
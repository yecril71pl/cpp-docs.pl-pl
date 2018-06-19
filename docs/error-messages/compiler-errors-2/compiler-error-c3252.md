---
title: C3252 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3252
dev_langs:
- C++
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bc7ca0ccf3c973363e4427c89ccf497c20d1791
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256535"
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
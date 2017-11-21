---
title: "C3253 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3253
dev_langs: C++
helpviewer_keywords: C3253
ms.assetid: da40be26-0f78-4730-8727-ad11cddf8869
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5eae8e6bae423cb24e2a364ef59309d4110ccc49
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3253"></a>C3253 błąd kompilatora
"Funkcja": błąd z jawnym przesłanianiem  
  
 Jawne przesłanianie została określona nieprawidłowo. Na przykład nie można określić implementację określane również jako czysty zastąpienia. Aby uzyskać więcej informacji, zobacz [jawne zastąpienia](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
 Poniższy przykład generuje C3253:  
  
```  
// C3253.cpp  
// compile with: /clr  
public interface struct I {  
   void a();  
   void b();  
   void c();  
};  
  
public ref struct R : I {  
   virtual void a() = 0, I::a {}   // C3253  
   virtual void b() = I::a {}   // OK  
   virtual void c() = 0;   // OK  
};  
```
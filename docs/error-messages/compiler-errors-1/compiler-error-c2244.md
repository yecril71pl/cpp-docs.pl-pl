---
title: "C2244 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2244
dev_langs: C++
helpviewer_keywords: C2244
ms.assetid: d9911c12-ceb5-4f93-ac47-b44a485215c2
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4aae196f2acf59f8a06659e94583240ecd8a5653
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2244"></a>C2244 błąd kompilatora
'Identyfikator': nie można dopasować definicji funkcji do istniejącej deklaracji  
  
 Nietypowe zachowanie podczas stosowania Jednoargumentowy + — operator została użyta przed wywołanie funkcji, która nie ma nawiasu.  
  
 Ten błąd występuje tylko w projektach C++.  
  
 Poniższy przykład generuje C2244:  
  
```  
// C2244.cpp  
int func(char) {  
   return 0;  
}   
  
int func(int) {  
   return 0;  
}  
  
int main() {  
   +func;   // C2244  
}  
```  
  
 C2244 może również wystąpić, gdy podpisu Niepoprawna funkcja służy do funkcji członkowskiej klasy szablonu klasy.  
  
```  
// C2244b.cpp  
// compile with: /c  
template<class T>   
class XYZ {  
   void func(T t);  
};  
  
template<class T>  
void XYZ<T>::func(int i) {}   // C2244 wrong function signature  
// try the following line instead  
// void XYZ<T>::func(T t) {}  
```  
  
 C2244 może również wystąpić, gdy podpisu Niepoprawna funkcja jest używana dla elementu członkowskiego szablonu funkcji.  
  
```  
// C2244c.cpp  
// compile with: /c  
class ABC {  
   template<class T>   
   void func(int i, T t);  
};  
  
template<class T>  
void ABC::func(int i) {}   // C2244 wrong signature  
// try the following line instead  
// void ABC::func(int i, T t) {}  
```  
  
 Częściowo nie można specjalizować szablonu funkcji.  
  
```  
// C2244d.cpp  
template<class T, class U>  
class QRS {  
   void func(T t, U u);  
};  
  
template<class T>  
void QRS<T,int>::func(T t, int u) {}   // C2244  
```
---
title: "C3672 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3672
dev_langs: C++
helpviewer_keywords: C3672
ms.assetid: da971041-1766-467a-aecf-1d8655c6cb7a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f01237ca5ac90ea3def4a6d2733ef8dd700bf738
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3672"></a>C3672 błąd kompilatora
wyrażenie pseudo-destruktora może służyć jedynie jako część wywołania funkcji  
  
 Destruktor została niepoprawnie wywołana.  Aby uzyskać więcej informacji, zobacz [destruktory](../../cpp/destructors-cpp.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3672.  
  
```  
// C3672.cpp  
template<typename T>  
void f(T* pT) {  
   &pT->T::~T;   // C3672  
   pT->T::~T();   // OK  
};  
  
int main() {  
   int i;  
   f(&i);  
}  
```
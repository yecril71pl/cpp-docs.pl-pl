---
title: "C2765 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2765
dev_langs: C++
helpviewer_keywords: C2765
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f0caf89da3e3bf227d296df36d499b6d19096dfa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2765"></a>C2765 błąd kompilatora
"Funkcja": jawna specjalizacja szablonu funkcji nie może mieć argumentów domyślnych  
  
 Argumenty domyślne są niedozwolone w jawnej specjalizacji szablonu funkcji. Aby uzyskać więcej informacji, zobacz [jawna specjalizacja szablonów funkcji](../../cpp/explicit-specialization-of-function-templates.md).  
  
 Poniższy przykład generuje C2765:  
  
```  
// C2765.cpp  
template<class T> void f(T t) {};  
  
template<> void f<char>(char c = 'a') {}   // C2765  
// try the following line instead  
// template<> void f<char>(char c) {}  
```
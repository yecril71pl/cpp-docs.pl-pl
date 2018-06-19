---
title: C2765 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2765
dev_langs:
- C++
helpviewer_keywords:
- C2765
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 926cc1657db67530f866a2b2e00e4b23f4ccd0bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234587"
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
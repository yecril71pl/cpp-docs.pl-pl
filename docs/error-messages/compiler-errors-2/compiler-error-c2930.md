---
title: C2930 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2930
dev_langs:
- C++
helpviewer_keywords:
- C2930
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d2d1890b86292cec062d64e1fe56c5769178444
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247875"
---
# <a name="compiler-error-c2930"></a>C2930 błąd kompilatora
"class": typ klasy identyfikator ponownie zdefiniować jako moduł wyliczający "enum identyfikatora"  
  
 Klasy ogólne lub szablonu nie można użyć jako elementu członkowskiego wyliczenia.  
  
 Ten błąd może być spowodowany nieprawidłowo są dopasowywane w nawiasach klamrowych.  
  
 Poniższy przykład generuje C2930:  
  
```  
// C2930.cpp  
// compile with: /c  
template<class T>   
class x{};  
enum SomeEnum { x };   // C2930  
  
class y{};  
enum SomeEnum { y };  
```  
  
 C2930 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2930c.cpp  
// compile with: /clr /c  
generic<class T>   
ref struct GC {};  
enum SomeEnum { GC };   // C2930  
  
ref struct GC2 {};  
enum SomeEnum2 { GC2 };  
```
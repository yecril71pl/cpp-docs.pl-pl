---
title: C3181 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3181
dev_langs:
- C++
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33d5c42ce7fec65b2b4481b46590396f3af7d97a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252166"
---
# <a name="compiler-error-c3181"></a>C3181 błąd kompilatora
'type': nieprawidłowy operand dla operatora  
  
Przekazano nieprawidłowy parametr do [typeid](../../windows/typeid-cpp-component-extensions.md) operatora. Parametr musi być typu zarządzanego.  
  
Należy pamiętać, że kompilator używa aliasów dla natywnych typów, które mapują do typów w środowisko uruchomieniowe języka wspólnego.  
  
Poniższy przykład generuje C3181:  
  
```  
// C3181a.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181  
   Type ^pType2 = int::typeid;   // OK  
}  
```  

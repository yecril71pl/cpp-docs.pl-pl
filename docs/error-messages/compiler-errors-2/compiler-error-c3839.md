---
title: C3839 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3839
dev_langs:
- C++
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbb5541e07d168df36bae83f81b7b8a8a7273665
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3839"></a>C3839 błąd kompilatora
Nie można zmienić wyrównania w zarządzanych lub typu WinRT  
  
 Wyrównanie zmiennych w zarządzanych lub typów środowiska wykonawczego systemu Windows jest kontrolowany przez CLR lub środowiska wykonawczego systemu Windows i nie można modyfikować [Dopasuj](../../cpp/align-cpp.md).  
  
 Poniższy przykład generuje C3839:  
  
```  
// C3839a.cpp  
// compile with: /clr  
ref class C  
{  
public:  
   __declspec(align(32)) int m_j; // C3839  
};  
  
int main()  
{  
}  
```
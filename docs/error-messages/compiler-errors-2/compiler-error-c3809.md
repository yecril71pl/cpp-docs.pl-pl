---
title: C3809 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3809
dev_langs:
- C++
helpviewer_keywords:
- C3809
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4b9fabec4da63bfe881e0020e99cd5c49a51789
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273043"
---
# <a name="compiler-error-c3809"></a>C3809 błąd kompilatora
"class": zarządzanego lub typu WinRT nie może mieć żadnych friend funkcji/klas/interfejsów  
  
 Typy zarządzane i środowiska wykonawczego systemu Windows nie zezwalaj na dodawanie znajomych. Aby naprawić ten błąd nie deklaruj znajomych w zarządzanych lub typów środowiska wykonawczego systemu Windows.  
  
 Poniższy przykład generuje C3809:  
  
```  
// C3809a.cpp  
// compile with: /clr  
ref class A {};  
  
ref class B  
{  
public:  
   friend ref class A;   // C3809  
};  
  
int main()  
{  
}  
```
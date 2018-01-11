---
title: "C3809 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3809
dev_langs: C++
helpviewer_keywords: C3809
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22b4406676ced6c2a96241eb15a4329d8933b777
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
---
title: "C3836 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3836
dev_langs:
- C++
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed48f6fd044ccc17dacd79d774f8db2c6888a0cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3836"></a>C3836 błąd kompilatora
Konstruktor statyczny nie może mieć listy inicjatorów elementu członkowskiego  
  
 Zarządzanej klasy nie może mieć statycznego konstruktora, który ma także listy inicjowania elementu członkowskiego. Konstruktory statyczne klasy są wywoływane przez środowisko uruchomieniowe języka wspólnego do klasy inicjowania inicjowanie danych statycznych elementów członkowskich.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3836:  
  
```  
// C3836a.cpp  
// compile with: /clr  
ref class M  
{  
   static int s_i;  
  
public:  
   static M() :  s_i(1234)   // C3836, delete initializer to resolve  
   {  
   }  
};  
  
int main()  
{  
}  
```  

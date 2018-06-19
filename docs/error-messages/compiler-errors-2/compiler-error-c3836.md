---
title: C3836 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3836
dev_langs:
- C++
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45a2eda2567e63771ed4c8919945e34ee41be1cb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267397"
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

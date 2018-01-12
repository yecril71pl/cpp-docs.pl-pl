---
title: "C3465 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3465
dev_langs: C++
helpviewer_keywords: C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b7706779684158da8b1bc7187621420e52a640a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3465"></a>C3465 błąd kompilatora
Aby użyć typu "type" musi odwoływać się do zestawu "assembly"  
  
 Przekazywanie dalej typu będzie działać dla aplikacji klienckiej, dopóki nie zostanie ponownie skompilować klienta. Gdy zostanie ponownie skompilowana, konieczne będzie odwołania dla każdego zestawu zawierającego definicję typu używana w aplikacji klienta.  
  
 Aby uzyskać więcej informacji, zobacz [przesyłania dalej typu (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy zestaw, który zawiera nową lokalizację typu.  
  
```  
// C3465.cpp  
// compile with: /clr /LD  
public ref class R {  
public:  
   ref class N {};  
};  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy zestawu, który zawiera definicję typu, ale zawiera teraz składni przesyłania dalej dla typu.  
  
```  
// C3465_b.cpp  
// compile with: /clr /LD  
#using "C3465.dll"  
[ assembly:TypeForwardedTo(R::typeid) ];  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3465.  
  
```  
// C3465_c.cpp  
// compile with: /clr  
// C3465 expected  
#using "C3465_b.dll"  
// Uncomment the following line to resolve.  
// #using "C3465.dll"  
  
int main() {  
   R^ r = gcnew R();  
}  
```
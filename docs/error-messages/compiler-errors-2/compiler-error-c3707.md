---
title: C3707 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3707
dev_langs:
- C++
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7268f584d9f269b4f2f15b837379ec12ab0185d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3707"></a>C3707 błąd kompilatora
"Funkcja": metoda dispinterface musi posiadać identyfikator dispid  
  
 Jeśli używasz `dispinterface` metody, należy go przypisać `dispid`. Aby naprawić ten błąd, należy przypisać `dispid` do `dispinterface` metody, na przykład usunięcie komentarza `id` atrybutu w metodzie w poniższym przykładzie. Aby uzyskać więcej informacji, zobacz atrybuty [dispinterface](../../windows/dispinterface.md) i [identyfikator](../../windows/id.md).  
  
 Poniższy przykład generuje C3707:  
  
```  
// C3707.cpp  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(name="xx")];  
[dispinterface]  
__interface IEvents : IDispatch  
{  
   HRESULT event1([in] int i);   // C3707  
   // try the following line instead  
   // [id(1)] HRESULT event1([in] int i);  
};  
  
int main() {  
}  
```
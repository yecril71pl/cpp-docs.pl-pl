---
title: "C3707 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3707
dev_langs: C++
helpviewer_keywords: C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e3c61c23c093106267b4854109a8cfeb699bda78
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
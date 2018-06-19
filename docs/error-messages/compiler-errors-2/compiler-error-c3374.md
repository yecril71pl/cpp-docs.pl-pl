---
title: C3374 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3374
dev_langs:
- C++
helpviewer_keywords:
- C3374
ms.assetid: 41431299-bd20-47d4-a0c8-1334dd79018b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd06f0e63ab1c467b9359c38ad77056440535aba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253895"
---
# <a name="compiler-error-c3374"></a>C3374 błąd kompilatora
Nie można przyjąć adresu "funkcji", chyba że podczas tworzenia wystąpienia delegata  
  
 Adres funkcji została wykonana w kontekście innym niż utworzenie wystąpienia obiektu delegowanego.  
  
 Poniższy przykład generuje C3374:  
  
```  
// C3374.cpp  
// compile with: /clr  
public delegate void MyDel(int i);  
  
ref class A {  
public:  
   void func1(int i) {  
      System::Console::WriteLine("in func1 {0}", i);  
   }  
};  
  
int main() {  
   &A::func1;   // C3374  
  
   // OK  
   A ^ a = gcnew A;  
   MyDel ^ StaticDelInst = gcnew MyDel(a, &A::func1);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: definiowanie obiektów delegowanych (C++/CLI) oraz korzystanie z nich](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)
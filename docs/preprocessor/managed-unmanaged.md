---
title: "zarządzane, niezarządzane | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
dev_langs: C++
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 38047e535c53a1f463e3c0a7c5d210fab480cb71
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="managed-unmanaged"></a>zarządzane, niezarządzane
Kontrola funkcji na poziomie obliczania funkcji jako zarządzane lub niezarządzane.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      #pragma managed  
#pragma unmanaged  
#pragma managed([push,] on | off)  
#pragma managed(pop)  
```  
  
## <a name="remarks"></a>Uwagi  
 [/CLR](../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora można kontrolować poziom modułu dla kompilowania funkcji jako zarządzane lub niezarządzane.  
  
 Funkcji niezarządzanej zostanie skompilowany dla platformy natywnego, a wykonanie tej części, program zostanie przekazany do natywnego platformy przez środowisko uruchomieniowe języka wspólnego.  
  
 Funkcje są kompilowane jako zarządzany domyślnie podczas **/CLR** jest używany.  
  
 Podczas stosowania tych pragm:  
  
-   Dodaj pragma poprzedzających funkcji, ale nie w treści funkcji.  
  
-   Dodaj pragma po `#include` instrukcje. Nie należy używać tych pragm przed `#include` instrukcje.  
  
 Kompilator ignoruje `managed` i `unmanaged` pragm Jeśli **/CLR** nie jest używany w kompilacji.  
  
 Podczas tworzenia wystąpienia klasy funkcji szablonu stan pragma w czasie definicji szablonu określa, czy ma zarządzane lub niezarządzane.  
  
 Aby uzyskać więcej informacji, zobacz [inicjowanie zestawów mieszanych](../dotnet/initialization-of-mixed-assemblies.md).  
  
## <a name="example"></a>Przykład  
  
```cpp  
// pragma_directives_managed_unmanaged.cpp  
// compile with: /clr  
#include <stdio.h>  
  
// func1 is managed  
void func1() {  
   System::Console::WriteLine("In managed function.");  
}  
  
// #pragma unmanaged  
// push managed state on to stack and set unmanaged state  
#pragma managed(push, off)  
  
// func2 is unmanaged  
void func2() {  
   printf("In unmanaged function.\n");  
}  
  
// #pragma managed  
#pragma managed(pop)  
  
// main is managed  
int main() {  
   func1();  
   func2();  
}  
```  
  
```Output  
In managed function.  
In unmanaged function.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
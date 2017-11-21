---
title: fenv_access | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d2f95187be09177fea573181f1e3a827409fb77c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fenvaccess"></a>fenv_access
Wyłącza (ON) lub włącza (funkcje optymalizacji, które można zmienić flagi testów i zmiany trybu wyłączone).  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma fenv_access [ON | OFF]  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie `fenv_access` ma wartość OFF.  
  
 Aby uzyskać więcej informacji dotyczących zachowania zmiennoprzecinkowego, zobacz [/fp (określenie zachowania Floating-Point)](../build/reference/fp-specify-floating-point-behavior.md).  
  
 Rodzaje funkcje optymalizacji, które podlegają `fenv_access` są:  
  
-   Globalne eliminacja wspólnych podwyrażeń  
  
-   Kod ruchu  
  
-   Składania stałej  
  
 Inne zmiennoprzecinkowych pragm obejmują:  
  
-   [float_control](../preprocessor/float-control.md)  
  
-   [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>Przykład  
  
```  
// pragma_directive_fenv_access_x86.cpp  
// compile with: /O2  
// processor: x86  
#include <stdio.h>  
#include <float.h>   
#include <errno.h>  
#pragma fenv_access (on)  
  
int main() {  
   double z, b = 0.1, t = 0.1;  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);  
   if (err != 0) {  
      printf_s("The function _controlfp_s failed!\n");  
      return -1;  
   }  
   z = b * t;  
   printf_s ("out=%.15e\n",z);  
}  
```  
  
```Output  
out=9.999999776482582e-003  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dotyczy kompilatora produkujących plików wyjściowych dla procesorach Itanium. **/ FP: precise** zachowuje wyników pośrednich w rozszerzona dokładność, których wartości większe niż flt_max — (3.402823466e + 38F), może zostać obliczona i w wyniku tej sumy będą mieć wynik 1.0, jak powinno Jeśli ręcznie obliczana. **/ FP: strict** przechowuje pośredniego powoduje ich dokładności źródła (float), dodanie pierwszy tworzy nieskończoności, który jest przechowywany w wyrażeniu.  
  
```  
// pragma_directive_fenv_access_IPF.cpp  
// compile with: /O2 /fp:precise  
// processor: IPF  
// compiling with /fp:precise prints 1.0F  
// compile with /fp:strict to print infinity  
  
#include <stdio.h>  
float arr[5] = {3.402823465e+38F,   
               3.402823462e+38F,  
               3.402823464e+38F,  
               3.402823463e+38F,  
               1.0F};  
  
int main() {  
   float sum = 0;  
   sum = arr[0] + arr[1] - arr[2] - arr[3] + arr[4];  
   printf_s("%f\n", sum);  
}  
```  
  
```Output  
1.000000  
```  
  
## <a name="example"></a>Przykład  
 Podczas dodawania komentarzy limit `#pragma fenv_access (on)` od poprzedniej próbki, należy pamiętać, że dane wyjściowe różnych ponieważ kompilator jest oceny kompilacji, która nie używa trybu formantu.  
  
```  
// pragma_directive_fenv_access_2.cpp  
// compile with: /O2  
#include <stdio.h>  
#include <float.h>   
  
int main() {  
   double z, b = 0.1, t = 0.1;  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);  
   if (err != 0) {  
      printf_s("The function _controlfp_s failed!\n");  
      return -1;  
   }  
   z = b * t;  
   printf_s ("out=%.15e\n",z);  
}  
```  
  
```Output  
out=1.000000000000000e-002  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
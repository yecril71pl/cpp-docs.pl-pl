---
title: float_control | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
dev_langs: C++
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 821890c7fdb719b5ab320588476bd1ebb73793ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="floatcontrol"></a>float_control
Określa zachowania zmiennoprzecinkowego dla funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## <a name="flags"></a>Flagi  
 `value`, `setting` **[wypychania]**  
 Określa zachowanie zmiennoprzecinkowych. `value`może być **dokładne** lub **z wyjątkiem**. Aby uzyskać więcej informacji, zobacz [/fp (określenie zachowania Floating-Point)](../build/reference/fp-specify-floating-point-behavior.md). `setting`można albo być **na** lub **poza**.  
  
 Jeśli `value` jest **dokładne**, ustawienia **dokładne** i **z wyjątkiem** określania. **z wyjątkiem** można ustawić tylko na **na** podczas **dokładne** również ustawiono **na**.  
  
 Jeśli opcjonalny **wypychania** token zostanie dodany, bieżące ustawienia dla `value` spoczywa stos wewnętrznych kompilatora.  
  
 **push**  
 Wypychanie bieżącej `float_control` ustawienie na stosie wewnętrznych kompilatora  
  
 **POP**  
 Usuwa `float_control` z góry stosu wewnętrznego kompilatora i sprawia, że nowe `float_control` ustawienie.  
  
## <a name="remarks"></a>Uwagi  
 Nie można włączyć `float_control precise` wyłączone podczas **z wyjątkiem** znajduje się na. Podobnie **dokładne** nie może być wyłączone podczas `fenv_access` znajduje się na. Aby przejść z ograniczeniami modelu do szybkiego modelu z `float_control` pragma, użyj następującego kodu:  
  
```  
#pragma float_control(except, off)  
#pragma fenv_access(off)  
#pragma float_control(precise, off)  
// The following line is needed on Itanium processors  
#pragma fp_contract(on)  
```  
  
 Przechodzenie od szybkiego modelu do modelu ograniczeniami z `float_control` pragma, użyj następującego kodu:  
  
```  
#pragma float_control(precise, on)  
#pragma fenv_access(on)  
#pragma float_control(except, on)  
// The following line is needed on Itanium processors.  
#pragma fp_contract(off)  
```  
  
 Inne zmiennoprzecinkowych pragm obejmują:  
  
-   [fenv_access](../preprocessor/fenv-access.md)  
  
-   [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób catch przepełnienie zmiennoprzecinkowej wyjątek przy użyciu pragma `float_control`.  
  
```  
// pragma_directive_float_control.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <float.h>  
  
double func( ) {  
   return 1.1e75;  
}  
  
#pragma float_control (except,on)  
  
int main( ) {  
   float u[1];  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);  
   if (err != 0)  
      printf_s("_controlfp_s failed!\n");  
  
   try  {  
      u[0] = func();  
      printf_s ("Fail");     
      return(1);  
   }   
  
   catch (...)  {  
      printf_s ("Pass");  
      return(0);  
   }  
}  
```  
  
```Output  
Pass  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
---
title: float_control | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
dev_langs:
- C++
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9b94e5b8eccdc63735c7cb25faa7eacb1e23670
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466127"
---
# <a name="floatcontrol"></a>float_control
Określa zachowanie liczb zmiennopozycyjnych dla funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## <a name="flags"></a>Flagi  
 
*wartość*, *ustawienie* *[wypychanych]*  
Określa zachowanie liczb zmiennopozycyjnych. *wartość* może być `precise` lub `except`. Aby uzyskać więcej informacji, zobacz [/FP (określenie zachowania zmiennopozycyjna)](../build/reference/fp-specify-floating-point-behavior.md). *ustawienie* albo można `on` lub `off`.  
  
Jeśli *wartość* jest `precise`, ustawienia `precise` i `except` określania. `except` można ustawić tylko `on` podczas `precise` jest również ustawiona na `on`.  
  
Jeśli opcjonalny *wypychania* token zostanie dodany, bieżące ustawienie *wartość* zostanie przypisany wewnętrznym stosie kompilatora.  
  
*push*  
Wypychanie bieżącej **float_control** ustawienie na wewnętrznym stosie kompilatora  
  
*POP*  
Usuwa **float_control** ustawienie z góry wewnętrznego stosu kompilatora i sprawia, że nowe **float_control** ustawienie.  
  
## <a name="remarks"></a>Uwagi  
 
Nie można włączyć `float_control precise` wyłączone, gdy `except` znajduje się na. Podobnie `precise` nie może być wyłączone podczas `fenv_access` znajduje się na. Można przejść od modelu strict do szybkiego model przy użyciu **float_control** pragma, użyj następującego kodu:  
  
```  
#pragma float_control(except, off)  
#pragma fenv_access(off)  
#pragma float_control(precise, off)  
```  
  
Można przejść od szybkie modelu do modelu ściśle z **float_control** pragma, użyj następującego kodu:  
  
```  
#pragma float_control(precise, on)  
#pragma fenv_access(on)  
#pragma float_control(except, on)  
```  
  
Inne zmiennoprzecinkowych pragm, obejmują:  
  
- [fenv_access](../preprocessor/fenv-access.md)  
  
- [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>Przykład  
 
Poniższy przykład pokazuje, jak catch przepełnienie zmiennoprzecinkowej wyjątek za pomocą pragmy **float_control**.  
  
```cpp  
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

---
title: _ReturnAddress | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ReturnAddress
dev_langs:
- C++
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0431302ae745a1e4a03da4b3fd660fda7d2cfa72
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="returnaddress"></a>_ReturnAddress
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 `_ReturnAddress` Wewnętrzne dostarcza adres instrukcji w wywołania funkcji, która zostanie wykonana po powrocie sterowania do obiektu wywołującego.  
  
 Kompilacja następujących programów i wykonywania krokowego w debugerze. Podczas wykonywania kroków przez program, należy pamiętać, adres, który jest zwracany z `_ReturnAddress`. Następnie natychmiast, po powrocie z funkcji gdzie `_ReturnAddress` został użyty, otwórz [porady: Korzystanie z okna dezasemblacji](/visualstudio/debugger/how-to-use-the-disassembly-window) i należy pamiętać, że adres następną instrukcję do wykonania odpowiada adresowi zwrócony z `_ReturnAddress`.  
  
 Optymalizacje, takich jak ze śródwierszowaniem może mieć wpływ na adres zwrotny. Na przykład poniższy przykładowy program jest skompilowana przy użyciu [/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` będzie wbudowana w funkcji wywołującej `main`. W związku z tym wywołań `_ReturnAddress` z `inline_func` i `main` każdego utworzy tę samą wartość.  
  
 Podczas `_ReturnAddress` jest używany w programie skompilowane z [/CLR](../build/reference/clr-common-language-runtime-compilation.md), zawierający funkcja `_ReturnAddress` wywołanie zostanie skompilowany, ponieważ funkcja macierzystego. Gdy funkcja skompilowana jako zarządzane wywołuje zawierający funkcja `_ReturnAddress`, `_ReturnAddress` może nie działać zgodnie z oczekiwaniami.  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="example"></a>Przykład  
  
```  
// compiler_intrinsics__ReturnAddress.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_ReturnAddress)  
  
__declspec(noinline)  
void noinline_func(void)  
{  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
}  
  
__forceinline  
void inline_func(void)  
{  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
}  
  
int main(void)  
{  
   noinline_func();   
   inline_func();  
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());  
  
   return 0;  
}  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)
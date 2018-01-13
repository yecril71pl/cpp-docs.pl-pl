---
title: __int8, __int16, __int32, __int64 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
dev_langs: C++
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 957e2483d61855c442780440ccf87441f00cb1c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="int8-int16-int32-int64"></a>__int8, __int16, __int32, __int64
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Typy całkowite o określonym rozmiarze obsługuje funkcje Microsoft C/C++. 8 - 16-, 32- i 64-bitową liczbę całkowitą zmienne można zadeklarować przy użyciu **__int**  *n*  wpisz specyfikator, gdzie  *n*  jest 8, 16, 32 lub 64.  
  
 Poniższy przykład deklaruje jedną zmienną dla każdego typu liczb całkowitych o rozmiarze:  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 Typy `__int8`, `__int16`, i `__int32` są synonimy dla typów ANSI, które mają taki sam rozmiar i są użyteczne do pisania kodu przenośnego zachowuje się tak samo na wielu platformach. `__int8` — Typ danych jest tożsame z typem `char`, `__int16` jest tożsame z typem **krótki**, i `__int32` jest synonimem typu `int`. `__int64` Tożsame z typem jest typ `long long`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia __int*xx* parametr zostanie podwyższony do `int`:  
  
```  
// sized_int_types.cpp  
  
#include <stdio.h>  
  
void func(int i) {  
    printf_s("%s\n", __FUNCTION__);  
}  
  
int main()  
{  
    __int8 i8 = 100;  
    func(i8);   // no void func(__int8 i8) function  
                // __int8 will be promoted to int  
}  
```  
  
```Output  
func  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Typy podstawowe](../cpp/fundamental-types-cpp.md)   
 [Zakresy typu danych](../cpp/data-type-ranges.md)
---
title: __int8, __int16, __int32, __int64 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
dev_langs:
- C++
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1be48b2e6972ca3a291ab57dbcb1976e6a56d87
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39401383"
---
# <a name="int8-int16-int32-int64"></a>__int8, __int16, __int32, __int64
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Funkcje Microsoft C/C++ obsługuje typy wielkości liczb całkowitych. 8-, 16-, 32- lub 64-bitową liczbę całkowitą zmiennych można zadeklarować za pomocą **__int *** n* wpisz specyfikator, gdzie *n* jest 8, 16, 32 lub 64.  
  
 Poniższy przykład deklaruje jedną zmienną dla każdego z tych typów całkowitych o rozmiarze:  
  
```cpp 
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 Typy **__int8**, **__int16**, i **__int32** są synonimy typy ANSI, które mają taki sam rozmiar i są przydatne przy pisaniu przenośny kod, który zachowuje się tak samo na wielu platformach. **__Int8** typ danych jest synonimem typu **char**, **__int16** jest synonimem typu **krótki**, i **__int32**  jest synonimem typu **int**. **__Int64** typ jest synonimem typu **long long**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, że __int*xx* parametr zostanie podniesiony do **int**:  
  
```cpp 
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
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [Keywords](../cpp/keywords-cpp.md)   
 [Typy podstawowe](../cpp/fundamental-types-cpp.md)   
 [Zakresy typu danych](../cpp/data-type-ranges.md)
---
title: __emul, __emulu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __emulu_cpp
- __emul
- __emul_cpp
- __emulu
dev_langs:
- C++
helpviewer_keywords:
- __emul intrinsic
- __emulu intrinsic
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6e9e7ee594f2587334d93173daa147d81dcebb2
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464491"
---
# <a name="emul-emulu"></a>__emul, __emulu
**Microsoft Specific**  
  
 Wykonuje mnożenia, które przepełnienia, co może zawierać 32-bitową liczbę całkowitą.  
  
## <a name="syntax"></a>Składnia  
  
```  
__int64 __emul(  
   int a,  
   int b  
);  
unsigned __int64 __emulu(  
   unsigned int a,  
   unsigned int b  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `a`  
 Pierwszy operand całkowitą mnożenia.  
  
 [in] `b`  
 Drugi argument liczby całkowitej mnożenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wynik mnożenia.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__emul`|x86, x64|  
|`__emulu`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `__emul` przyjmuje dwie wartości podpisem 32-bitowe i zwraca wynik mnożenia jako wartość 64-bitową.  
  
 `__emulu` przyjmuje dwie wartości 32-bitowej nieoznaczonej liczby całkowitej i zwraca wynik mnożenia jako wartość 64-bitowej nieoznaczonej liczby całkowitej.  
  
## <a name="example"></a>Przykład  
  
```  
// emul.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__emul)  
#pragma intrinsic(__emulu)  
  
int main()  
{  
   int a = -268435456;   
   int b = 2;   
  
   __int64 result = __emul(a, b);  
  
   cout << a << " * " << b << " = " << result << endl;  
  
   unsigned int ua = 0xFFFFFFFF; // Dec value: 4294967295  
   unsigned int ub = 0xF000000;  // Dec value: 251658240  
  
   unsigned __int64 uresult = __emulu(ua, ub);  
  
   cout << ua << " * " << ub << " = " << uresult << endl;  
  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
-268435456 * 2 = -536870912  
4294967295 * 251658240 = 1080863910317260800  
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
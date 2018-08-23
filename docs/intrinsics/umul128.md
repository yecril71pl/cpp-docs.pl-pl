---
title: _umul128 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __umul128
dev_langs:
- C++
helpviewer_keywords:
- __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e996a83cfc2a79d4bf5cc458ccc5bdd586355b64
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464833"
---
# <a name="umul128"></a>_umul128
**Microsoft Specific**  
  
 Mnoży dwie 64-bitowych liczb całkowitych bez znaku przekazany jako pierwsze dwa argumenty i umieszcza wysokiej 64-bitowy produktu w 64-bitowej nieoznaczonej liczby całkowitej wskazywany przez `HighProduct` i zwraca niski 64-bitowy produkt.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 _umul128(   
   unsigned __int64 Multiplier,   
   unsigned __int64 Multiplicand,   
   unsigned __int64 *HighProduct   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Multiplier`  
 Pierwsza liczba całkowita 64-bitowego do pomnożenia.  
  
 [in] `Multiplicand`  
 Drugi 64-bitową liczbę całkowitą do pomnożenia.  
  
 [out] `HighProduct`  
 Wysoka 64 bity produktu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Niski 64 bity produktu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`_umul128`|ARM, x64|\<intrin.h>|  
  
## <a name="example"></a>Przykład  
  
```  
// umul128.c  
// processor: IPF, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_umul128)  
  
int main()  
{  
    unsigned __int64 a = 0x0fffffffffffffffI64;  
    unsigned __int64 b = 0xf0000000I64;  
    unsigned __int64 c, d;  
  
    d = _umul128(a, b, &c);  
  
    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);  
}  
```  
  
```Output  
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000  
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
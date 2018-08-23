---
title: _BitScanForward, _BitScanForward64 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _BitScanForward
- _BitScanForward_cpp
- _BitScanForward64_cpp
- _BitScanForward64
dev_langs:
- C++
helpviewer_keywords:
- _BitScanForward intrinsic
- bsf instruction
- BitScanForward intrinsic
ms.assetid: 405e60fb-0815-42a7-9b02-6fc035122203
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4720ca4a65a543ca09412ac0c1eb1e65bf6cdd23
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464460"
---
# <a name="bitscanforward-bitscanforward64"></a>_BitScanForward, _BitScanForward64
**Microsoft Specific**  
  
 Wyszukaj maskowanie danych z co najmniej znaczący bit (najmniej znaczący BAJT) do najbardziej znaczący bit (BITEM) ustawionego bitu (1).  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char _BitScanForward(  
   unsigned long * Index,  
   unsigned long Mask  
);  
unsigned char _BitScanForward64(  
   unsigned long * Index,  
   unsigned __int64 Mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `Index`  
 Pozycja bitu pierwszego ustawionego bitu [1], znaleziono załadowana.  
  
 [in] `Mask`  
 32-bitowy lub 64-bitową wartość do wyszukania.  
  
## <a name="return-value"></a>Wartość zwracana  
 0, jeśli maska jest równa zeru; wartość różną od zera w przeciwnym razie.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zostanie znaleziony zestaw bitów, pozycja bitu pierwszego ustawionego bitu znaleziono jest zwracany w pierwszym parametrem. Jeśli zostanie znaleziony nie ustawionego bitu, zwracany jest 0; w przeciwnym razie zwracana jest 1.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_BitScanForward`|x86, ARM, x64|  
|`_BitScanForward64`|ARM, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="example"></a>Przykład  
  
```  
// BitScanForward.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanForward)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanForward(&index, mask);  
   if (isNonzero)  
   {  
      cout << "Mask: " << mask << " Index: " << index << endl;  
   }  
   else  
   {  
      cout << "No set bits found.  Mask is zero." << endl;  
   }  
}  
```  
  
## <a name="input"></a>Dane wejściowe  
  
```  
12  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
Enter a positive integer as the mask:   
Mask: 12 Index: 2  
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
---
title: _BitScanForward, _BitScanForward64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb9f45a0cf518265a1eb40a12a976ec0c1e5b9d1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="bitscanforward-bitscanforward64"></a>_BitScanForward, _BitScanForward64
**Microsoft Specific**  
  
 Wyszukiwanie danych maski z bitem (najmniej znaczący BAJT) do najbardziej znaczącego bitu (BITEM) Ustaw bit (1).  
  
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
 Pozycja bitu pierwszego ustawiony bit [1], znaleziono załadowana.  
  
 [in] `Mask`  
 32-bitowa czy 64-bitowa wartość do wyszukiwania.  
  
## <a name="return-value"></a>Wartość zwracana  
 0, jeśli maski ma wartość 0. różna od zera, w przeciwnym razie wartość.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli bit zestaw zostanie znaleziony, pozycja bitu pierwszy bitów zestawu znaleziono jest zwracany w pierwszym parametrem. Jeśli nie z bitowego zestawu zostanie znaleziony, jest zwracana 0; w przeciwnym razie zwracany jest 1.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_BitScanForward`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`_BitScanForward64`|ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
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
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
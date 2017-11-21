---
title: _BitScanReverse, _BitScanReverse64 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _BitScanReverse64
- _BitScanReverse_cpp
- _BitScanReverse
- _BitScanReverse64_cpp
dev_langs: C++
helpviewer_keywords:
- bsr instruction
- _BitScanReverse intrinsic
- BitScanReverse intrinsic
ms.assetid: 2520a207-af8b-4aad-9ae7-831abeadf376
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1547a5aa4ab4709c47305bd5097ba138171fd71c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="bitscanreverse-bitscanreverse64"></a>_BitScanReverse, _BitScanReverse64
**Dotyczące firmy Microsoft**  
  
 Wyszukiwanie danych maski z najbardziej znaczącego bitu (BITEM) do najmniej znaczącego bitu (najmniej znaczący BAJT) dla zestawu bit (1).  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char _BitScanReverse(  
   unsigned long * Index,  
   unsigned long Mask  
);  
unsigned char _BitScanReverse64(  
   unsigned long * Index,  
   unsigned __int64 Mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`Index`  
 Pozycja bitu pierwszego ustawiony bit [1], znaleziono załadowana.  
  
 [in]`Mask`  
 32-bitowa czy 64-bitowa wartość do wyszukiwania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `Index` było zestawu lub 0, jeśli nie znaleziono żadnych zestawu usługi bits.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`_BitScanReverse`|x86, ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_BitScanReverse64`|ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]||  
  
## <a name="example"></a>Przykład  
  
```  
// BitScanReverse.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(_BitScanReverse)  
  
int main()  
{  
   unsigned long mask = 0x1000;  
   unsigned long index;  
   unsigned char isNonzero;  
  
   cout << "Enter a positive integer as the mask: " << flush;  
   cin >> mask;  
   isNonzero = _BitScanReverse(&index, mask);  
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
Mask: 12 Index: 3  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
---
title: __lzcnt16 __lzcnt, __lzcnt64 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __lzcnt64
- __lzcnt16
- __lzcnt
dev_langs:
- C++
helpviewer_keywords:
- __lzcnt intrinsic
- lzcnt instruction
- lzcnt16 intrinsic
- lzcnt intrinsic
- __lzcnt16 intrinsic
- lzcnt64 intrinsic
- __lzcnt64 intrinsic
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85af6534ccf578bccabcd0f7b517234b2b560b6f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="lzcnt16-lzcnt-lzcnt64"></a>__lzcnt16, __lzcnt, __lzcnt64
**Microsoft Specific**  
  
 Wartości zerowe liczbę wiodących liczby 16-, 32-lub 64-bajtowych liczb całkowitych.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned short __lzcnt16(  
   unsigned short value  
);  
unsigned int __lzcnt(  
   unsigned int value  
);  
unsigned __int64 __lzcnt64(  
   unsigned __int64 value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `value`  
 16 – 32- i 64-bitowej liczby całkowitej bez znaku skanowania pod kątem zerami.  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba początkowe zero bitów `value` parametru. Jeśli `value` wynosi zero, wartość zwracana jest rozmiar operand danych wejściowych (16, 32 lub 64). Jeśli najbardziej znaczącego bitu `value` , jest zwracana wartość wynosi zero.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__lzcnt16`|AMD: Manipulowanie zaawansowane Bit (ABM)<br /><br /> Intel: Haswell|  
|`__lzcnt`|AMD: Manipulowanie zaawansowane Bit (ABM)<br /><br /> Intel: Haswell|  
|`__lzcnt64`|AMD: Zaawansowane manipulowanie bitowe (ABM) w trybie 64-bitowym.<br /><br /> Intel: Haswell|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Każdy z tych funkcji wewnętrznych generuje `lzcnt` instrukcji.  Rozmiar wartości który `lzcnt` instrukcji zwraca jest taka sama jak rozmiar jej argument.  W trybie 32-bitowym istnieją nie 64-bitowych ogólnego przeznaczenia rejestrów, dlatego nie 64-bitowych `lzcnt`.  
  
 Ustalenie sprzętu Obsługa `lzcnt` wywołanie instrukcji `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 5 `CPUInfo[2] (ECX)`. Ten bit będzie 1, jeśli instrukcja jest obsługiwana i 0 w inny sposób. Jeśli możesz uruchomić kodu korzystającego z tym wewnętrzna na sprzęcie, który nie obsługuje `lzcnt` instrukcji są nieprzewidywalne wyniki.  
  
 Na procesory Intel, które nie obsługują `lzcnt` instrukcji, kodowanie instrukcji bajtów jest wykonywany jako `bsr` (bit skanowania odwrotnie). Przenośność kodu w przypadku wątpliwości dotyczących, rozważ użycie `_BitScanReverse` wewnętrzne zamiast tego. Aby uzyskać więcej informacji, zobacz [_BitScanReverse, _BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md).  
  
## <a name="example"></a>Przykład  
  
```  
// Compile this test with: /EHsc  
#include <iostream>   
#include <intrin.h>   
using namespace std;   
  
int main()   
{  
  unsigned short us[3] = {0, 0xFF, 0xFFFF};  
  unsigned short usr;  
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};  
  unsigned int   uir;  
  
  for (int i=0; i<3; i++) {  
    usr = __lzcnt16(us[i]);  
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __lzcnt(ui[i]);  
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
```Output  
__lzcnt16(0x0) = 16  
__lzcnt16(0xff) = 8  
__lzcnt16(0xffff) = 0  
__lzcnt(0x0) = 32  
__lzcnt(0xff) = 24  
__lzcnt(0xffff) = 16  
__lzcnt(0xffffffff) = 0  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
 Część tej zawartości są Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć z uprawnieniem z zaawansowanymi Micro urządzeń, Inc.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
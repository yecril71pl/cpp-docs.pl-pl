---
title: __popcnt16 __popcnt, __popcnt64 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
dev_langs: C++
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 45e60a412dc24f685fd375ebc19c109b2bee0e2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="popcnt16-popcnt-popcnt64"></a>__popcnt16 __popcnt, __popcnt64
**Dotyczące firmy Microsoft**  
  
 Zlicza jednego bitów (liczba populacji) 16 – 32- i 64-bajtowa liczba całkowita bez znaku.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned short __popcnt16(  
   unsigned short value  
);  
unsigned int __popcnt(  
   unsigned int value  
);  
unsigned __int64 __popcnt64(  
   unsigned __int64 value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`value`  
 16-, 32- lub 64-bitowych unsigned integer dla którego chcemy liczba populacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba bitów jeden `value` parametru.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__popcnt16`|Manipulowanie Bit zaawansowane|  
|`__popcnt`|Manipulowanie Bit zaawansowane|  
|`__popcnt64`|Zaawansowane manipulowanie bitowe w trybie 64-bitowym.|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Każdy z tych funkcji wewnętrznych generuje `popcnt` instrukcji.  Rozmiar wartości który `popcnt` instrukcji zwraca jest taka sama jak rozmiar jej argument.  W trybie 32-bitowym istnieją nie 64-bitowych ogólnego przeznaczenia rejestrów, dlatego nie 64-bitowych `popcnt`.  
  
 Aby określić obsługę sprzętu `popcnt` instrukcji, wywołanie `__cpuid` wewnętrzne z `InfoType=0x00000001` i sprawdź bit 23 `CPUInfo[2] (ECX)`. Ten bit jest 1, jeśli instrukcja jest obsługiwana i 0, w przeciwnym razie wartość. Jeśli możesz uruchomić kodu korzystającego z tym wewnętrzna na sprzęcie, który nie obsługuje `popcnt` instrukcji są nieprzewidywalne wyniki.  
  
## <a name="example"></a>Przykład  
  
```  
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
    usr = __popcnt16(us[i]);  
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __popcnt(ui[i]);  
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
```Output  
__popcnt16(0x0) = 0  
__popcnt16(0xff) = 8  
__popcnt16(0xffff) = 16  
__popcnt(0x0) = 0  
__popcnt(0xff) = 8  
__oopcnt(0xffff) = 16  
__popcnt(0xffffffff) = 32  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
 Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć z uprawnieniem z zaawansowanymi Micro urządzeń, Inc.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
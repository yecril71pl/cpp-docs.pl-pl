---
title: __popcnt16, __popcnt, __popcnt64
ms.date: 11/04/2016
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
ms.openlocfilehash: d6cc9a0ce784ab79f5e4225675a082fc55bd53e7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037013"
---
# <a name="popcnt16-popcnt-popcnt64"></a>__popcnt16, __popcnt, __popcnt64

**Microsoft Specific**

Zlicza jednej usługi bits (liczba populacji) w 16-, 32- lub 64-bitowej nieoznaczonej liczby całkowitej.

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

*value*<br/>
[in] 16-, 32- lub 64-bitowych unsigned integer dla którego chcemy, aby liczba populacji.

## <a name="return-value"></a>Wartość zwracana

Liczba bitów co `value` parametru.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__popcnt16`|Manipulowanie Bit zaawansowane|
|`__popcnt`|Manipulowanie Bit zaawansowane|
|`__popcnt64`|Zaawansowane manipulowania bitowych w trybie 64-bitowym.|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Każda z tych funkcji wewnętrznych generuje `popcnt` instrukcji. W trybie 32-bitowym istnieją Brak 64-bitowych ogólnego przeznaczenia rejestrów, dlatego nie 64-bitowych `popcnt`.

Aby określić, pomoc techniczna dotycząca sprzętu dla `popcnt` instrukcji, wywołanie `__cpuid` wewnętrzne z `InfoType=0x00000001` i sprawdź bit 23 `CPUInfo[2] (ECX)`. Ten bit jest 1, jeśli instrukcja jest obsługiwana lub 0. Jeśli możesz uruchomić kod, który korzysta z tym wewnętrzne na sprzęcie, który nie obsługuje `popcnt` instrukcji, wyniki są nieprzewidywalne.

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
__popcnt(0xffff) = 16
__popcnt(0xffffffff) = 32
```

**END specyficzny dla Microsoft**

Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć zgoda zaawansowane Micro urządzeń, Inc.

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)

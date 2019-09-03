---
title: __popcnt16, __popcnt, __popcnt64
ms.date: 09/02/2019
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
ms.openlocfilehash: 3e5ae7f897500775671f8bd2563028874579a627
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221359"
---
# <a name="__popcnt16-__popcnt-__popcnt64"></a>__popcnt16, __popcnt, __popcnt64

**Microsoft Specific**

Zlicza liczbę `1` bitów (liczbę populacji) w 16-, 32-lub 64-bitowej liczbie całkowitej bez znaku.

## <a name="syntax"></a>Składnia

```C
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

### <a name="parameters"></a>Parametry

*wartościami*\
podczas 16-, 32-lub 64-bitowa liczba całkowita bez znaku, dla którego chcemy obliczyć liczbę populacji.

## <a name="return-value"></a>Wartość zwracana

Liczba `1` bitów w parametrze *Value* .

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__popcnt16`|Zaawansowane manipulowanie Bitmi|
|`__popcnt`|Zaawansowane manipulowanie Bitmi|
|`__popcnt64`|Zaawansowane manipulowanie Bitmi w trybie 64-bitowym.|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Każda z elementów wewnętrznych generuje `popcnt` instrukcję. W trybie 32-bitowym nie ma żadnych 64-bitowych rejestrów ogólnego przeznaczenia, dlatego 64-bit `popcnt` nie jest obsługiwany.

Aby określić obsługę `popcnt` sprzętową instrukcji, `__cpuid` Wywołaj wewnętrzne z `InfoType=0x00000001` i sprawdź bit 23 w `CPUInfo[2] (ECX)`. Ten bit ma wartość 1, jeśli instrukcja jest obsługiwana i 0 w przeciwnym razie. Jeśli uruchamiasz kod, który używa tych elementów wewnętrznych na sprzęcie, który nie `popcnt` obsługuje instrukcji, wyniki są nieprzewidywalne.

## <a name="example"></a>Przykład

```cpp
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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

Fragmenty Copyright 2007 przez Advanced Micro Devices, Inc. Wszelkie prawa zastrzeżone. Wygenerowane z uprawnieniami z zaawansowanych urządzeń Micro Devices, Inc.

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)

---
title: __lzcnt16, __lzcnt, __lzcnt64
ms.date: 11/04/2016
f1_keywords:
- __lzcnt64
- __lzcnt16
- __lzcnt
helpviewer_keywords:
- __lzcnt intrinsic
- lzcnt instruction
- lzcnt16 intrinsic
- lzcnt intrinsic
- __lzcnt16 intrinsic
- lzcnt64 intrinsic
- __lzcnt64 intrinsic
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
ms.openlocfilehash: 333d9f2b23fb90388af8395945256956c9222ab9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041341"
---
# <a name="lzcnt16-lzcnt-lzcnt64"></a>__lzcnt16, __lzcnt, __lzcnt64

**Specyficzne dla firmy Microsoft**

Powoduje wyzerowanie liczbę wiodących liczby 16-, 32-lub 64-bitową liczbę całkowitą.

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

*value*<br/>
[in] 16-, 32- lub 64-bitowa liczba całkowita bez znaku do skanowania w poszukiwaniu zer wiodących.

## <a name="return-value"></a>Wartość zwracana

Liczba wiodące zero bitów `value` parametru. Jeśli `value` wynosi zero, wartość zwracana jest rozmiar danych wejściowych operand (16, 32 lub 64). Jeśli najbardziej znaczącego bitu `value` , jest zwracana wartość wynosi zero.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__lzcnt16`|AMD: Manipulowanie zaawansowane Bit (ABM)<br /><br /> Intel: Haswell|
|`__lzcnt`|AMD: Manipulowanie zaawansowane Bit (ABM)<br /><br /> Intel: Haswell|
|`__lzcnt64`|AMD: Zaawansowane Bit manipulowania (ABM) w trybie 64-bitowym.<br /><br /> Intel: Haswell|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Każda z tych funkcji wewnętrznych generuje `lzcnt` instrukcji.  Rozmiar wartości, `lzcnt` instrukcji daje w wyniku jest taki sam jak rozmiar argumentu.  W trybie 32-bitowym istnieją Brak 64-bitowych ogólnego przeznaczenia rejestrów, dlatego nie 64-bitowych `lzcnt`.

Aby określić, pomoc techniczna dotycząca sprzętu dla `lzcnt` wywołania instrukcji `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 5 `CPUInfo[2] (ECX)`. Ten bit będzie 1, jeśli instrukcja jest obsługiwana lub 0 w inny sposób. Jeśli możesz uruchomić kod, który korzysta z tym wewnętrzne na sprzęcie, który nie obsługuje `lzcnt` instrukcji, wyniki są nieprzewidywalne.

Na procesorach Intel, które nie obsługują `lzcnt` instrukcji, instrukcje bajtów kodowania jest wykonywane jako `bsr` (bit skanowania wstecznego). Jeśli przenośność kodu jest istotna, rozważ użycie `_BitScanReverse` wewnętrzne zamiast tego. Aby uzyskać więcej informacji, zobacz [_BitScanReverse, _BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md).

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

**KONIEC Specyficzne dla firmy Microsoft**

Część tej zawartości są Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć zgoda zaawansowane Micro urządzeń, Inc.

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)

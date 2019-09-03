---
title: __shiftright128
ms.date: 09/02/2019
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: a18a9958a51f291e4997c23e87ee48f739562416
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220020"
---
# <a name="__shiftright128"></a>__shiftright128

**Microsoft Specific**

Przenosi ilość 128-bitową, reprezentowaną jako 2 64-bitowe `LowPart` ilości `HighPart`i, po prawej stronie przez liczbę bitów określoną przez `Shift` , i zwraca niskie 64 bitów wyniku.

## <a name="syntax"></a>Składnia

```C
unsigned __int64 __shiftright128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

### <a name="parameters"></a>Parametry

*LowPart*\
podczas Niska 64 bitów ilości 128-bitowej do przesunięcia.

*HighPart*\
podczas Wysoka 64 bitów 128-bitowej liczby do przesunięcia.

*Nocn*\
podczas Liczba bitów do przesunięcia.

## <a name="return-value"></a>Wartość zwracana

Niska 64 bitów wyniku.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__shiftright128`|X64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

`0` `__shiftright128(0, 1, 64)` `1` `0` Wartość jest zawsze modulo 64, tak więc, na przykład, jeśli wywołasz, funkcja zmieni górną część bitów w prawo i zwróci niską część, a nie jako nieoczekiwaną. `Shift`

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem, zobacz [__shiftleft128](../intrinsics/shiftleft128.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__shiftleft128](../intrinsics/shiftleft128.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)

---
title: __shiftright128
ms.date: 11/04/2016
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: b721abc9be22709fdc221951e2012300d6b96762
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390337"
---
# <a name="shiftright128"></a>__shiftright128

**Microsoft Specific**

Przenosi ilość 128-bitowego, reprezentowane jako dwie ilości 64-bitowych `LowPart` i `HighPart`, w prawo o liczbę bitów określoną przez `Shift` i zwraca niski 64 bity wyniku.

## <a name="syntax"></a>Składnia

```
unsigned __int64 __shiftright128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

#### <a name="parameters"></a>Parametry

*LowPart*<br/>
[in] Niski 64 bity ilość 128-bitowe przesunięcie.

*HighPart*<br/>
[in] Wysoka 64 bity ilość 128-bitowe przesunięcie.

*SHIFT*<br/>
[in] Liczba bitów, aby przesunąć.

## <a name="return-value"></a>Wartość zwracana

Niski 64 bity wyniku.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__shiftright128`|X64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

`Shift` Wartość jest zawsze modulo 64 więc, na przykład, jeśli wywołasz `__shiftright128(0, 1, 64)`, funkcja zostanie wprowadzony wysokiej część `0` bitów, kliknij prawym przyciskiem myszy i powrócić niskiej część `0` i nie `1` w przeciwnym razie może być oczekiwany.

## <a name="example"></a>Przykład

Aby uzyskać przykład, zobacz [__shiftleft128](../intrinsics/shiftleft128.md).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__shiftleft128](../intrinsics/shiftleft128.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
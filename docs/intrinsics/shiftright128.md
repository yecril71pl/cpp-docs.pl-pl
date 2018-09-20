---
title: __shiftright128 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __shiftright128
dev_langs:
- C++
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10e848321f105f60643f579c12772f6a40edebeb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383522"
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

## <a name="see-also"></a>Zobacz też

[__shiftleft128](../intrinsics/shiftleft128.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
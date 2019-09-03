---
title: __ll_lshift
ms.date: 09/02/2019
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 158ecbf39320d70b51f1f498a0b689ba58fec363
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221812"
---
# <a name="__ll_lshift"></a>__ll_lshift

**Microsoft Specific**

Przesuwa podaną wartość 64-bitową w lewo o określoną liczbę bitów.

## <a name="syntax"></a>Składnia

```C
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>Parametry

*Bitowa*\
podczas 64-bitowa wartość całkowita do przesunięcia w lewo.

*nBit*\
podczas Liczba bitów do przesunięcia.

## <a name="return-value"></a>Wartość zwracana

Maska przesunięta w lewo `nBit` o bity.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__ll_lshift`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Jeśli kompilujesz program dla architektury 64-bitowej i `nBit` jest większy niż 63, liczba bitów do przesunięcia to `nBit` modulo 64. Jeśli kompilujesz program dla architektury 32-bitowej i `nBit` jest większy niż 31, liczba bitów do przesunięcia to `nBit` modulo 32.

Wartość `ll` w polu Nazwa wskazuje, że jest to operacja na `long long` (`__int64`).

## <a name="example"></a>Przykład

```cpp
// ll_lshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_lshift)

int main()
{
   unsigned __int64 Mask = 0x100;
   int nBit = 8;
   Mask = __ll_lshift(Mask, nBit);
   cout << hex << Mask << endl;
}
```

## <a name="output"></a>Dane wyjściowe

```Output
10000
```

> [!NOTE]
> Nie istnieje niepodpisana wersja operacji przesunięcia w lewo. Dzieje się tak `__ll_lshift` , ponieważ używa już niepodpisanego parametru wejściowego. W przeciwieństwie do prawego przesunięcia nie ma zależności od znaku po lewej stronie, ponieważ najmniej znaczący bit w wyniku jest zawsze ustawiony na zero, niezależnie od znaku wartości przesuniętej.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__ll_rshift](../intrinsics/ll-rshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)

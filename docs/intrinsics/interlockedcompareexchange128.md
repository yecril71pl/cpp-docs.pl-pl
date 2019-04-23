---
title: _InterlockedCompareExchange128
ms.date: 11/04/2016
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
ms.openlocfilehash: 9330b1405ca247364cd04d3ab399f66e4f332273
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037873"
---
# <a name="interlockedcompareexchange128"></a>_InterlockedCompareExchange128

**Microsoft Specific**

Wykonuje porównanie blokowane 128-bitowego i exchange.

## <a name="syntax"></a>Składnia

```
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

#### <a name="parameters"></a>Parametry

*miejsce docelowe*<br/>
[out w] Wskaźnik do miejsca docelowego, który jest tablicą dwóch 64-bitowych liczb całkowitych są traktowane jako pola 128-bitowego. Dane docelowego musi być 16-bajtowy wyrównane, aby uniknąć błędów ogólnej ochrony.

*ExchangeHigh*<br/>
[in] 64-bitowa liczba całkowita, która może być wymieniane z wysokiej część miejsca docelowego.

*ExchangeLow*<br/>
[in] 64-bitowa liczba całkowita, która może być wymieniane o niskiej część miejsca docelowego.

*ComparandResult*<br/>
[out w] Wskaźnik do tablicy dwóch 64-bitowych liczb całkowitych (traktowane jako pola 128-bitowy) do porównania z miejsca docelowego.  W danych wyjściowych to jest zastępowany oryginalnej wartości elementu docelowego.

## <a name="return-value"></a>Wartość zwracana

1, jeśli wzorzec 128-bitowy jest równe oryginalnej wartości elementu docelowego. `ExchangeHigh` i `ExchangeLow` zastąpić docelowy 128-bitowego.

0, jeśli wzorzec nie jest równa oryginalnej wartości elementu docelowego. Niezmieniona wartość miejsca docelowego, a wartość wzorzec zostanie zastąpiony wartością miejsca docelowego.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_InterlockedCompareExchange128`|X64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Generuje tym wewnętrzne `cmpxchg16b` instrukcji (przy użyciu `lock` prefiks) do wykonania porównania zablokowane 128-bitowego i exchange. Wczesne wersje AMD 64-bitowym sprzęcie nie obsługują tej instrukcji. Aby sprawdzić, czy pomoc techniczna dotycząca sprzętu dla `cmpxchg16b` instrukcji, wywołanie `__cpuid` wewnętrzne z `InfoType=0x00000001 (standard function 1)`. Bit 13 `CPUInfo[2]` (ECX) wynosi 1, jeśli instrukcja jest obsługiwana.

> [!NOTE]
>  Wartość `ComparandResult` jest zawsze zastąpiony. Po `lock` instrukcji, w tym wewnętrzne natychmiast kopiuje wartość początkową `Destination` do `ComparandResult`. Z tego powodu `ComparandResult` i `Destination` powinien wskazywać lokalizacji pamięci, aby uniknąć nieoczekiwanego zachowania.

Chociaż można używać `_InterlockedCompareExchange128` do synchronizacji niskiego poziomu wątku nie trzeba synchronizować ponad 128 bitów, jeśli można używać mniejszych funkcji synchronizacji (takich jak drugi `_InterlockedCompareExchange` funkcje wewnętrzne) zamiast tego. Użyj `_InterlockedCompareExchange128` chcącym atomic dostęp do 128-bitową wartością w pamięci.

Jeśli możesz uruchomić kod, który korzysta z tym wewnętrzne na sprzęcie, który nie obsługuje `cmpxchg16b` instrukcji, wyniki są nieprzewidywalne.

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

W tym przykładzie użyto `_InterlockedCompareExchange128` zamienić słowo wysokiej tablicy dwóch 64-bitowych liczb całkowitych z sumą jego słów wysoki i niski i zwiększ niższe słowo. Dostęp do tablicy BigInt.Int są niepodzielne, ale w tym przykładzie używa jednego wątku i ignoruje blokowania dla uproszczenia.

```
// cmpxchg16b.c
// processor: x64
// compile with: /EHsc /O2
#include <stdio.h>
#include <intrin.h>

typedef struct _LARGE_INTEGER_128 {
    __int64 Int[2];
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;

volatile LARGE_INTEGER_128 BigInt;

// This AtomicOp() function atomically performs:
//   BigInt.Int[1] += BigInt.Int[0]
//   BigInt.Int[0] += 1
void AtomicOp ()
{
    LARGE_INTEGER_128 Comparand;
    Comparand.Int[0] = BigInt.Int[0];
    Comparand.Int[1] = BigInt.Int[1];
    do {
        ; // nothing
    } while (_InterlockedCompareExchange128(BigInt.Int,
                                            Comparand.Int[0] + Comparand.Int[1],
                                            Comparand.Int[0] + 1,
                                            Comparand.Int) == 0);
}

// In a real application, several threads contend for the value
// of BigInt.
// Here we focus on the compare and exchange for simplicity.
int main(void)
{
   BigInt.Int[1] = 23;
   BigInt.Int[0] = 11;
   AtomicOp();
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",
      BigInt.Int[1],BigInt.Int[0]);
}
```

```Output
BigInt.Int[1] = 34, BigInt.Int[0] = 12
```

**END specyficzny dla Microsoft**

Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć zgoda zaawansowane Micro urządzeń, Inc.

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Funkcje wewnętrzne _InterlockedCompareExchange](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)<br/>
[Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
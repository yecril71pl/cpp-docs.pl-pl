---
title: Funkcje wewnętrzne _InterlockedCompareExchange128
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
- _InterlockedCompareExchange128_acq
- _InterlockedCompareExchange128_nf
- _InterlockedCompareExchange128_np
- _InterlockedCompareExchange128_rel
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
ms.openlocfilehash: 525b0fd77323789eed05c47c944794ff389bfac5
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217688"
---
# <a name="_interlockedcompareexchange128-intrinsic-functions"></a>Funkcje wewnętrzne _InterlockedCompareExchange128

**Microsoft Specific**

Wykonuje porównanie z programem 128-bitową, która jest Zablokowani.

## <a name="syntax"></a>Składnia

```C
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_acq(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_nf(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_np(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_rel(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

### <a name="parameters"></a>Parametry

*Punktu*\
[in. out] Wskaźnik do miejsca docelowego, który jest tablicą 2 64-bitowych liczb całkowitych uznawanych za pole 128-bitowe. Dane docelowe muszą być wyrównane do 16 bajtów, aby uniknąć ogólnego błędu ochrony.

*ExchangeHigh*\
podczas 64-bitowa liczba całkowita, która może być wymieniana z wysoką częścią miejsca docelowego.

*ExchangeLow*\
podczas 64-bitowa liczba całkowita, która może być wymieniana z niską częścią miejsca docelowego.

*ComparandResult*\
[in. out] Wskaźnik do tablicy 2 64-bitowych liczb całkowitych (traktowanych jako pole 128-bitowe) do porównania z miejscem docelowym.  W danych wyjściowych ta tablica jest zastępowana oryginalną wartością miejsca docelowego.

## <a name="return-value"></a>Wartość zwracana

1, jeśli 128-bitowy argument porównania określony jest równa oryginalnej wartości docelowej. `ExchangeHigh`i `ExchangeLow` Zastąp wartość 128-bitowym miejscem docelowym.

0, jeśli argument porównania określony nie jest równa oryginalnej wartości docelowej. Wartość miejsca docelowego jest niezmieniona, a wartość argument porównania określony jest zastępowana wartością docelową.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_InterlockedCompareExchange128`|x64, ARM64|
|`_InterlockedCompareExchange128_acq`, `_InterlockedCompareExchange128_nf`, `_InterlockedCompareExchange128_rel`|ARM64|
|`_InterlockedCompareExchange128_np`|X64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Wewnętrznie generuje instrukcję (z `lock` prefiksem), aby wykonać 128-bitowe blokowanie porównania i programu Exchange. `cmpxchg16b` `_InterlockedCompareExchange128` Wczesne wersje sprzętu AMD 64-bit nie obsługują tej instrukcji. Aby sprawdzić obsługę `cmpxchg16b` sprzętową instrukcji, `__cpuid` Wywołaj metodę wewnętrzną za `InfoType=0x00000001 (standard function 1)`pomocą. Bit 13 of `CPUInfo[2]` (ECX) to 1, jeśli instrukcja jest obsługiwana.

> [!NOTE]
> Wartość `ComparandResult` jest zawsze zastępowana. Po instrukcji ten element wewnętrzny natychmiast kopiuje `Destination` wartość początkową do `ComparandResult`. `lock` Z tego powodu `Destination` należy `ComparandResult` wskazać osobne lokalizacje pamięci, aby uniknąć nieoczekiwanego zachowania.

Chociaż można używać `_InterlockedCompareExchange128` do synchronizacji wątków niskiego poziomu, nie trzeba synchronizować ponad 128 bitów, jeśli można użyć mniejszych funkcji synchronizacji (takich jak inne `_InterlockedCompareExchange` wewnętrzne). Użyj `_InterlockedCompareExchange128` , jeśli chcesz, aby dostęp niepodzielny do 128-bitowej wartości w pamięci.

Jeśli uruchamiasz kod, który używa wewnętrznego na sprzęcie, który nie obsługuje `cmpxchg16b` instrukcji, wyniki są nieprzewidywalne.

Na platformach ARM Użyj wewnętrznych z `_acq` i `_rel` sufiksów dla semantyki pozyskiwania i wydawania, na przykład na początku i na końcu sekcji krytycznej. Elementy wewnętrzne ARM z `_nf` sufiksem ("No ogrodzeni") nie działają jako bariera pamięci.

Elementy wewnętrzne z `_np` sufiksem ("No Fetch") uniemożliwiają wstawienie przez kompilator możliwej operacji pobierania z wyprzedzeniem.

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

W tym przykładzie `_InterlockedCompareExchange128` używa się, aby zastąpić wielką część tablicy 2 64-bitową liczbę całkowitą z sumą jej dużych i małych słów i aby zwiększyć dolny wyraz. Dostęp do `BigInt.Int` tablicy jest niepodzielny, ale w tym przykładzie użyto jednego wątku i ignoruje blokadę dla uproszczenia.

```cpp
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

**ZAKOŃCZENIE określonych przez firmę Microsoft**


## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Funkcje wewnętrzne _InterlockedCompareExchange](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)\
[Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

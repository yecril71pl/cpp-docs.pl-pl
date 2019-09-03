---
title: __rdtscp
ms.date: 09/02/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: 4dcabd6ed0f7fb3f422927815cbdc91f2b4b9d43
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221318"
---
# <a name="__rdtscp"></a>__rdtscp

**Microsoft Specific**

Generuje instrukcję, zapis `TSC_AUX[31:0`] do pamięci i zwraca licznik 64-bitowy sygnatura czasowa (`TSC)` wynik. `rdtscp`

## <a name="syntax"></a>Składnia

```C
unsigned __int64 __rdtscp(
   unsigned int * AUX
);
```

### <a name="parameters"></a>Parametry

*POMOCNICZ*\
określoną Wskaźnik do lokalizacji, która będzie zawierać zawartość rejestru `TSC_AUX[31:0]`właściwego dla komputera.

## <a name="return-value"></a>Wartość zwracana

64-bitowa liczba kresek bez znaku.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__rdtscp`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

`__rdtscp` Wewnętrznie`rdtscp` generuje instrukcję. Aby określić obsługę sprzętową dla tej instrukcji, wywołaj `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 27 `CPUInfo[3] (EDX)`z. Ten bit ma wartość 1, jeśli instrukcja jest obsługiwana i 0 w przeciwnym razie.  Jeśli uruchamiasz kod, który używa wewnętrznego na sprzęcie, który nie obsługuje `rdtscp` instrukcji, wyniki są nieprzewidywalne.

Ta instrukcja czeka, aż wszystkie poprzednie instrukcje zostały wykonane i wszystkie poprzednie obciążenia są widoczne globalnie. Nie jest to jednak serializowana instrukcja. Aby uzyskać więcej informacji, zobacz Podręczniki firmy Intel i AMD.

Znaczenie wartości w `TSC_AUX[31:0]` zależności od systemu operacyjnego.

## <a name="example"></a>Przykład

```cpp
#include <intrin.h>
#include <stdio.h>
int main()
{
    unsigned __int64 i;
    unsigned int ui;
    i = __rdtscp(&ui);
    printf_s("%I64d ticks\n", i);
    printf_s("TSC_AUX was %x\n", ui);
}
```

```Output
3363423610155519 ticks
TSC_AUX was 0
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__rdtsc](../intrinsics/rdtsc.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)

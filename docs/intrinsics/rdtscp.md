---
title: __rdtscp
ms.date: 07/11/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: b8a31c6d19cd171cbe909c75a27c2389866bd578
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861106"
---
# <a name="rdtscp"></a>__rdtscp

**Microsoft Specific**

Generuje `rdtscp` instrukcji, zapisuje `TSC_AUX[31:0`] do pamięci i zwraca licznika sygnatury czasu 64-bitowych (`TSC)` wynik.

## <a name="syntax"></a>Składnia

```
unsigned __int64 __rdtscp(
   unsigned int * Aux
);
```

#### <a name="parameters"></a>Parametry

*AUX*<br/>
[out] Wskaźnik do lokalizacji, która będzie zawierać zawartość rejestru specyficzny dla komputera `TSC_AUX[31:0]`.

## <a name="return-value"></a>Wartość zwracana

Liczba cykli 64-bitowej nieoznaczonej liczby całkowitej.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__rdtscp`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Generuje tym wewnętrzne `rdtscp` instrukcji. Aby ustalić, pomoc techniczna dotycząca sprzętu dla tej instrukcji, należy wywołać `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 27 `CPUInfo[3] (EDX)`. Ten bit jest 1, jeśli instrukcja jest obsługiwana lub 0.  Jeśli możesz uruchomić kod, który korzysta z tym wewnętrzne na sprzęcie, który nie obsługuje `rdtscp` instrukcji, wyniki są nieprzewidywalne.

Ta instrukcja czeka, aż wykonaniu wszystkich poprzednich instrukcji i wszystkie poprzednie obciążenia są widoczne globalnie. Jednak nie jest instrukcja serializacji. Zobacz instrukcje firmy Intel i AMD, aby uzyskać więcej informacji.

Znaczenie wartość `TSC_AUX[31:0]` zależy od systemu operacyjnego.

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

**END specyficzny dla Microsoft**


## <a name="see-also"></a>Zobacz także

[__rdtsc](../intrinsics/rdtsc.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
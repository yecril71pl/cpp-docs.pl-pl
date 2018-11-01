---
title: __rdtscp
ms.date: 11/04/2016
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: 813f13e20e74890cfcb52ae25234aa348e1d522d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496306"
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
|`__rdtscp`|0Fh rodziny NPT AMD lub nowszy|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Generuje tym wewnętrzne `rdtscp` instrukcji. Aby ustalić, pomoc techniczna dotycząca sprzętu dla tej instrukcji, należy wywołać `__cpuid` wewnętrzne z `InfoType=0x80000001` i sprawdź bit 27 `CPUInfo[3] (EDX)`. Ten bit jest 1, jeśli instrukcja jest obsługiwana lub 0.  Jeśli możesz uruchomić kod, który korzysta z tym wewnętrzne na sprzęcie, który nie obsługuje `rdtscp` instrukcji, wyniki są nieprzewidywalne.

> [!CAUTION]
>  W odróżnieniu od `rdtsc`, `rdtscp` to instrukcja serializacji; Niemniej jednak kompilator można przenieść kod obejścia tego problemu wewnętrzne.

Interpretacja wartości TSC w tej generacji sprzętowy różni się od we wcześniejszych wersjach programu x64.  Zobacz instrukcje sprzętu, aby uzyskać więcej informacji.

Znaczenie wartość `TSC_AUX[31:0]` zależy od systemu operacyjnego.

## <a name="example"></a>Przykład

```
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

Copyright 2007 zaawansowane Micro urządzeń, Inc. Wszelkie prawa zastrzeżone. Odtworzyć zgoda zaawansowane Micro urządzeń, Inc.

## <a name="see-also"></a>Zobacz też

[__rdtsc](../intrinsics/rdtsc.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
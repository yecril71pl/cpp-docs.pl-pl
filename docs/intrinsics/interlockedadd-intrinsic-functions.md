---
title: Funkcje wewnętrzne _InterlockedAdd
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAdd64_acq_cpp
- _InterlockedAdd64_acq
- _InterlockedAdd_acq
- _InterlockedAdd_nf
- _InterlockedAdd64_rel
- _InterlockedAdd64
- _InterlockedAdd_cpp
- _InterlockedAdd_rel_cpp
- _InterlockedAdd_rel
- _InterlockedAdd64_rel_cpp
- _InterlockedAdd64_cpp
- _InterlockedAdd_acq_cpp
- _InterlockedAdd64_nf
- _InterlockedAdd
helpviewer_keywords:
- _InterlockedAdd_nf intrinsic
- _InterlockedAdd_rel intrinsic
- _InterlockedAdd intrinsic
- _InterlockedAdd64 intrinsic
- _InterlockedAdd64_acq intrinsic
- _InterlockedAdd64_nf intrinsic
- _InterlockedAdd_acq intrinsic
- _InterlockedAdd64_rel intrinsic
ms.assetid: 3d319603-ea9c-4fdd-ae61-e52430ccc3b1
ms.openlocfilehash: c540cfe6abd8ae6dc2933e7fb21e2a331c21ea71
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217727"
---
# <a name="_interlockedadd-intrinsic-functions"></a>Funkcje wewnętrzne _InterlockedAdd

**Microsoft Specific**

Te funkcje wykonują niepodzielną dodanie, co gwarantuje, że operacja zostanie zakończona pomyślnie, gdy więcej niż jeden wątek ma dostęp do zmiennej udostępnionej.

## <a name="syntax"></a>Składnia

```C
long _InterlockedAdd(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_acq(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_nf(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_rel(
   long volatile * Addend,
   long Value
);
__int64 _InterlockedAdd64(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_acq(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_nf (
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_rel(
   __int64 volatile * Addend,
   __int64 Value
);
```

### <a name="parameters"></a>Parametry

*Składnik dodawania*\
[in. out] Wskaźnik na liczbę całkowitą, która ma zostać dodana; zastąpione przez wynik dodania.

*Wartościami*\
podczas Wartość do dodania.

## <a name="return-value"></a>Wartość zwracana

Obie funkcje zwracają wynik dodania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_InterlockedAdd`|ARM, ARM64|
|`_InterlockedAdd_acq`|ARM, ARM64|
|`_InterlockedAdd_nf`|ARM, ARM64|
|`_InterlockedAdd_rel`|ARM, ARM64|
|`_InterlockedAdd64`|ARM, ARM64|
|`_InterlockedAdd64_acq`|ARM, ARM64|
|`_InterlockedAdd64_nf`|ARM, ARM64|
|`_InterlockedAdd64_rel`|ARM, ARM64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Wersje tych funkcji z sufiksami `_acq` lub `_rel` wykonują komplementarne Dodawanie przy użyciu semantyki pozyskiwania lub wydawania. *Uzyskanie semantyki* oznacza, że wynik operacji jest widoczny dla wszystkich wątków i procesorów przed późniejszym odczytaniem i zapisem pamięci. Pobieranie jest przydatne podczas wprowadzania sekcji krytycznej. *Semantyka wersji* oznacza, że wszystkie operacje odczytu i zapisu pamięci są wymuszane jako widoczne dla wszystkich wątków i procesorów, zanim wynik operacji zostanie wyświetlony jako widoczny. Wydanie jest przydatne przy opuszczaniu sekcji krytycznej. Elementy wewnętrzne z `_nf` sufiksem ("No ogrodzeni") nie działają jako bariera pamięci.

Te procedury są dostępne tylko jako elementy wewnętrzne.

## <a name="example"></a>Przykład

```cpp
// interlockedadd.cpp
// Compile with: /Oi /EHsc
// processor: ARM
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_InterlockedAdd)

int main()
{
        long data1 = 0xFF00FF00;
        long data2 = 0x00FF0000;
        long retval;
        retval = _InterlockedAdd(&data1, data2);
        printf("0x%x 0x%x 0x%x", data1, data2, retval);
}
```

## <a name="output"></a>Dane wyjściowe

```Output
0xffffff00 0xff0000 0xffffff00
```

## <a name="example"></a>Przykład

```cpp
// interlockedadd64.cpp
// compile with: /Oi /EHsc
// processor: ARM
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_InterlockedAdd64)

int main()
{
        __int64 data1 = 0x0000FF0000000000;
        __int64 data2 = 0x00FF0000FFFFFFFF;
        __int64 retval;
        cout << hex << data1 << " + " << data2 << " = " ;
        retval = _InterlockedAdd64(&data1, data2);
        cout << data1 << endl;
        cout << "Return value: " << retval << endl;
}
```

## <a name="output"></a>Dane wyjściowe

```Output
ff0000000000 + ff0000ffffffff = ffff00ffffffff
Return value: ffff00ffffffff
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

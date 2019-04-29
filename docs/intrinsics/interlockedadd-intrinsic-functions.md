---
title: _InterlockedAdd — funkcje wewnętrzne
ms.date: 12/17/2018
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
ms.openlocfilehash: 348e936bb05796e36ae45095f25b943076cec464
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349520"
---
# <a name="interlockedadd-intrinsic-functions"></a>_InterlockedAdd — funkcje wewnętrzne

**Microsoft Specific**

Te funkcje wykonać dodatek atomic upewnia się, że operacja zakończy się pomyślnie po więcej niż jeden wątek ma dostęp do udostępnionej zmiennej.

## <a name="syntax"></a>Składnia

```
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

#### <a name="parameters"></a>Parametry

*Składnik dodawania*<br/>
[out w] Wskaźnik do liczby całkowitej, która ma zostać dodany do; zastępuje wynik dodawania.

*Wartość*<br/>
[in] Wartość do dodania.

## <a name="return-value"></a>Wartość zwracana

Obie funkcje zwracają wynik dodawania.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_InterlockedAdd`|ARM|
|`_InterlockedAdd_acq`|ARM|
|`_InterlockedAdd_nf`|ARM|
|`_InterlockedAdd_rel`|ARM|
|`_InterlockedAdd64`|ARM|
|`_InterlockedAdd64_acq`|ARM|
|`_InterlockedAdd64_nf`|ARM|
|`_InterlockedAdd64_rel`|ARM|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Wersje tych funkcji `_acq` lub `_rel` sufiksy przeprowadzić Dodawanie blokowane, zgodnie z semantyką nabywania lub wersji. *Semantyka nabycia* oznacza, że wynik operacji stają się widoczne dla wszystkich wątków i procesorów przed wszystkie nowsze pamięci operacji odczytu i zapisu. Uzyskiwanie jest przydatne w przypadku wprowadzania sekcję krytyczną. *Zwolnij semantyki* wymuszenie były widoczne dla wszystkich wątków i procesorów, zanim wynik operacji stają się widoczne dla samego oznacza, że wszystkie pamięci operacji odczytu i zapisu. Wersja jest przydatne podczas opuszczania sekcję krytyczną. Funkcje wewnętrzne z `_nf` sufiks ("nie ogranicznika") nie działają jako czynnik blokujący pamięci.

Te procedury są dostępne tylko jako funkcje wewnętrzne.

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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)<br/>
[Konflikty z kompilatorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
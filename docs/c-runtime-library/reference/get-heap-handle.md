---
title: _get_heap_handle
ms.date: 4/2/2020
api_name:
- _get_heap_handle
- _o__get_heap_handle
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_heap_handle
- get_heap_handle
helpviewer_keywords:
- heap functions
- memory allocation, heap memory
- _get_heap_handle function
- get_heap_handle function
ms.assetid: a4d05049-8528-494a-8281-a470d1e1115c
ms.openlocfilehash: e2e48e4acc26c7b8317a2d358d1a426d012ec508
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345090"
---
# <a name="_get_heap_handle"></a>_get_heap_handle

Zwraca dojście stosu, który jest używany przez system wykonywania języka C.

## <a name="syntax"></a>Składnia

```C
intptr_t _get_heap_handle( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca dojście do sterty Win32 używanej przez system czasu wykonywania języka C.

## <a name="remarks"></a>Uwagi

Użyj tej funkcji, jeśli chcesz wywołać [HeapSetInformation](/windows/win32/api/heapapi/nf-heapapi-heapsetinformation) i włączyć sterty niskiego fragmentacji na stercie CRT.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_heap_handle**|\<> malloc.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="sample"></a>Przykład

```cpp
// crt_get_heap_handle.cpp
// compile with: /MT
#include <windows.h>
#include <malloc.h>
#include <stdio.h>

int main(void)
{
    intptr_t hCrtHeap = _get_heap_handle();
    ULONG ulEnableLFH = 2;
    if (HeapSetInformation((PVOID)hCrtHeap,
                           HeapCompatibilityInformation,
                           &ulEnableLFH, sizeof(ulEnableLFH)))
        puts("Enabling Low Fragmentation Heap succeeded");
    else
        puts("Enabling Low Fragmentation Heap failed");
    return 0;
}
```

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>

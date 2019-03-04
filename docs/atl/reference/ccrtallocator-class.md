---
title: Klasa CCRTAllocator
ms.date: 11/04/2016
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
ms.openlocfilehash: c08d594e1c0f4d532f46961e266bf6ced98c51b2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287365"
---
# <a name="ccrtallocator-class"></a>Klasa CCRTAllocator

Ta klasa dostarcza metody do zarządzania ilości pamięci za pomocą procedury pamięci CRT.

## <a name="syntax"></a>Składnia

```
class ATL::CCRTAllocator
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCRTAllocator::Allocate](#allocate)|(Statyczny) Wywołaj tę metodę można przydzielić pamięci.|
|[CCRTAllocator::Free](#free)|(Statyczny) Wywołaj tę metodę, aby zwolnić pamięć.|
|[CCRTAllocator::Reallocate](#reallocate)|(Statyczny) Wywołaj tę metodę w celu ponownego przydzielenia pamięci.|

## <a name="remarks"></a>Uwagi

Ta klasa jest używana przez [CHeapPtr](../../atl/reference/cheapptr-class.md) do dostarczenia pamięci CRT procedur alokacji. Klasa odpowiednika [CComAllocator](../../atl/reference/ccomallocator-class.md), oferuje te same metody, za pomocą procedury COM.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

##  <a name="allocate"></a>  CCRTAllocator::Allocate

Wywołaj tę funkcję statyczne można przydzielić pamięci.

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Liczba bajtów do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca pusty wskaźnik do przydzielonego miejsca lub wartość NULL, jeśli ma za mało pamięci.

### <a name="remarks"></a>Uwagi

Przydziela pamięć. Zobacz [— funkcja malloc](../../c-runtime-library/reference/malloc.md) Aby uzyskać więcej informacji.

##  <a name="free"></a>  CCRTAllocator::Free

Wywołaj tę funkcję statycznej, aby zwolnić pamięć.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do alokacji pamięci.

### <a name="remarks"></a>Uwagi

Zwalnia ilość przydzielonej pamięci. Zobacz [bezpłatne](../../c-runtime-library/reference/free.md) Aby uzyskać więcej informacji.

##  <a name="reallocate"></a>  CCRTAllocator::Reallocate

Wywołaj tę funkcję statycznych w celu ponownego przydzielenia pamięci.

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do alokacji pamięci.

*nBytes*<br/>
Liczba bajtów w celu ponownego przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca pusty wskaźnik do przydzielonego miejsca lub wartość NULL, jeśli pamięć jest niewystarczająca.

### <a name="remarks"></a>Uwagi

Zmienia rozmiar ilość ilość przydzielonej pamięci. Zobacz [realloc](../../c-runtime-library/reference/realloc.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Klasa CComAllocator](../../atl/reference/ccomallocator-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)

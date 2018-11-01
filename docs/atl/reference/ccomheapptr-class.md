---
title: Klasa CComHeapPtr
ms.date: 11/04/2016
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
ms.openlocfilehash: eaa21700f63ae07565dba4b8b3b5dabac69e0168
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553741"
---
# <a name="ccomheapptr-class"></a>Klasa CComHeapPtr

Klasa inteligentnego wskaźnika do zarządzania wskaźniki stosu.

## <a name="syntax"></a>Składnia

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, który ma być przechowywany na stosie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|Konstruktor.|

## <a name="remarks"></a>Uwagi

`CComHeapPtr` pochodzi od klasy `CHeapPtr`, ale używa [CComAllocator](../../atl/reference/ccomallocator-class.md) można przydzielić pamięci za pomocą procedury COM. Zobacz [CHeapPtr](../../atl/reference/cheapptr-class.md) i [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) dla metod, które są dostępne.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="ccomheapptr"></a>  CComHeapPtr::CComHeapPtr

Konstruktor.

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Istniejące `CComHeapPtr` obiektu.

### <a name="remarks"></a>Uwagi

Opcjonalnie można utworzyć wskaźnik stosu przy użyciu istniejącego `CComHeapPtr` obiektu. Jeśli tak, nowe `CComHeapPtr` obiektu przyjmuje odpowiedzialność za zarządzanie nowy wskaźnik i zasobami.

## <a name="see-also"></a>Zobacz też

[Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Klasa CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)<br/>
[Klasa CComAllocator](../../atl/reference/ccomallocator-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)

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
ms.openlocfilehash: 78cadfff9a278cf080393ab919f3891b201c91aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327776"
---
# <a name="ccomheapptr-class"></a>Klasa CComHeapPtr

Klasa inteligentnego wskaźnika do zarządzania wskaźnikami sterty.

## <a name="syntax"></a>Składnia

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, który ma być przechowywany na stercie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|Konstruktor.|

## <a name="remarks"></a>Uwagi

`CComHeapPtr`pochodzi od `CHeapPtr`, ale używa [CComAllocator](../../atl/reference/ccomallocator-class.md) do przydzielania pamięci przy użyciu procedur COM. Zobacz [CHeapPtr](../../atl/reference/cheapptr-class.md) i [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) dla dostępnych metod.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cheapptrbase](../../atl/reference/cheapptrbase-class.md)

[Cheapptr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccomheapptrccomheapptr"></a><a name="ccomheapptr"></a>CComHeapPtr::CComHeapPtr

Konstruktor.

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>Parametry

*Pdata*<br/>
Istniejący `CComHeapPtr` obiekt.

### <a name="remarks"></a>Uwagi

Wskaźnik sterty można opcjonalnie utworzyć `CComHeapPtr` przy użyciu istniejącego obiektu. Jeśli tak, `CComHeapPtr` nowy obiekt przejmuje odpowiedzialność za zarządzanie nowym wskaźnikiem i zasobami.

## <a name="see-also"></a>Zobacz też

[Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Klasa CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)<br/>
[Klasa CComAllocator](../../atl/reference/ccomallocator-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)

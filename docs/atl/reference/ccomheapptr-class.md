---
title: Klasa CComHeapPtr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
dev_langs:
- C++
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c7a5b30ca507387b1529c9e9726e48735c844fac
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764832"
---
# <a name="ccomheapptr-class"></a>Klasa CComHeapPtr

Klasa inteligentnego wskaźnika do zarządzania wskaźniki stosu.

## <a name="syntax"></a>Składnia

```
template<typename T>  
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>Parametry

*T*  
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

*pData*  
Istniejące `CComHeapPtr` obiektu.

### <a name="remarks"></a>Uwagi

Opcjonalnie można utworzyć wskaźnik stosu przy użyciu istniejącego `CComHeapPtr` obiektu. Jeśli tak, nowe `CComHeapPtr` obiektu przyjmuje odpowiedzialność za zarządzanie nowy wskaźnik i zasobami.

## <a name="see-also"></a>Zobacz też

[Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)   
[Klasa CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)   
[Klasa CComAllocator](../../atl/reference/ccomallocator-class.md)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)

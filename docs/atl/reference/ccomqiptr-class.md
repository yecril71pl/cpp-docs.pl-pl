---
title: Klasa CComQIPtr
ms.date: 11/04/2016
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
ms.openlocfilehash: 2b1d8b92fbc5e95a5061956bafc4922d249a6f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327416"
---
# <a name="ccomqiptr-class"></a>Klasa CComQIPtr

Klasa inteligentnego wskaźnika do zarządzania wskaźnikami interfejsu COM.

## <a name="syntax"></a>Składnia

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Interfejs COM określający typ wskaźnika do przechowywania.

*piid*<br/>
Wskaźnik do identyfikatora *T*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Konstruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComQIPtr::operator =](#operator_eq)|Przypisuje wskaźnik do wskaźnika elementu członkowskiego.|

## <a name="remarks"></a>Uwagi

ATL używa `CComQIPtr` i [CComPtr](../../atl/reference/ccomptr-class.md) do zarządzania wskaźnikami interfejsu COM, które pochodzą z [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Obie klasy wykonują automatyczne zliczanie odwołań za pośrednictwem wywołań do `AddRef` i `Release`. Przeciążone operatory obsługują operacje wskaźnika.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Ccomptrbase](../../atl/reference/ccomptrbase-class.md)

[Ccomptr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli.h

## <a name="ccomqiptrccomqiptr"></a><a name="ccomqiptr"></a>CComQIPtr::CComQIPtr

Konstruktor.

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>Parametry

*Lp*<br/>
Służy do inicjowania wskaźnika interfejsu.

*T*<br/>
Interfejs COM.

*piid*<br/>
Wskaźnik do identyfikatora *T*.

## <a name="ccomqiptroperator-"></a><a name="operator_eq"></a>CComQIPtr::operator =

Operator przypisania.

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>Parametry

*Lp*<br/>
Służy do inicjowania wskaźnika interfejsu.

*T*<br/>
Interfejs COM.

*piid*<br/>
Wskaźnik do identyfikatora *T*.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `CComQIPtr` zaktualizowanego obiektu.

## <a name="see-also"></a>Zobacz też

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr::CComQIPtr](#ccomqiptr)<br/>
[Klasa CComPtrBase](../../atl/reference/ccomptrbase-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)

---
title: Klasa CComQIPtr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4c35ab13d5cf2448135b1e07405a1e31a5eec86
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116675"
---
# <a name="ccomqiptr-class"></a>Klasa CComQIPtr

Klasa inteligentnego wskaźnika do zarządzania wskaźniki interfejsu COM.

## <a name="syntax"></a>Składnia

```
template<class T, const IID* piid= &__uuidof(T)>
class CComQIPtr: public CComPtr<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Interfejs COM, określając typ wskaźnika, które mają być przechowywane.

*piid*<br/>
Wskaźnik do identyfikatora IID z *T*.

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

Używa ATL `CComQIPtr` i [CComPtr](../../atl/reference/ccomptr-class.md) Zarządzanie wskaźniki interfejsu COM, z których oba dziedziczyć [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Obie klasy wykonywać automatyczne zliczanie za pośrednictwem wywołania `AddRef` i `Release`. Przeciążone operatory obsługiwać operacje wskaźnika.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

[CComPtr](../../atl/reference/ccomptr-class.md)

`CComQIPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli.h

##  <a name="ccomqiptr"></a>  CComQIPtr::CComQIPtr

Konstruktor.

```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```

### <a name="parameters"></a>Parametry

*LP*<br/>
Używane do zainicjowania wskaźnika interfejsu.

*T*<br/>
Interfejs COM.

*piid*<br/>
Wskaźnik do identyfikatora IID z *T*.

##  <a name="operator_eq"></a>  CComQIPtr::operator =

Operator przypisania.

```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```

### <a name="parameters"></a>Parametry

*LP*<br/>
Używane do zainicjowania wskaźnika interfejsu.

*T*<br/>
Interfejs COM.

*piid*<br/>
Wskaźnik do identyfikatora IID z *T*.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do zaktualizowanego `CComQIPtr` obiektu.

## <a name="see-also"></a>Zobacz też

[CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)<br/>
[CComQIPtr::CComQIPtr](#ccomqiptr)<br/>
[Klasa CComPtrBase](../../atl/reference/ccomptrbase-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasa CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)

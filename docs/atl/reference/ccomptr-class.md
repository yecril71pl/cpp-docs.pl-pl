---
title: Klasa CComPtr
description: Przewodnik po klasie CComPtr klasy CComPtr (Active Template Library) firmy Microsoft C++.Reference guide to the Microsoft C++ Active Template Library (ATL) class CComPtr.
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 855466225db2672755658dcbbc9a266d09e0e7be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327526"
---
# <a name="ccomptr-class"></a>Klasa CComPtr

Klasa inteligentnego wskaźnika do zarządzania wskaźnikami interfejsu COM.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>Parametry

*T*<br/>
Interfejs COM określający typ wskaźnika do przechowywania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPtr::CComPtr](#ccomptr)|Konstruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComPtr::operator =](#operator_eq)|Przypisuje wskaźnik do wskaźnika elementu członkowskiego.|

## <a name="remarks"></a>Uwagi

ATL używa `CComPtr` i [CComQIPtr](../../atl/reference/ccomqiptr-class.md) do zarządzania wskaźnikami interfejsu COM. Oba pochodzą z [CComPtrBase](../../atl/reference/ccomptrbase-class.md), a oba wykonują automatyczne liczenie odwołań.

Klasy `CComPtr` i [CComQIPtr](../../atl/reference/ccomqiptr-class.md) mogą pomóc wyeliminować przecieki pamięci, wykonując automatyczne liczenie odwołań.  Następujące funkcje wykonują te same operacje logiczne. Jednak druga wersja może być mniej podatne na błędy, ponieważ używa `CComPtr` klasy:

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

W kompilacjach debugowania łącz się z adresem atlsd.lib w celu śledzenia kodu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Ccomptrbase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccomptrccomptr"></a><a name="ccomptr"></a>CComPtr::CComPtr

Konstruktor.

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>Parametry

*Lp*<br/>
Służy do inicjowania wskaźnika interfejsu.

*T*<br/>
Interfejs COM.

### <a name="remarks"></a>Uwagi

Konstruktory, które `AddRef` podejmują wywołanie argumentu na *lp*, jeśli nie jest wskaźnik null. Obiekt należący do wartości `Release` null otrzymuje wywołanie zniszczenia obiektu CComPtr lub jeśli nowy obiekt jest przypisany do obiektu CComPtr.

## <a name="ccomptroperator-"></a><a name="operator_eq"></a>CComPtr::operator =

Operator przypisania.

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `CComPtr` zaktualizowanego obiektu

### <a name="remarks"></a>Uwagi

Ta operacja AddRefs nowy obiekt i zwalnia istniejący obiekt, jeśli istnieje.

## <a name="see-also"></a>Zobacz też

[CComPtr::CComPtr](#ccomptr)<br/>
[CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)

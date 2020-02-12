---
title: Klasa CComPtr
description: Przewodnik referencyjny do klasy C++ Microsoft Active Template Library (ATL) CComPtr.
ms.date: 02/07/2020
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
ms.openlocfilehash: 74a12b460f55a782fa2747b02f7d00287786fae6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127408"
---
# <a name="ccomptr-class"></a>Klasa CComPtr

Klasa inteligentnego wskaźnika do zarządzania wskaźnikami interfejsu COM.

## <a name="syntax"></a>Składnia

```cpp
template<class T>
class CComPtr
```

### <a name="parameters"></a>Parametry

*&*<br/>
Interfejs COM określający typ wskaźnika, który ma być przechowywany.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CComPtr:: CComPtr](#ccomptr)|Konstruktor.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CComPtr:: operator =](#operator_eq)|Przypisuje wskaźnik do wskaźnika elementu członkowskiego.|

## <a name="remarks"></a>Uwagi

ATL używa `CComPtr` i [CComQIPtr](../../atl/reference/ccomqiptr-class.md) do zarządzania wskaźnikami interfejsu com. Oba są wyprowadzane z [CComPtrBase](../../atl/reference/ccomptrbase-class.md)i oba są automatycznie zliczane odwołania.

Klasy `CComPtr` i [CComQIPtr](../../atl/reference/ccomqiptr-class.md) mogą pomóc wyeliminować przecieki pamięci, wykonując automatyczne zliczanie odwołań.  Poniższe funkcje wykonują te same operacje logiczne. Jednak druga wersja może być mniej podatna na błędy, ponieważ używa klasy `CComPtr`:

[!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]

[!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]

W kompilacjach debugowania Połącz atlsd. lib na potrzeby śledzenia kodu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CComPtrBase](../../atl/reference/ccomptrbase-class.md)

`CComPtr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="ccomptr"></a>CComPtr:: CComPtr

Konstruktor.

```cpp
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```

### <a name="parameters"></a>Parametry

*LP*<br/>
Służy do inicjowania wskaźnika interfejsu.

*&*<br/>
Interfejs COM.

### <a name="remarks"></a>Uwagi

Konstruktory, które przyjmują argument `AddRef` na *LP*, jeśli nie jest to wskaźnik o wartości null. Obiekt posiadający wartość inną niż null pobiera `Release` wywołanie na zniszczeniu obiektu CComPtr lub, jeśli nowy obiekt jest przypisany do obiektu CComPtr.

## <a name="operator_eq"></a>CComPtr:: operator =

Operator przypisania.

```cpp
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wskaźnik do zaktualizowanego obiektu `CComPtr`

### <a name="remarks"></a>Uwagi

Ta operacja służy do AddRefs nowego obiektu i zwalnia istniejący obiekt, jeśli taki istnieje.

## <a name="see-also"></a>Zobacz też

[CComPtr:: CComPtr](#ccomptr)<br/>
[CComQIPtr:: CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)

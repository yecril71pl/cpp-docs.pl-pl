---
title: Klasa CBookmark
ms.date: 11/04/2016
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
- ATL.CBookmark<0>.GetBuffer
- ATL.CBookmark.GetBuffer
- ATL::CBookmark<0>::GetBuffer
- ATL::CBookmark::GetBuffer
- CBookmark.GetBuffer
- ATL::CBookmark<nSize>::GetBuffer
- ATL.CBookmark<nSize>.GetBuffer
- CBookmark<0>.GetBuffer
- CBookmark<nSize>::GetBuffer
- CBookmark<0>::GetBuffer
- CBookmark<nSize>.GetBuffer
- CBookmark::GetBuffer
- CBookmark::GetSize
- ATL.CBookmark<nSize>.GetSize
- CBookmark<nSize>.GetSize
- CBookmark.GetSize
- ATL::CBookmark::GetSize
- CBookmark<0>::GetSize
- ATL::CBookmark<nSize>::GetSize
- ATL.CBookmark<0>.GetSize
- ATL::CBookmark<0>::GetSize
- ATL.CBookmark.GetSize
- CBookmark<0>.GetSize
- CBookmark<nSize>::GetSize
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
- CBookmark<0>::operator=
- CBookmark<0>.operator=
- ATL.CBookmark.operator=
- CBookmark::operator=
- ATL.CBookmark<0>.operator=
- ATL::CBookmark<0>::operator=
- CBookmark.operator=
- ATL::CBookmark::operator=
helpviewer_keywords:
- CBookmark class
- CBookmark class, constructor
- GetBuffer method
- GetSize method
- SetBookmark method
- = operator, with OLE DB templates
- operator =, bookmarks
- operator=, bookmarks
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
ms.openlocfilehash: 4013e40c364593676ebb099804304ffb2adb42c1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838480"
---
# <a name="cbookmark-class"></a>Klasa CBookmark

Przechowuje w buforze wartość zakładki.

## <a name="syntax"></a>Składnia

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
Rozmiar buforu zakładki w bajtach. Gdy *nSize* ma wartość zero, bufor zakładki zostanie dynamicznie utworzony w czasie wykonywania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|-|-|
|[CBookmark](#cbookmark)|Konstruktor|
|[GetBuffer](#getbuffer)|Pobiera wskaźnik do buforu.|
|[GetSize](#getsize)|Pobiera rozmiar buforu w bajtach.|
|[SetBookmark](#setbookmark)|Ustawia wartość zakładki.|

### <a name="operators"></a>Operatory

| Nazwa | Opis |
|-|-|
|[operator =](#operator)|Przypisuje jedną `CBookmark` klasę do innej.|

## <a name="remarks"></a>Uwagi

`CBookmark<0>` jest specjalizacją szablonu `CBookmark` ; jego bufor jest tworzony dynamicznie w czasie wykonywania.

## <a name="cbookmarkcbookmark"></a><a name="cbookmark"></a> CBookmark:: CBookmark

Konstruktor.

### <a name="syntax"></a>Składnia

```cpp
CBookmark();
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>Parametry

*nSize*<br/>
podczas Rozmiar buforu zakładki w bajtach.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja ustawia bufor na wartość NULL, a rozmiar buforu na 0. Druga funkcja ustawia rozmiar buforu na *nSize*i bufor na tablicę bajtową bajtów *nSize* .

> [!NOTE]
> Ta funkcja jest dostępna tylko w `CBookmark<0>` .

## <a name="cbookmarkgetbuffer"></a><a name="getbuffer"></a> CBookmark:: GetBuffer

Pobiera wskaźnik do buforu zakładek.

### <a name="syntax"></a>Składnia

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu zakładek.

## <a name="cbookmarkgetsize"></a><a name="getsize"></a> CBookmark:: GetSize

Pobiera rozmiar buforu zakładki.

### <a name="syntax"></a>Składnia

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar buforu w bajtach.

## <a name="cbookmarksetbookmark"></a><a name="setbookmark"></a> CBookmark:: SetBookmark

Kopiuje wartość zakładki przywoływaną przez *pBuffer* do `CBookmark` buforu i ustawia rozmiar buforu na *nSize*.

### <a name="syntax"></a>Składnia

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>Parametry

*nSize*<br/>
podczas Rozmiar buforu zakładek.

*pBuffer*<br/>
podczas Wskaźnik do tablicy bajtów zawierającej wartość zakładki.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta funkcja jest dostępna tylko w `CBookmark<0>` .

## <a name="cbookmarkoperator-"></a><a name="operator"></a> CBookmark:: operator =

Przypisuje `CBookmark` obiekt do innego.

### <a name="syntax"></a>Składnia

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>Uwagi

Ten operator jest wymagany tylko w `CBookmark<0>` .

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)

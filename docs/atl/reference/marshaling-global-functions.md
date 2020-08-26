---
title: Kierowanie funkcji globalnych
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: 79b19b613fbae49c0f8338dcadd2225e092fb371
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835327"
---
# <a name="marshaling-global-functions"></a>Kierowanie funkcji globalnych

Te funkcje zapewniają obsługę organizowania i konwertowania danych kierujących do wskaźników interfejsu.

> [!IMPORTANT]
> Funkcje wymienione w poniższej tabeli nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

|Nazwa|Opis|
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Zwalnia dane Marshal i `IStream` wskaźnik.|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Tworzy nowy obiekt strumienia i kierujący określony wskaźnik interfejsu.|
|[AtlUnmarshalPtr](#atlunmarshalptr)|Konwertuje dane kierujące strumienia do wskaźnika interfejsu.|

## <a name="requirements"></a>Wymagania:

**Nagłówek:** atlbase. h

## <a name="atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a> AtlFreeMarshalStream

Zwalnia dane organizatora w strumieniu, a następnie zwalnia wskaźnik strumienia.

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
podczas Wskaźnik do `IStream` interfejsu w strumieniu używanym do organizowania.

### <a name="example"></a>Przykład

Zobacz przykład dla [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a> AtlMarshalPtrInProc

Tworzy nowy obiekt strumienia, zapisuje identyfikator CLSID serwera proxy do strumienia i organizuje określony wskaźnik interfejsu, pisząc dane potrzebne do zainicjowania serwera proxy do strumienia.

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
podczas Wskaźnik do interfejsu, który ma być zorganizowany.

*IID*<br/>
podczas Identyfikator GUID organizowanego interfejsu.

*ppStream*<br/>
określoną Wskaźnik do `IStream` interfejsu w nowym obiekcie strumienia używanym do organizowania.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Flaga MSHLFLAGS_TABLESTRONG jest ustawiona, aby wskaźnik mógł być zorganizowany do wielu strumieni. Wskaźnik może być również nieorganizowany wiele razy.

Jeśli kierowanie zakończy się niepowodzeniem, wskaźnik strumienia zostanie opublikowany.

`AtlMarshalPtrInProc` może być używany tylko na wskaźniku do obiektu w procesie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

## <a name="atlunmarshalptr"></a><a name="atlunmarshalptr"></a> AtlUnmarshalPtr

Konwertuje dane dotyczące organizowania strumienia na wskaźnik interfejsu, którego może używać klient.

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
podczas Wskaźnik do nieorganizowanego strumienia.

*IID*<br/>
podczas Identyfikator GUID nieorganizowanego interfejsu.

*ppUnk*<br/>
określoną Wskaźnik do nieorganizowanego interfejsu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="example"></a>Przykład

Zobacz przykład dla [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)

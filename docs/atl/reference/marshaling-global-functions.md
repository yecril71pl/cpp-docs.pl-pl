---
title: Organizowanie funkcji globalnych
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: b839e93b6251a09ce79df60a49b4054d1af76cc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326265"
---
# <a name="marshaling-global-functions"></a>Organizowanie funkcji globalnych

Te funkcje zapewniają obsługę organizowania i konwertowania danych organizowania na wskaźniki interfejsu.

> [!IMPORTANT]
> Funkcji wymienionych w poniższej tabeli nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

|||
|-|-|
|[AtlFreeMarshalStream (Strumień Promienie)](#atlfreemarshalstream)|Zwalnia dane marshal `IStream` i wskaźnik.|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Tworzy nowy obiekt strumienia i marszałków określony wskaźnik interfejsu.|
|[AtlUnmarshalPtr ( AtlUnmarshalPtr )](#atlunmarshalptr)|Konwertuje dane kierowanie strumienia do wskaźnika interfejsu.|

## <a name="requirements"></a>Wymagania:

**Nagłówek:** atlbase.h

## <a name="atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a>AtlFreeMarshalStream (Strumień Promienie)

Zwalnia dane organizatora w strumieniu, a następnie zwalnia wskaźnik strumienia.

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream (Strumień)*<br/>
[w] Wskaźnik do `IStream` interfejsu w strumieniu używany do organizowania.

### <a name="example"></a>Przykład

Zobacz przykład [dla AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc

Tworzy nowy obiekt strumienia, zapisuje identyfikator CLSID serwera proxy do strumienia i organizuje określony wskaźnik interfejsu, pisząc dane potrzebne do zainicjowania serwera proxy do strumienia.

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
[w] Wskaźnik do interfejsu, który ma być organizowany.

*Iid*<br/>
[w] Identyfikator GUID interfejsu, który jest organizowany.

*Ppstream*<br/>
[na zewnątrz] Wskaźnik do `IStream` interfejsu na nowy obiekt strumienia używany do organizowania.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Flaga MSHLFLAGS_TABLESTRONG jest ustawiona, dzięki czemu wskaźnik może być kierowane do wielu strumieni. Wskaźnik może być również unmarshaled wiele razy.

Jeśli kierowanie nie powiedzie się, wskaźnik strumienia jest zwalniany.

`AtlMarshalPtrInProc`można używać tylko na wskaźniku do obiektu w trakcie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

## <a name="atlunmarshalptr"></a><a name="atlunmarshalptr"></a>AtlUnmarshalPtr ( AtlUnmarshalPtr )

Konwertuje dane dotyczące organizowania strumienia na wskaźnik interfejsu, którego może używać klient.

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>Parametry

*pStream (Strumień)*<br/>
[w] Wskaźnik do strumienia jest unmarshaled.

*Iid*<br/>
[w] Identyfikator GUID interfejsu jest unmarshaled.

*ppUnk (polski)*<br/>
[na zewnątrz] Wskaźnik do interfejsu niemarshaled.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="example"></a>Przykład

Zobacz przykład [dla AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)

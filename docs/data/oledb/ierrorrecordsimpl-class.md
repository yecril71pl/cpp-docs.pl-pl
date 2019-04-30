---
title: IErrorRecordsImpl — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
- GetErrorDescriptionString
- IErrorRecordsImpl.GetErrorDescriptionString
- IErrorRecordsImpl::GetErrorDescriptionString
- GetErrorGUID
- IErrorRecordsImpl.GetErrorGUID
- IErrorRecordsImpl::GetErrorGUID
- GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpContext
- IErrorRecordsImpl.GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpFile
- GetErrorHelpFile
- IErrorRecordsImpl.GetErrorHelpFile
- IErrorRecordsImpl.GetErrorSource
- GetErrorSource
- IErrorRecordsImpl::GetErrorSource
- IErrorRecordsImpl.AddErrorRecord
- AddErrorRecord
- IErrorRecordsImpl::AddErrorRecord
- ATL::IErrorRecordsImpl::GetBasicErrorInfo
- IErrorRecordsImpl::GetBasicErrorInfo
- GetBasicErrorInfo
- ATL.IErrorRecordsImpl.GetBasicErrorInfo
- IErrorRecordsImpl.GetBasicErrorInfo
- ATL::IErrorRecordsImpl::GetCustomErrorObject
- IErrorRecordsImpl::GetCustomErrorObject
- ATL.IErrorRecordsImpl.GetCustomErrorObject
- IErrorRecordsImpl.GetCustomErrorObject
- GetCustomErrorObject
- GetErrorInfo
- IErrorRecordsImpl.GetErrorInfo
- IErrorRecordsImpl::GetErrorInfo
- IErrorRecordsImpl::GetErrorParameters
- ATL.IErrorRecordsImpl.GetErrorParameters
- IErrorRecordsImpl.GetErrorParameters
- GetErrorParameters
- ATL::IErrorRecordsImpl::GetErrorParameters
- IErrorRecordsImpl::GetRecordCount
- ATL::IErrorRecordsImpl::GetRecordCount
- IErrorRecordsImpl.GetRecordCount
- ATL.IErrorRecordsImpl.GetRecordCount
- IErrorRecordsImpl::m_rgErrors
- IErrorRecordsImpl.m_rgErrors
- ATL.IErrorRecordsImpl.m_rgErrors
- m_rgErrors
- ATL::IErrorRecordsImpl::m_rgErrors
helpviewer_keywords:
- IErrorRecordsImpl class
- GetErrorDescriptionString method
- GetErrorGUID method
- GetErrorHelpContext method
- GetErrorHelpFile method
- GetErrorSource method
- AddErrorRecord method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetRecordCount method
- m_rgErrors
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
ms.openlocfilehash: b1ab6b0984cbf84690d69a3ffe7eb3931bf59563
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390961"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl — Klasa

Implementuje OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) interfejsu, dodawanie rekordów do i pobierania rekordów z element członkowski danych ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) typu **CAtlArray <** `RecordClass`**>**.

## <a name="syntax"></a>Składnia

```cpp
template <class T, class RecordClass = ATLERRORINFO>
class IErrorRecordsImpl : public IErrorRecords
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa pochodząca z `IErrorRecordsImpl`.

*RecordClass*<br/>
Klasa, która reprezentuje obiekt błędu OLE DB.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[GetErrorDescriptionString](#geterrordescriptionstring)|Pobiera ciąg opisu błędu z rekord błędu.|
|[Geterrorguid —](#geterrorguid)|Pobiera błąd identyfikatora GUID z rekord błędu.|
|[GetErrorHelpContext](#geterrorhelpcontext)|Pobiera identyfikator kontekstu pomocy z rekord błędu.|
|[GetErrorHelpFile](#geterrorhelpfile)|Pobiera pełną nazwę ścieżki pliku pomocy z rekord błędu.|
|[GetErrorSource](#geterrorsource)|Pobiera kod źródłowy błąd z rekord błędu.|

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[AddErrorRecord](#adderrorrecord)|Dodaje rekord do obiektu błąd OLE DB.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Zwraca podstawowe informacje o błędzie, np. kod powrotny i numer błędu specyficznego dla dostawcy.|
|[GetCustomErrorObject](#getcustomerrorobject)|Zwraca wskaźnik do interfejsu na obiekt błędu niestandardowego.|
|[GetErrorInfo](#geterrorinfo)|Zwraca [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) wskaźnik interfejsu do określonego rekordu.|
|[Geterrorparameters —](#geterrorparameters)|Zwraca parametry błędów.|
|[GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów w obiektach rekordów OLE DB.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_rgErrors](#rgerrors)|Tablica rekordów błędów.|

## <a name="geterrordescriptionstring"></a> IErrorRecordsImpl::GetErrorDescriptionString

Pobiera ciąg opisu błędu z rekord błędu.

### <a name="syntax"></a>Składnia

```cpp
LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
`ERRORINFO` Rekordów w `IErrorInfo` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik na ciąg opisujący błąd.

## <a name="geterrorguid"></a> IErrorRecordsImpl::GetErrorGUID

Pobiera błąd identyfikatora GUID z rekord błędu.

### <a name="syntax"></a>Składnia

```cpp
REFGUID GetErrorGUID(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
`ERRORINFO` Rekordów w `IErrorInfo` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do identyfikatora GUID dla błędu.

## <a name="geterrorhelpcontext"></a> IErrorRecordsImpl::GetErrorHelpContext

Pobiera identyfikator kontekstu pomocy z rekord błędu.

### <a name="syntax"></a>Składnia

```cpp
DWORD GetErrorHelpContext(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
`ERRORINFO` Rekordów w `IErrorInfo` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Identyfikator kontekstu pomocy dla błędu.

## <a name="geterrorhelpfile"></a> IErrorRecordsImpl::GetErrorHelpFile

Pobiera nazwę ścieżki pliku pomocy z rekord błędu.

### <a name="syntax"></a>Składnia

```cpp
LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
`ERRORINFO` Rekordów w `IErrorInfo` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik na ciąg, który zawiera nazwę ścieżki pliku pomocy dla błędu.

## <a name="geterrorsource"></a> IErrorRecordsImpl::GetErrorSource

Pobiera kod źródłowy, który spowodował błąd z rekord błędu.

### <a name="syntax"></a>Składnia

```cpp
LPOLESTR GetErrorSource(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
`ERRORINFO` Rekordów w `IErrorInfo` interfejsu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu zawierającego kod źródłowy dla błędu.

## <a name="adderrorrecord"></a> IErrorRecordsImpl::AddErrorRecord

Dodaje rekord do obiektu błąd OLE DB.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,
   DWORD dwLookupID,
   DISPPARAMS *pdispparams,
   IUnknown *punkCustomError,
   DWORD dwDynamicErrorID);
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords::AddErrorRecord](/previous-versions/windows/desktop/ms725362(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="getbasicerrorinfo"></a> IErrorRecordsImpl::GetBasicErrorInfo

Zwraca podstawowe informacje o błędzie, np. kod powrotny i numer błędu specyficznego dla dostawcy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,
   ERRORINFO *pErrorInfo);
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="getcustomerrorobject"></a> IErrorRecordsImpl::GetCustomErrorObject

Zwraca wskaźnik do interfejsu na obiekt błędu niestandardowego.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetCustomErrorObject )(ULONG ulRecordNum,
   REFIID riid,
   IUnknown **ppObject);
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="geterrorinfo"></a> IErrorRecordsImpl::GetErrorInfo

Zwraca [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) wskaźnik interfejsu do określonego rekordu.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetErrorInfo )(ULONG ulRecordNum,
   LCID lcid,
   IErrorInfo **ppErrorInfo);
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="geterrorparameters"></a> IErrorRecordsImpl::GetErrorParameters

Zwraca parametry błędów.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetErrorParameters )(ULONG ulRecordNum,
   DISPPARAMS *pdispparams);
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="getrecordcount"></a> IErrorRecordsImpl::GetRecordCount

Zwraca liczbę rekordów w obiektach rekordów OLE DB.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetRecordCount )(ULONG *pcRecords);
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords::GetRecordCount](/previous-versions/windows/desktop/ms722724(v=vs.85)) w *OLE DB Podręcznik programisty*.

## <a name="rgerrors"></a> IErrorRecordsImpl::m_rgErrors

Tablica rekordów błędów.

### <a name="syntax"></a>Składnia

```cpp
CAtlArray< RecordClass > m_rgErrors;
```

## <a name="see-also"></a>Zobacz także

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
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
ms.openlocfilehash: dd9e1f39d30dc8289b0236bf655c87da04b14de6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447363"
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl — Klasa

Implementuje interfejs OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) , Dodawanie rekordów do i pobieranie rekordów z elementu członkowskiego danych ([M_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) typu **CAtlArray <** `RecordClass` **>** .

## <a name="syntax"></a>Składnia

```cpp
template <class T, class RecordClass = ATLERRORINFO>
class IErrorRecordsImpl : public IErrorRecords
```

### <a name="parameters"></a>Parametry

*&*<br/>
Klasa pochodna `IErrorRecordsImpl`.

*RecordClass*<br/>
Klasa, która reprezentuje obiekt błędu OLE DB.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[GetErrorDescriptionString](#geterrordescriptionstring)|Pobiera ciąg opisu błędu z rekordu błędu.|
|[GetErrorGUID](#geterrorguid)|Pobiera identyfikator GUID błędu z rekordu błędu.|
|[GetErrorHelpContext](#geterrorhelpcontext)|Pobiera identyfikator kontekstu pomocy z rekordu błędu.|
|[GetErrorHelpFile](#geterrorhelpfile)|Pobiera pełną nazwę ścieżki pliku pomocy z rekordu błędu.|
|[GetErrorSource](#geterrorsource)|Pobiera kod źródłowy błędu z rekordu błędu.|

### <a name="interface-methods"></a>Metody interfejsu

|||
|-|-|
|[AddErrorRecord](#adderrorrecord)|Dodaje rekord do obiektu błędu OLE DB.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Zwraca podstawowe informacje o błędzie, takie jak kod powrotu i numer błędu specyficzny dla dostawcy.|
|[GetCustomErrorObject](#getcustomerrorobject)|Zwraca wskaźnik do interfejsu w obiekcie błędu niestandardowego.|
|[GetErrorInfo](#geterrorinfo)|Zwraca wskaźnik interfejsu [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) w określonym rekordzie.|
|[GetErrorParameters](#geterrorparameters)|Zwraca parametry błędu.|
|[GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów w obiekcie rekordu OLE DB.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_rgErrors](#rgerrors)|Tablica rekordów błędów.|

## <a name="geterrordescriptionstring"></a>IErrorRecordsImpl:: GetErrorDescriptionString

Pobiera ciąg opisu błędu z rekordu błędu.

### <a name="syntax"></a>Składnia

```cpp
LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
Rekord `ERRORINFO` w interfejsie `IErrorInfo`.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu opisującego błąd.

## <a name="geterrorguid"></a>IErrorRecordsImpl:: GetErrorGUID

Pobiera identyfikator GUID błędu z rekordu błędu.

### <a name="syntax"></a>Składnia

```cpp
REFGUID GetErrorGUID(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
Rekord `ERRORINFO` w interfejsie `IErrorInfo`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do identyfikatora GUID dla błędu.

## <a name="geterrorhelpcontext"></a>IErrorRecordsImpl:: GetErrorHelpContext

Pobiera identyfikator kontekstu pomocy z rekordu błędu.

### <a name="syntax"></a>Składnia

```cpp
DWORD GetErrorHelpContext(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
Rekord `ERRORINFO` w interfejsie `IErrorInfo`.

### <a name="return-value"></a>Wartość zwracana

Identyfikator kontekstu pomocy dla błędu.

## <a name="geterrorhelpfile"></a>IErrorRecordsImpl:: GetErrorHelpFile

Pobiera nazwę ścieżki pliku pomocy z rekordu błędu.

### <a name="syntax"></a>Składnia

```cpp
LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
Rekord `ERRORINFO` w interfejsie `IErrorInfo`.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik na ciąg, który zawiera nazwę ścieżki pliku pomocy dla błędu.

## <a name="geterrorsource"></a>IErrorRecordsImpl:: GetErrorSource

Pobiera kod źródłowy, który spowodował błąd z rekordu błędu.

### <a name="syntax"></a>Składnia

```cpp
LPOLESTR GetErrorSource(ERRORINFO& rCurError);
```

#### <a name="parameters"></a>Parametry

*rCurError*<br/>
Rekord `ERRORINFO` w interfejsie `IErrorInfo`.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik na ciąg zawierający kod źródłowy błędu.

## <a name="adderrorrecord"></a>IErrorRecordsImpl:: AddErrorRecord

Dodaje rekord do obiektu błędu OLE DB.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(AddErrorRecord )(ERRORINFO *pErrorInfo,
   DWORD dwLookupID,
   DISPPARAMS *pdispparams,
   IUnknown *punkCustomError,
   DWORD dwDynamicErrorID);
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords:: AddErrorRecord](/previous-versions/windows/desktop/ms725362(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="getbasicerrorinfo"></a>IErrorRecordsImpl:: GetBasicErrorInfo

Zwraca podstawowe informacje o błędzie, takie jak kod powrotu i numer błędu specyficzny dla dostawcy.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,
   ERRORINFO *pErrorInfo);
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="getcustomerrorobject"></a>IErrorRecordsImpl:: getcustomerrorobject

Zwraca wskaźnik do interfejsu w obiekcie błędu niestandardowego.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetCustomErrorObject )(ULONG ulRecordNum,
   REFIID riid,
   IUnknown **ppObject);
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords:: Getcustomerrorobject](/previous-versions/windows/desktop/ms725417(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="geterrorinfo"></a>IErrorRecordsImpl:: GetErrorInfo

Zwraca wskaźnik interfejsu [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) w określonym rekordzie.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetErrorInfo )(ULONG ulRecordNum,
   LCID lcid,
   IErrorInfo **ppErrorInfo);
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="geterrorparameters"></a>IErrorRecordsImpl:: GetErrorParameters

Zwraca parametry błędu.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetErrorParameters )(ULONG ulRecordNum,
   DISPPARAMS *pdispparams);
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="getrecordcount"></a>IErrorRecordsImpl:: GetRecordCount

Zwraca liczbę rekordów w obiekcie rekordu OLE DB.

### <a name="syntax"></a>Składnia

```cpp
STDMETHOD(GetRecordCount )(ULONG *pcRecords);
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords:: GetRecordCount](/previous-versions/windows/desktop/ms722724(v=vs.85)) w *dokumentacji programisty OLE DB*.

## <a name="rgerrors"></a>IErrorRecordsImpl:: m_rgErrors

Tablica rekordów błędów.

### <a name="syntax"></a>Składnia

```cpp
CAtlArray< RecordClass > m_rgErrors;
```

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
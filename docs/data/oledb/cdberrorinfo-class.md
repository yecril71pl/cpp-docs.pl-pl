---
title: CDBErrorInfo — Klasa
ms.date: 11/04/2016
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- CDBErrorInfo::GetErrorRecords
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
ms.openlocfilehash: 8c91beb2a305604f663d5e81b4a534a1699705cf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212037"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo — Klasa

Zapewnia obsługę przetwarzania błędów OLE DB przy użyciu interfejsu OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) .

## <a name="syntax"></a>Składnia

```cpp
class CDBErrorInfo
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Members

### <a name="methods"></a>Metody

|||
|-|-|
|[GetAllErrorInfo](#getallerrorinfo)|Zwraca wszystkie informacje o błędzie zawarte w rekordzie błędu.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Wywołuje [IErrorRecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) , aby zwrócić podstawowe informacje o określonym błędzie.|
|[GetCustomErrorObject](#getcustomerrorobject)|Wywołuje [IErrorRecords:: Getcustomerrorobject](/previous-versions/windows/desktop/ms725417(v=vs.85)) , aby zwrócić wskaźnik do interfejsu w obiekcie błędu niestandardowego.|
|[GetErrorInfo](#geterrorinfo)|Wywołuje [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) , aby zwrócić wskaźnik interfejsu `IErrorInfo` do określonego rekordu.|
|[GetErrorParameters](#geterrorparameters)|Wywołuje [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) w celu zwrócenia parametrów błędu.|
|[GetErrorRecords](#geterrorrecords)|Pobiera rekordy błędów dla określonego obiektu.|

## <a name="remarks"></a>Uwagi

Ten interfejs zwraca jeden lub więcej rekordów błędów do użytkownika. Najpierw Wywołaj [CDBErrorInfo:: GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) , aby uzyskać liczbę rekordów błędów. Następnie Wywołaj jedną z funkcji dostępu, na przykład [CDBErrorInfo:: GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md), aby pobrać informacje o błędzie dla każdego rekordu.

## <a name="cdberrorinfogetallerrorinfo"></a><a name="getallerrorinfo"></a>CDBErrorInfo:: GetAllErrorInfo

Zwraca wszystkie typy informacji o błędzie zawartych w rekordzie błędu.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetAllErrorInfo(ULONG ulRecordNum,
   LCID lcid,  BSTR* pbstrDescription,
   BSTR* pbstrSource = NULL,
   GUID* pguid = NULL,
   DWORD* pdwHelpContext = NULL,
   BSTR* pbstrHelpFile = NULL) const throw();
```

#### <a name="parameters"></a>Parametry

*ulRecordNum*<br/>
podczas Liczba liczonych od zera rekordu, dla którego mają zostać zwrócone informacje o błędzie.

*lcid*<br/>
podczas Identyfikator ustawień regionalnych dla zwracanych informacji o błędzie.

*pbstrDescription*<br/>
określoną Wskaźnik do opisu tekstu błędu lub wartości NULL, jeśli ustawienia regionalne nie są obsługiwane. Zobacz uwagi.

*pbstrSource*<br/>
określoną Wskaźnik do ciągu zawierającego nazwę składnika, który wygenerował błąd.

*pguid*<br/>
określoną Wskaźnik do identyfikatora GUID interfejsu, który definiuje błąd.

*pdwHelpContext*<br/>
określoną Wskaźnik do identyfikatora kontekstu pomocy dla błędu.

*pbstrHelpFile*<br/>
określoną Wskaźnik do ciągu zawierającego ścieżkę do pliku pomocy, który opisuje błąd.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie. Zobacz [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) w *Kompendium OLE DB programisty* dla innych zwracanych wartości.

### <a name="remarks"></a>Uwagi

Wartość wyjściowa *pbstrDescription* jest uzyskiwana wewnętrznie przez wywołanie `IErrorInfo::GetDescription`, która ustawia wartość null, jeśli ustawienia regionalne nie są obsługiwane lub jeśli są spełnione oba poniższe warunki:

1. wartość *LCID* nie jest angielski (Stany Zjednoczone) i

1. wartość *LCID* nie jest równa wartości zwracanej przez GetUserDefaultLCID.

## <a name="cdberrorinfogetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a>CDBErrorInfo:: GetBasicErrorInfo

Wywołuje [IErrorRecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) , aby zwrócić podstawowe informacje o błędzie, takie jak kod powrotu i numer błędu specyficzny dla dostawcy.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,
   ERRORINFO* pErrorInfo) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="cdberrorinfogetcustomerrorobject"></a><a name="getcustomerrorobject"></a>CDBErrorInfo:: getcustomerrorobject

Wywołuje [IErrorRecords:: Getcustomerrorobject](/previous-versions/windows/desktop/ms725417(v=vs.85)) , aby zwrócić wskaźnik do interfejsu w obiekcie błędu niestandardowego.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,
   REFIID riid,IUnknown** ppObject) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords:: Getcustomerrorobject](/previous-versions/windows/desktop/ms725417(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="cdberrorinfogeterrorinfo"></a><a name="geterrorinfo"></a>CDBErrorInfo:: GetErrorInfo

Wywołuje [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) , aby zwrócić wskaźnik interfejsu [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) do określonego rekordu.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="cdberrorinfogeterrorparameters"></a><a name="geterrorparameters"></a>CDBErrorInfo:: GetErrorParameters

Wywołuje [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) w celu zwrócenia parametrów błędu.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,
   DISPPARAMS* pdispparams) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="cdberrorinfogeterrorrecords"></a><a name="geterrorrecords"></a>CDBErrorInfo:: GetErrorRecords

Pobiera rekordy błędów dla określonego obiektu.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,
   const IID& iid,
   ULONG* pcRecords) throw();

HRESULT GetErrorRecords(ULONG* pcRecords) throw();
```

#### <a name="parameters"></a>Parametry

*Punkt*<br/>
podczas Interfejs do obiektu, dla którego mają zostać pobrane rekordy błędów.

*IID*<br/>
podczas Identyfikator IID interfejsu skojarzonego z błędem.

*pcRecords*<br/>
określoną Wskaźnik do (jedna z nich) liczby rekordów błędów.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Użyj pierwszej formy funkcji, jeśli chcesz sprawdzić, z którego interfejsu pobrać informacje o błędzie. W przeciwnym razie użyj drugiego formularza.

## <a name="see-also"></a>Zobacz też

[DBVIEWER](../../overview/visual-cpp-samples.md)<br/>
[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)

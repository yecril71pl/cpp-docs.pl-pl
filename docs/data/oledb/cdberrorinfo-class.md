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
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- GetCustomErrorObject
- GetErrorInfo
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- GetErrorRecords
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
ms.openlocfilehash: bc13137a4222ba51cf3745f9706353d48068a072
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021543"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo — Klasa

Zapewnia obsługę OLE DB wystąpił błąd podczas przetwarzania przy użyciu OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) interfejsu.

## <a name="syntax"></a>Składnia

```cpp
class CDBErrorInfo
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[GetAllErrorInfo](#getallerrorinfo)|Zwraca wszystkie zawarte w rekord błędu informacje o błędzie.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|Wywołania [IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) do zwrócenia podstawowe informacje dotyczące określonego błędu.|
|[GetCustomErrorObject](#getcustomerrorobject)|Wywołania [IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) aby zwrócić wskaźnik do interfejsu na obiekt błędu niestandardowego.|
|[GetErrorInfo](#geterrorinfo)|Wywołania [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) do zwrócenia `IErrorInfo` wskaźnik interfejsu do określonego rekordu.|
|[Geterrorparameters —](#geterrorparameters)|Wywołania [IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) zwracać parametry błędów.|
|[GetErrorRecords](#geterrorrecords)|Pobiera rekordy błędów dla określonego obiektu.|

## <a name="remarks"></a>Uwagi

Ten interfejs rekordy co najmniej jeden błąd użytkownikowi. Wywołaj [CDBErrorInfo::GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) pierwszy, aby uzyskać liczbę rekordów błędów. A następnie wywołania jednej dostępu funkcje, takie jak [CDBErrorInfo::GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md), aby pobrać informacje o błędzie dla każdego rekordu.

## <a name="getallerrorinfo"></a> CDBErrorInfo::GetAllErrorInfo

Zwraca wszystkie typy informacji o błędach zawarte w rekord błędu.

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
[in] Liczony od zera liczba rekordów, dla której ma zostać zwrócone informacje o błędzie.

*lcid*<br/>
[in] Identyfikator ustawień regionalnych dla informacji o błędzie do zwrócenia.

*pbstrDescription*<br/>
[out] Wskaźnik do tekst opisu błędu lub wartość NULL, jeśli ustawienia regionalne nie jest obsługiwana. Zobacz uwagi.

*pbstrSource*<br/>
[out] Wskaźnik do ciągu zawierającego nazwę składnika, który wygenerował błąd.

*pguid*<br/>
[out] Wskaźnik do identyfikatora GUID interfejsu, który zdefiniowany błędu.

*pdwHelpContext*<br/>
[out] Wskaźnik do identyfikator kontekstu pomocy dla błędu.

*pbstrHelpFile*<br/>
[out] Wskaźnik do ciągu zawierającą ścieżkę do pliku pomocy, który opisuje błąd.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia. Zobacz [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) w *OLE DB Podręcznik programisty* dla innych wartości zwracanych.

### <a name="remarks"></a>Uwagi

Wartość danych wyjściowych *pbstrDescription* uzyskuje się wewnętrznie przez wywołanie metody `IErrorInfo::GetDescription`, która ustawia wartość null Jeśli ustawienia regionalne nie jest obsługiwany lub jeśli są spełnione oba poniższe warunki:

1. wartość *lcid* nie jest w Stanach Zjednoczonych Język angielski i

1. wartość *lcid* jest nie jest równa wartości zwracanej przez GetUserDefaultLCID.

## <a name="getbasicerrorinfo"></a> CDBErrorInfo::GetBasicErrorInfo

Wywołania [IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) do zwrócenia podstawowe informacje o błędzie, np. kod powrotny i numer błędu specyficznego dla dostawcy.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,
   ERRORINFO* pErrorInfo) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

## <a name="getcustomerrorobject"></a> CDBErrorInfo::GetCustomErrorObject

Wywołania [IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) aby zwrócić wskaźnik do interfejsu na obiekt błędu niestandardowego.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,
   REFIID riid,IUnknown** ppObject) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

## <a name="geterrorinfo"></a> CDBErrorInfo::GetErrorInfo

Wywołania [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) do zwrócenia [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) wskaźnik interfejsu do określonego rekordu.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

## <a name="geterrorparameters"></a> CDBErrorInfo::GetErrorParameters

Wywołania [IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) zwracać parametry błędów.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,
   DISPPARAMS* pdispparams) const throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

## <a name="geterrorrecords"></a> CDBErrorInfo::GetErrorRecords

Pobiera rekordy błędów dla określonego obiektu.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,
   const IID& iid,
   ULONG* pcRecords) throw();

HRESULT GetErrorRecords(ULONG* pcRecords) throw();
```

#### <a name="parameters"></a>Parametry

*pUnk*<br/>
[in] Interfejs do obiektu, dla którego należy pobrać rekordów błędów.

*IID*<br/>
[in] Identyfikator IID interfejsu skojarzonego z powodu błędu.

*pcRecords*<br/>
[out] Wskaźnik do rekordów błędów liczba (w oparciu o jeden).

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Pierwszy formularz tej funkcji należy użyć, jeśli chcesz sprawdzić, który interfejs, aby uzyskać informacje o błędzie z. W przeciwnym razie użyj drugiego formularza.

## <a name="see-also"></a>Zobacz także

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)
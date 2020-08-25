---
title: Rejestr i funkcje globalne biblioteki typów
ms.date: 03/27/2019
f1_keywords:
- atlbase/ATL::AtlGetPerUserRegistration
- afxpriv/ATL::AfxRegCreateKey
- afxpriv/ATL::AfxRegDeleteKey
- atlbase/ATL::AtlRegisterTypeLib
- afxpriv/ATL::AfxRegOpenKey
- afxpriv/ATL::AfxRegOpenKeyEx
- afxdisp/ATL::AfxUnregisterPreviewHandler
- atlbase/ATL::AtlSetPerUserRegistration
- atlbase/ATL::AtlUnRegisterTypeLib
- atlbase/ATL::AtlLoadTypeLib
- atlbase/ATL::AtlUpdateRegistryFromResourceD
- atlbase/ATL::RegistryDataExchange
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
ms.openlocfilehash: 0f29f8cac62a7452781e8fde697cdf992db00b8c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834621"
---
# <a name="registry-and-typelib-global-functions"></a>Rejestr i funkcje globalne biblioteki typów

Te funkcje zapewniają obsługę ładowania i rejestrowania biblioteki typów.

> [!IMPORTANT]
> Funkcje wymienione w poniższych tabelach nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

|Nazwa|Opis|
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|Tworzy określony klucz rejestru.|
|[AfxRegDeleteKey](#afxregdeletekey)|Usuwa określony klucz rejestru.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Pomocnik do zarejestrowania procedury obsługi podglądu.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Pomocnik do wyrejestrowywania procedury obsługi podglądu. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Ta funkcja jest wywoływana, aby zarejestrować bibliotekę typów.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Ta funkcja jest wywoływana, aby wyrejestrować bibliotekę typów|
|[AfxRegOpenKey](#afxregopenkey)|Otwiera określony klucz rejestru.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Otwiera określony klucz rejestru.|
|[AtlLoadTypeLib](#atlloadtypelib)|Ta funkcja jest wywoływana, aby załadować bibliotekę typów.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Ta funkcja jest wywoływana, aby zaktualizować rejestr z dostarczonego zasobu.|
|[RegistryDataExchange](#registrydataexchange)|Ta funkcja jest wywoływana, aby odczytywać dane z lub zapisywać do rejestru systemowego. Wywoływane przez [makra wymiany danych rejestru](../../atl/reference/registry-data-exchange-macros.md).|

Te funkcje kontrolują węzeł rejestru używany przez program do przechowywania informacji.

|Nazwa|Opis|
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Pobiera czy aplikacja przekierowuje dostęp do rejestru do węzła **HKEY_CURRENT_USER** ( **HKCU**).|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Określa, czy aplikacja przekierowuje dostęp do rejestru do węzła **HKEY_CURRENT_USER** ( **HKCU**).|

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="atlgetperuserregistration"></a><a name="atlgetperuserregistration"></a> AtlGetPerUserRegistration

Użyj tej funkcji, aby określić, czy aplikacja przekierowuje dostęp do rejestru do węzła **HKEY_CURRENT_USER** (**HKCU**).

### <a name="syntax"></a>Składnia

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>Parametry

*pEnabled*<br/>
określoną Wartość TRUE wskazuje, że informacje rejestru są kierowane do węzła **HKCU** ; Wartość FALSE oznacza, że aplikacja zapisuje informacje rejestru w domyślnym węźle. Domyślnym węzłem jest **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda zakończy się pomyślnie, w przeciwnym razie kod błędu HRESULT w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Przekierowywanie rejestru nie jest domyślnie włączone. Po włączeniu tej opcji dostęp do rejestru zostanie przekierowany do **HKEY_CURRENT_USER \software\classes**.

Przekierowanie nie jest globalne. Przekierowanie rejestru ma wpływ tylko na platformy MFC i ATL.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="afxregcreatekey"></a><a name="afxregcreatekey"></a> AfxRegCreateKey

Tworzy określony klucz rejestru.

### <a name="syntax"></a>Składnia

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Uchwyt do otwartego klucza rejestru.

*lpSubKey*<br/>
Nazwa klucza, który zostanie otwarty lub utworzony przez tę funkcję.

*phkResult*<br/>
Wskaźnik do zmiennej, która otrzymuje dojście do otwartego lub utworzonego klucza.

*pTM*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja się nie powiedzie, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w Winerror. h.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXPRIV. h

## <a name="afxregdeletekey"></a><a name="afxregdeletekey"></a> AfxRegDeleteKey

Usuwa określony klucz rejestru.

### <a name="syntax"></a>Składnia

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Uchwyt do otwartego klucza rejestru.

*lpSubKey*<br/>
Nazwa klucza, który ma zostać usunięty.

*pTM*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja się nie powiedzie, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w Winerror. h.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXPRIV. h

## <a name="afxregisterpreviewhandler"></a>

Pomocnik do zarejestrowania procedury obsługi podglądu.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>Parametry

*lpszCLSID*<br/>
Określa identyfikator CLSID programu obsługi.

*lpszShortTypeName*<br/>
Określa ProgID programu obsługi.

*lpszFilterExt*<br/>
Określa rozszerzenie pliku zarejestrowane w ramach tej procedury obsługi.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="atlregistertypelib"></a><a name="atlregistertypelib"></a> AtlRegisterTypeLib

Ta funkcja jest wywoływana, aby zarejestrować bibliotekę typów.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*hInstTypeLib*<br/>
Uchwyt do wystąpienia modułu.

*lpszIndex*<br/>
Ciąg w formacie " \\ \n", gdzie N jest indeksem liczbowym zasobu biblioteki typów. Może mieć wartość NULL, jeśli indeks nie jest wymagany.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywana przez [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) i [CAtlComModule:: RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="afxregopenkey"></a><a name="afxregopenkey"></a> AfxRegOpenKey

Otwiera określony klucz rejestru.

### <a name="syntax"></a>Składnia

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Uchwyt do otwartego klucza rejestru.

*lpSubKey*<br/>
Nazwa klucza, który zostanie otwarty lub utworzony przez tę funkcję.

*phkResult*<br/>
Wskaźnik do zmiennej, która otrzymuje dojście do tworzonego klucza.

*pTM*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja się nie powiedzie, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w Winerror. h.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXPRIV. h

## <a name="afxregopenkeyex"></a><a name="afxregopenkeyex"></a> AfxRegOpenKeyEx

Otwiera określony klucz rejestru.

### <a name="syntax"></a>Składnia

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Uchwyt do otwartego klucza rejestru.

*lpSubKey*<br/>
Nazwa klucza, który zostanie otwarty lub utworzony przez tę funkcję.

*ulOptions*<br/>
Ten parametr jest zarezerwowany i musi mieć wartość zero.

*samDesired*<br/>
Maska, która określa odpowiednie prawa dostępu do klucza.

*phkResult*<br/>
Wskaźnik do zmiennej, która otrzymuje dojście do otwartego klucza.

*pTM*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja się nie powiedzie, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w Winerror. h.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXPRIV. h

## <a name="afxunregisterpreviewhandler"></a><a name="afxunregisterpreviewhandler"></a> AfxUnregisterPreviewHandler

Pomocnik do wyrejestrowywania procedury obsługi podglądu.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>Parametry

*lpszCLSID*<br/>
Określa identyfikator CLSID programu obsługi, który ma zostać wyrejestrowany.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="atlsetperuserregistration"></a><a name="atlsetperuserregistration"></a> AtlSetPerUserRegistration

Określa, czy aplikacja przekierowuje dostęp do rejestru do węzła **HKEY_CURRENT_USER** (**HKCU**).

### <a name="syntax"></a>Składnia

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas Wartość TRUE wskazuje, że informacje rejestru są kierowane do węzła **HKCU** ; Wartość FALSE oznacza, że aplikacja zapisuje informacje rejestru w domyślnym węźle. Domyślnym węzłem jest **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda zakończy się pomyślnie, w przeciwnym razie kod błędu HRESULT w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Przekierowywanie rejestru nie jest domyślnie włączone. Po włączeniu tej opcji dostęp do rejestru zostanie przekierowany do **HKEY_CURRENT_USER \software\classes**.

Przekierowanie nie jest globalne. Przekierowanie rejestru ma wpływ tylko na platformy MFC i ATL.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="atlunregistertypelib"></a><a name="atlunregistertypelib"></a> AtlUnRegisterTypeLib

Ta funkcja jest wywoływana, aby wyrejestrować bibliotekę typów.

### <a name="syntax"></a>Składnia

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*hInstTypeLib*<br/>
Uchwyt do wystąpienia modułu.

*lpszIndex*<br/>
Ciąg w formacie " \\ \n", gdzie N jest indeksem liczbowym zasobu biblioteki typów. Może mieć wartość NULL, jeśli indeks nie jest wymagany.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywana przez [CAtlComModule:: UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) i [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="atlloadtypelib"></a><a name="atlloadtypelib"></a> AtlLoadTypeLib

Ta funkcja jest wywoływana, aby załadować bibliotekę typów.

### <a name="syntax"></a>Składnia

```
ATLINLINE ATLAPI AtlLoadTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex,
    BSTR* pbstrPath,
    ITypeLib** ppTypeLib);
```

### <a name="parameters"></a>Parametry

*hInstTypeLib*<br/>
Dojście do modułu skojarzonego z biblioteką typów.

*lpszIndex*<br/>
Ciąg w formacie " \\ \n", gdzie N jest indeksem liczbowym zasobu biblioteki typów. Może mieć wartość NULL, jeśli indeks nie jest wymagany.

*pbstrPath*<br/>
Po pomyślnym powrocie, zawiera pełną ścieżkę modułu skojarzonego z biblioteką typów.

*ppTypeLib*<br/>
Po pomyślnym powrocie, zawiera wskaźnik do wskaźnika do załadowanej biblioteki typów.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywana przez [AtlRegisterTypeLib](#atlregistertypelib) i [AtlUnRegisterTypeLib](#atlunregistertypelib).

## <a name="atlupdateregistryfromresourced"></a><a name="atlupdateregistryfromresourced"></a> AtlUpdateRegistryFromResourceD

Ta funkcja była przestarzała w Visual Studio 2013 i została usunięta w programie Visual Studio 2015.

```
<removed>
```

## <a name="registrydataexchange"></a><a name="registrydataexchange"></a> RegistryDataExchange

Ta funkcja jest wywoływana, aby odczytywać dane z lub zapisywać do rejestru systemowego.

### <a name="syntax"></a>Składnia

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>Parametry

*Zmiennoprzecinkow*<br/>
Wskaźnik do bieżącego obiektu.

*rdxOp*<br/>
Wartość wyliczenia wskazująca, która operacja powinna zostać wykonana. Zapoznaj się z tabelą w sekcji uwagi, aby uzyskać dozwolone wartości.

*pItem*<br/>
Wskaźnik na dane, które mają być odczytywane lub zapisywane w rejestrze. Dane mogą również reprezentować klucz, który ma zostać usunięty z rejestru. Wartość domyślna to NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Makra [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) i [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) rozszerzają się do funkcji, która wywołuje `RegistryDataExchange` .

Możliwe wartości wyliczenia wskazujące na działanie, które funkcja powinna wykonać, są przedstawione w poniższej tabeli:

|Wartość wyliczenia|Operacja|
|----------------|---------------|
|eReadFromReg|Odczytaj dane z rejestru.|
|eWriteToReg|Zapisz dane w rejestrze.|
|eDeleteFromReg|Usuń klucz z rejestru.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="see-also"></a>Zobacz też

[Funkcje](atl-functions.md)<br/>
[Makra wymiany danych rejestru](registry-data-exchange-macros.md)

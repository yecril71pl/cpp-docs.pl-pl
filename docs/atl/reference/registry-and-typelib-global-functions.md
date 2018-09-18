---
title: Funkcje globalne rejestru i elementu TypeLib | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0e4eba9940546e72f11c220dc03a6538750ae85
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028340"
---
# <a name="registry-and-typelib-global-functions"></a>Funkcje globalne rejestru i elementu TypeLib

Te funkcje zapewniają obsługę ładowania i rejestrowania biblioteki typów.

> [!IMPORTANT]
>  Funkcje wymienione w poniższych tabelach nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

|||
|-|-|
|[AfxRegCreateKey](#afxrefcreatekey)|Tworzy określony klucz rejestru.|
|[AfxRegDeleteKey](#afxrefdeletekey)|Usuwa określony klucz rejestru.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Element pomocniczy służący do rejestrowania procedury obsługi podglądu.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Pomocnik wyrejestrować obsługi wersji zapoznawczej. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Ta funkcja jest wywoływana, aby zarejestrować bibliotekę typów.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Ta funkcja jest wywoływana, aby wyrejestrować biblioteki typów|
|[AfxRegOpenKey](#afxregopenkey)|Otwiera określony klucz rejestru.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Otwiera określony klucz rejestru.|
|[AtlLoadTypeLib](#atlloadtypelib)|Ta funkcja jest wywoływana, aby załadować bibliotekę typów.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Ta funkcja jest wywoływana, aby zaktualizować rejestr z dostarczonego zasobu.|
|[RegistryDataExchange](#registrydataexchange)|Ta funkcja jest wywoływana, aby odczytywać dane z lub zapisywać do rejestru systemowego. Wywoływane przez [makra wymiany danych rejestru](../../atl/reference/registry-data-exchange-macros.md).|

Funkcje te kontrolują, który węzeł w rejestrze jest używana do przechowywania informacji.

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Pobiera czy aplikacja przekierowuje dostęp do rejestru **HKEY_CURRENT_USER** ( **HKCU**) węzła.|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Określa, czy aplikacja przekierowuje dostęp do rejestru **HKEY_CURRENT_USER** ( **HKCU**) węzła.|  

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="atlgetperuserregistration"></a> AtlGetPerUserRegistration

Ta funkcja służy do określenia, czy aplikacja przekierowuje dostęp do rejestru **HKEY_CURRENT_USER** (**HKCU**) węzła.

### <a name="syntax"></a>Składnia

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>Parametry

*pEnabled*<br/>
[out] Wartość TRUE wskazuje, że informacje rejestru zostanie skierowany do **HKCU** węzła; Wartość FALSE wskazuje, że aplikacja zapisze informacje rejestru do węzła domyślnego. Węzeł domyślny jest **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda zakończy się pomyślnie, w przeciwnym razie błąd HRESULT kodu w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Przekierowanie rejestru nie jest włączona domyślnie. Jeśli ta opcja jest włączona, dostęp do rejestru jest przekierowywane do **HKEY_CURRENT_USER\Software\Classes**.

Przekierowanie nie jest globalne. Dotyczy tylko struktury MFC i ATL przekierowanie rejestru.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h  

## <a name="afxregcreatekey"></a> AfxRegCreateKey

Tworzy określony klucz rejestru.

### <a name="syntax"></a>Składnia

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Dojście można otworzyć klucza rejestru.

*lpSubKey*<br/>
Nazwa klucza, ta funkcja zostanie otwarty lub tworzy.

*phkResult*<br/>
Wskaźnik do zmiennej, która odbiera dojścia do klucza otwarte lub utworzone.

*pTM*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli funkcja zawiedzie, wartość zwracana jest kod błędu różny od zera określonych w pliku Winerror.h.  

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxpriv.h  

## <a name="afxregdeletekey"></a> AfxRegDeleteKey

Usuwa określony klucz rejestru.

### <a name="syntax"></a>Składnia

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Dojście można otworzyć klucza rejestru.

*lpSubKey*<br/>
Nazwa klucza do usunięcia.

*pTM*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli funkcja zawiedzie, wartość zwracana jest kod błędu różny od zera określonych w pliku Winerror.h.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxpriv.h  

## <a name="afxregisterpreviewhandler"></a>

Element pomocniczy służący do rejestrowania procedury obsługi podglądu.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>Parametry

*lpszCLSID*<br/>
Określa identyfikator CLSID programu obsługi.

*lpszShortTypeName*<br/>
Określa identyfikator ProgID programu obsługi.

*lpszFilterExt*<br/>
Określa rozszerzenie pliku zarejestrowane przy użyciu tej procedury obsługi.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h   

##  <a name="atlregistertypelib"></a>  AtlRegisterTypeLib

Ta funkcja jest wywoływana, aby zarejestrować bibliotekę typów.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*hInstTypeLib*<br/>
Dojście do wystąpienia modułu.

*lpszIndex*<br/>
Ciąg w formacie "\\\N", gdzie N to liczba całkowita indeks zasób biblioteki typów. Może mieć wartość NULL, jeśli brak indeksu jest wymagana.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywany przez [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) i [CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="afxregopenkey"></a> AfxRegOpenKey

Otwiera określony klucz rejestru.

### <a name="syntax"></a>Składnia

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Dojście można otworzyć klucza rejestru.

*lpSubKey*<br/>
Nazwa klucza, ta funkcja zostanie otwarty lub tworzy.

*phkResult*<br/>
Wskaźnik do zmiennej, która odbiera dojścia do utworzony klucz.

*pTM*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli funkcja zawiedzie, wartość zwracana jest kod błędu różny od zera określonych w pliku Winerror.h.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxpriv.h  

## <a name="afxregopenkeyex"></a>  AfxRegOpenKeyEx

Otwiera określony klucz rejestru. 

### <a name="syntax"></a>Składnia

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Dojście można otworzyć klucza rejestru.

*lpSubKey*<br/>
Nazwa klucza, ta funkcja zostanie otwarty lub tworzy.

*ulOptions*<br/>
Ten parametr jest zarezerwowana i musi mieć wartość zero.

*samDesired*<br/>
Maska, która określa prawa żądanego dostępu do klucza.

*phkResult*<br/>
Wskaźnik do zmiennej, która odbiera dojście otwartego klucza.

*pTM*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli funkcja zawiedzie, wartość zwracana jest kod błędu różny od zera określonych w pliku Winerror.h.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxpriv.h  

## <a name="afxunregisterpreviewhandler"></a> AfxUnregisterPreviewHandler

Pomocnik wyrejestrować obsługi wersji zapoznawczej.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>Parametry

*lpszCLSID*<br/>
Określa identyfikator CLSID programu obsługi, który ma być wyrejestrowany.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h  

## <a name="atlsetperuserregistration"></a> AtlSetPerUserRegistration

Określa, czy aplikacja przekierowuje dostęp do rejestru **HKEY_CURRENT_USER** (**HKCU**) węzła.

### <a name="syntax"></a>Składnia

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość TRUE wskazuje, że informacje rejestru zostanie skierowany do **HKCU** węzła; Wartość FALSE wskazuje, że aplikacja zapisze informacje rejestru do węzła domyślnego. Węzeł domyślny jest **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli metoda zakończy się pomyślnie, w przeciwnym razie błąd HRESULT kodu w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Przekierowanie rejestru nie jest włączona domyślnie. Jeśli ta opcja jest włączona, dostęp do rejestru jest przekierowywane do **HKEY_CURRENT_USER\Software\Classes**.

Przekierowanie nie jest globalne. Dotyczy tylko struktury MFC i ATL przekierowanie rejestru.  

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h  

##  <a name="atlunregistertypelib"></a>  AtlUnRegisterTypeLib

Ta funkcja jest wywoływana, aby wyrejestrować bibliotekę typów.

### <a name="syntax"></a>Składnia

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib, 
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*hInstTypeLib*<br/>
Dojście do wystąpienia modułu.

*lpszIndex*<br/>
Ciąg w formacie "\\\N", gdzie N to liczba całkowita indeks zasób biblioteki typów. Może mieć wartość NULL, jeśli brak indeksu jest wymagana.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywany przez [CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) i [AtlComModuleUnregisterServer](#atlcommoduleunregisterserver).  

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="atlloadtypelib"></a>  AtlLoadTypeLib

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
Obsługa modułu powiązane z biblioteką typów.

*lpszIndex*<br/>
Ciąg w formacie "\\\N", gdzie N to liczba całkowita indeks zasób biblioteki typów. Może mieć wartość NULL, jeśli brak indeksu jest wymagana.

*pbstrPath*<br/>
Przy powrocie z pomyślnym zawiera pełną ścieżkę moduł, który został skojarzony z biblioteki typów.

*ppTypeLib*<br/>
Przy powrocie z pomyślnym zawiera wskaźnik do wskaźnika do biblioteki typów załadowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywany przez [AtlRegisterTypeLib](#atlregistertypelib) i [AtlUnRegisterTypeLib](#atlunregistertypelib).

##  <a name="atlupdateregistryfromresourced"></a>  AtlUpdateRegistryFromResourceD

Ta funkcja została zakończona w programie Visual Studio 2013 i został usunięty w programie Visual Studio 2015.

```
<removed>
```

##  <a name="registrydataexchange"></a>  RegistryDataExchange

Ta funkcja jest wywoływana, aby odczytywać dane z lub zapisywać do rejestru systemowego.  

### <a name="syntax"></a>Składnia

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>Parametry

*(CZAS PACYFICZNY)*<br/>
Wskaźnik do bieżącego obiektu.

*rdxOp*<br/>
Wartość wyliczenia, która wskazuje, które operacji funkcji, należy wykonać. Zobacz tabelę w sekcji uwag do dozwolonych wartości.

*pItem*<br/>
Wskaźnik do danych, który ma być odczytywany lub zapisywane w rejestrze. Dane można również oznaczyć klucz do usunięcia z rejestru. Wartością domyślną jest NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Makra [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) i [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) rozwiń funkcję, która wywołuje `RegistryDataExchange`.

Wartości wyliczenia możliwych, wskazujący, że należy wykonywać operacji funkcji są wyświetlane w poniższej tabeli:

|Wartość wyliczenia|Operacja|
|----------------|---------------|
|eReadFromReg|Odczytywanie danych z rejestru.|
|eWriteToReg|Wpisywanie danych do rejestru.|
|eDeleteFromReg|Usuń klucz z rejestru.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="see-also"></a>Zobacz też

[Funkcje](atl-functions.md)<br/>
[Makra wymiany danych rejestru](registry-data-exchange-macros.md)

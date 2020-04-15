---
title: Funkcje globalne rejestru i typuLib
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
ms.openlocfilehash: 69df927ddd04c19d10703854aa8c8948894309d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326077"
---
# <a name="registry-and-typelib-global-functions"></a>Funkcje globalne rejestru i typuLib

Te funkcje zapewniają obsługę ładowania i rejestrowania biblioteki typów.

> [!IMPORTANT]
> Funkcji wymienionych w poniższych tabelach nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

|||
|-|-|
|[AfxRegCreateKey (Klucz)](#afxregcreatekey)|Tworzy określony klucz rejestru.|
|[AfxRegDeleteKey (Klucz)](#afxregdeletekey)|Usuwa określony klucz rejestru.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Pomocnik do zarejestrowania programu obsługi wersji zapoznawczej.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Pomocnik do wyrejestrowania programu obsługi podglądu. |
|[AtlRegisterTypeLib (Rejestracja Typów)](#atlregistertypelib)|Ta funkcja jest wywoływana, aby zarejestrować bibliotekę typów.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Ta funkcja jest wywoływana w celu wyrejestrowania biblioteki typów|
|[AfxRegOpenKey (Klucz AfxRegOpenKey)](#afxregopenkey)|Otwiera określony klucz rejestru.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Otwiera określony klucz rejestru.|
|[AtlLoadTypeLib (AtlLoadTypeLib)](#atlloadtypelib)|Ta funkcja jest wywoływana, aby załadować bibliotekę typów.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Ta funkcja jest wywoływana, aby zaktualizować rejestr z dostarczonego zasobu.|
|[Rejestracja danych rejestru](#registrydataexchange)|Ta funkcja jest wywoływana, aby odczytywać dane z lub zapisywać do rejestru systemowego. Wywoływane przez [makra wymiany danych rejestru](../../atl/reference/registry-data-exchange-macros.md).|

Te funkcje określają, który węzeł w rejestrze program używa do przechowywania informacji.

|||
|-|-|
|[Rejestracja AtlGetPerUser](#atlgetperuserregistration)|Pobiera, czy aplikacja przekierowuje dostęp rejestru do **węzła HKEY_CURRENT_USER** **(HKCU).**|
|[Rejestracja AtlSetPerUserRegistration](#atlsetperuserregistration)|Określa, czy aplikacja przekierowuje dostęp rejestru do węzła **HKEY_CURRENT_USER** **(HKCU).**|

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="atlgetperuserregistration"></a><a name="atlgetperuserregistration"></a>Rejestracja AtlGetPerUser

Ta funkcja służy do określania, czy aplikacja przekierowuje dostęp rejestru do węzła **HKEY_CURRENT_USER** **(HKCU).**

### <a name="syntax"></a>Składnia

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>Parametry

*pWęgosi*<br/>
[na zewnątrz] WARTOŚĆ TRUE wskazuje, że informacje rejestru są kierowane do węzła **HKCU;** FALSE wskazuje, że aplikacja zapisuje informacje rejestru do domyślnego węzła. Domyślnym węzłem jest **HKEY_CLASSES_ROOT** **(HKCR).**

### <a name="return-value"></a>Wartość zwracana

S_OK jeśli metoda zakończy się pomyślnie, w przeciwnym razie kod błędu HRESULT, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Przekierowanie rejestru nie jest domyślnie włączone. Jeśli ta opcja zostanie włączona, dostęp do rejestru zostanie przekierowany do **HKEY_CURRENT_USER\Software\Classes**.

Przekierowanie nie jest globalne. Tylko MFC i ATL struktury są dotknięte tym przekierowania rejestru.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="afxregcreatekey"></a><a name="afxregcreatekey"></a>AfxRegCreateKey (Klucz)

Tworzy określony klucz rejestru.

### <a name="syntax"></a>Składnia

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*klawiszy*<br/>
Dojście do otwartego klucza rejestru.

*lpSubKey*<br/>
Nazwa klucza, który ta funkcja otwiera lub tworzy.

*phkResult (wynik)*<br/>
Wskaźnik do zmiennej, która odbiera dojście do klucza otwartego lub utworzonego.

*Ptm*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w Winerror.h.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxpriv.h

## <a name="afxregdeletekey"></a><a name="afxregdeletekey"></a>AfxRegDeleteKey (Klucz)

Usuwa określony klucz rejestru.

### <a name="syntax"></a>Składnia

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*klawiszy*<br/>
Dojście do otwartego klucza rejestru.

*lpSubKey*<br/>
Nazwa klucza do usunięcia.

*Ptm*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w Winerror.h.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxpriv.h

## <a name="afxregisterpreviewhandler"></a>

Pomocnik do zarejestrowania programu obsługi wersji zapoznawczej.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>Parametry

*lpszCLSID*<br/>
Określa clsid programu obsługi.

*lpszShortTypeName*<br/>
Określa identyfikator progid programu obsługi.

*lpszFilterext*<br/>
Określa rozszerzenie pliku zarejestrowane w tym programie obsługi.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="atlregistertypelib"></a><a name="atlregistertypelib"></a>AtlRegisterTypeLib (Rejestracja Typów)

Ta funkcja jest wywoływana, aby zarejestrować bibliotekę typów.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Parametry

*hInstTypeLib*<br/>
Dojście do wystąpienia modułu.

*lpszIndex*<br/>
Ciąg w formacie\\"\N", gdzie N jest indeksem liczb całkowitych zasobu biblioteki typów. Może mieć wartość NULL, jeśli nie jest wymagany żaden indeks.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywana przez [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) i [CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="afxregopenkey"></a><a name="afxregopenkey"></a>AfxRegOpenKey (Klucz AfxRegOpenKey)

Otwiera określony klucz rejestru.

### <a name="syntax"></a>Składnia

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*klawiszy*<br/>
Dojście do otwartego klucza rejestru.

*lpSubKey*<br/>
Nazwa klucza, który ta funkcja otwiera lub tworzy.

*phkResult (wynik)*<br/>
Wskaźnik do zmiennej, która odbiera dojście do utworzonego klucza.

*Ptm*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w Winerror.h.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxpriv.h

## <a name="afxregopenkeyex"></a><a name="afxregopenkeyex"></a>AfxRegOpenKeyEx

Otwiera określony klucz rejestru.

### <a name="syntax"></a>Składnia

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*klawiszy*<br/>
Dojście do otwartego klucza rejestru.

*lpSubKey*<br/>
Nazwa klucza, który ta funkcja otwiera lub tworzy.

*UlOptions*<br/>
Ten parametr jest zarezerwowany i musi wynosić zero.

*samDesired (polski)*<br/>
Maska określająca żądane prawa dostępu do klucza.

*phkResult (wynik)*<br/>
Wskaźnik do zmiennej, która odbiera dojście do otwartego klucza.

*Ptm*<br/>
Wskaźnik do `CAtlTransactionManager` obiektu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w Winerror.h.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a><a name="afxunregisterpreviewhandler"></a>AfxUnregisterPreviewHandler

Pomocnik do wyrejestrowania programu obsługi podglądu.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>Parametry

*lpszCLSID*<br/>
Określa CLSID programu obsługi do wyrejestrowania.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="atlsetperuserregistration"></a><a name="atlsetperuserregistration"></a>Rejestracja AtlSetPerUserRegistration

Określa, czy aplikacja przekierowuje dostęp rejestru do węzła **HKEY_CURRENT_USER** **(HKCU).**

### <a name="syntax"></a>Składnia

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] WARTOŚĆ TRUE wskazuje, że informacje rejestru są kierowane do węzła **HKCU;** FALSE wskazuje, że aplikacja zapisuje informacje rejestru do domyślnego węzła. Domyślnym węzłem jest **HKEY_CLASSES_ROOT** **(HKCR).**

### <a name="return-value"></a>Wartość zwracana

S_OK jeśli metoda zakończy się pomyślnie, w przeciwnym razie kod błędu HRESULT, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Przekierowanie rejestru nie jest domyślnie włączone. Jeśli ta opcja zostanie włączona, dostęp do rejestru zostanie przekierowany do **HKEY_CURRENT_USER\Software\Classes**.

Przekierowanie nie jest globalne. Tylko MFC i ATL struktury są dotknięte tym przekierowania rejestru.

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="atlunregistertypelib"></a><a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib

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
Ciąg w formacie\\"\N", gdzie N jest indeksem liczb całkowitych zasobu biblioteki typów. Może mieć wartość NULL, jeśli nie jest wymagany żaden indeks.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywana przez [CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) i [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="atlloadtypelib"></a><a name="atlloadtypelib"></a>AtlLoadTypeLib (AtlLoadTypeLib)

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
Ciąg w formacie\\"\N", gdzie N jest indeksem liczb całkowitych zasobu biblioteki typów. Może mieć wartość NULL, jeśli nie jest wymagany żaden indeks.

*pbstrPath (pbstrPath)*<br/>
Po pomyślnym powrocie zawiera pełną ścieżkę modułu skojarzonego z biblioteką typów.

*ppTypeLib (Polski)*<br/>
Po pomyślnym powrocie zawiera wskaźnik do wskaźnika do załadowanej biblioteki typów.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywana przez [AtlRegisterTypeLib](#atlregistertypelib) i [AtlUnRegisterTypeLib](#atlunregistertypelib).

## <a name="atlupdateregistryfromresourced"></a><a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD

Ta funkcja została przestarzała w programie Visual Studio 2013 i jest usuwana w programie Visual Studio 2015.

```
<removed>
```

## <a name="registrydataexchange"></a><a name="registrydataexchange"></a>Rejestracja danych rejestru

Ta funkcja jest wywoływana, aby odczytywać dane z lub zapisywać do rejestru systemowego.

### <a name="syntax"></a>Składnia

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Wskaźnik do bieżącego obiektu.

*RdxOp ( rdxop )*<br/>
Wartość wyliczenia, która wskazuje, jaką operację powinna wykonać funkcja. Zobacz tabelę w sekcji Uwagi dla dozwolonych wartości.

*pItem (własówce)*<br/>
Wskaźnik do danych, które mają być odczytywane z rejestru lub zapisywane w nim. Dane mogą również reprezentować klucz do usunięcia z rejestru. Wartością domyślną jest NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Makra [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) i [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) rozszerzać się do funkcji, `RegistryDataExchange`która wywołuje .

Możliwe wartości wyliczenia wskazujące operację, którą funkcja powinna wykonać, są pokazane w poniższej tabeli:

|Wartość wyliczenia|Operacja|
|----------------|---------------|
|eReadFromReg|Odczytywanie danych z rejestru.|
|eWriteToReg|Zapisuj dane w rejestrze.|
|eDeleteFromReg|Usuń klucz z rejestru.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="see-also"></a>Zobacz też

[Funkcje](atl-functions.md)<br/>
[Makra wymiany danych rejestru](registry-data-exchange-macros.md)

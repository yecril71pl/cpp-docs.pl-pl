---
title: Globalne funkcje rejestru i biblioteki typów | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: cb0a89ecf8bb81e515703abe819bb1edfbf80d59
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365510"
---
# <a name="registry-and-typelib-global-functions"></a>Globalne funkcje rejestru i biblioteki typów
Funkcje te zapewniają obsługę ładowania i rejestrowania biblioteki typów.  
  
> [!IMPORTANT]
>  Funkcje wymienione w poniższych tabelach nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
|||  
|-|-|  
|[AfxRegCreateKey](#afxrefcreatekey)|Tworzy określony klucz rejestru.|
|[AfxRegDeleteKey](#afxrefdeletekey)|Usuwa określony klucz rejestru.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Pomocnik można zarejestrować obsługi podglądu.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Pomocnik wyrejestrować Obsługa podglądu. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Ta funkcja jest wywoływana, aby zarejestrować bibliotekę typów.|  
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Ta funkcja jest wywoływana można wyrejestrować biblioteki typów|  
|[AfxRegOpenKey](#afxregopenkey)|Otwiera określony klucz rejestru.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Otwiera określony klucz rejestru.|
|[AtlLoadTypeLib](#atlloadtypelib)|Ta funkcja jest wywoływana, aby załadować bibliotekę typów.|  
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Ta funkcja jest wywoływana, aby zaktualizować rejestr z dostarczonego zasobu.|  
|[RegistryDataExchange](#registrydataexchange)|Ta funkcja jest wywoływana, aby odczytywać dane z lub zapisywać do rejestru systemowego. Wywoływane przez [makra wymiany danych rejestru](../../atl/reference/registry-data-exchange-macros.md).|  
  
 Funkcje te kontrolują który węzeł będzie używana do przechowywania informacji rejestru.  
  
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
 [out] `pEnabled`  
 `TRUE` Wskazuje, że informacje rejestru jest kierowany do **HKCU** węzła; `FALSE` wskazuje, że aplikacja zapisuje informacje rejestru do domyślnego węzła. Domyślny węzeł jest **wpisów z HKEY_CLASSES_ROOT** (**HKCR**).  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda zakończy się pomyślnie, w przeciwnym razie `HRESULT` kodu błędu, jeśli wystąpi błąd.  
  
### <a name="remarks"></a>Uwagi  
 Przekierowanie rejestru nie jest domyślnie włączona. Jeśli ta opcja jest włączona, dostępu do rejestru jest przekierowywany do **HKEY_CURRENT_USER\Software\Classes**.  
  
 Przekierowanie nie jest globalnego. Dotyczy tylko struktury MFC i ATL przekierowanie rejestru.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  

 ## <a name="afxregcreatekey"></a> AfxRegCreateKey
 Tworzy określony klucz rejestru.  
  
### <a name="syntax"></a>Składnia  
  
```  
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `hKey`  
 Dojście można otworzyć klucza rejestru.  
  
 `lpSubKey`  
 Nazwa klucza, który otwiera tej funkcji, lub tworzy.  
  
 `phkResult`  
 Wskaźnik do zmiennej, która odbiera dojście do klucza otwarty lub utworzony.  
  
 `pTM`  
 Wskaźnik do `CAtlTransactionManager` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, wartość zwracana jest zdefiniowane w pliku Winerror.h kod błędu różną od zera.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpriv.h  

## <a name="afxregdeletekey"></a> AfxRegDeleteKey
Usuwa określony klucz rejestru.  
  
### <a name="syntax"></a>Składnia  
  
```  
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `hKey`  
 Dojście można otworzyć klucza rejestru.  
  
 `lpSubKey`  
 Nazwa klucza do usunięcia.  
  
 `pTM`  
 Wskaźnik do `CAtlTransactionManager` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, wartość zwracana jest zdefiniowane w pliku Winerror.h kod błędu różną od zera.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpriv.h  

## <a name="afxregisterpreviewhandler"></a>
Pomocnik można zarejestrować obsługi podglądu.  
  
### <a name="syntax"></a>Składnia  
  
```  
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);  
```  
  
### <a name="parameters"></a>Parametry  
 `lpszCLSID`  
 Określa identyfikator CLSID programu obsługi.  
  
 `lpszShortTypeName`  
 Określa identyfikator programu obsługi.  
  
 `lpszFilterExt`  
 Określa rozszerzenie pliku zarejestrowane z tym programem obsługi.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h   

##  <a name="atlregistertypelib"></a>  AtlRegisterTypeLib  
 Ta funkcja jest wywoływana, aby zarejestrować bibliotekę typów.  
  
  
```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `hInstTypeLib`  
 Dojście do wystąpienia modułu.  
  
 `lpszIndex`  
 Ciąg w formacie "\\\N", gdzie N to liczba całkowita indeks zasób biblioteki typów. Może mieć wartość NULL, jeśli indeks nie jest wymagane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
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
 `hKey`  
 Dojście można otworzyć klucza rejestru.  
  
 `lpSubKey`  
 Nazwa klucza, który otwiera tej funkcji, lub tworzy.  
  
 `phkResult`  
 Wskaźnik do zmiennej, która odbiera dojścia do utworzony klucz.  
  
 `pTM`  
 Wskaźnik do `CAtlTransactionManager` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, wartość zwracana jest zdefiniowane w pliku Winerror.h kod błędu różną od zera.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpriv.h  

## <a name="afxregopenkeyex"></a>  AfxRegOpenKeyEx
Otwiera określony klucz rejestru. 

### <a name="syntax"></a>Składnia  
  
```  
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `hKey`  
 Dojście można otworzyć klucza rejestru.  
  
 `lpSubKey`  
 Nazwa klucza, który otwiera tej funkcji, lub tworzy.  
  
 `ulOptions`  
 Ten parametr jest zarezerwowany i musi być równy zero.  
  
 `samDesired`  
 Maska, która określa prawa żądany dostęp do klucza.  
  
 `phkResult`  
 Wskaźnik do zmiennej, która odbiera dojścia do otwartego klucza.  
  
 `pTM`  
 Wskaźnik do `CAtlTransactionManager` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, wartość zwracana jest zdefiniowane w pliku Winerror.h kod błędu różną od zera.  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpriv.h  

 ## <a name="afxunregisterpreviewhandler"></a> AfxUnregisterPreviewHandler
 Pomocnik wyrejestrować Obsługa podglądu.  
  
### <a name="syntax"></a>Składnia  
  
```  
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);  
```  
  
### <a name="parameters"></a>Parametry  
 `lpszCLSID`  
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
 [in] `bEnable`  
 `TRUE` Wskazuje, że informacje rejestru jest kierowany do **HKCU** węzła; `FALSE` wskazuje, że aplikacja zapisuje informacje rejestru do domyślnego węzła. Domyślny węzeł jest **wpisów z HKEY_CLASSES_ROOT** (**HKCR**).  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda zakończy się pomyślnie, w przeciwnym razie `HRESULT` kodu błędu, jeśli wystąpi błąd.  
  
### <a name="remarks"></a>Uwagi  
 Przekierowanie rejestru nie jest domyślnie włączona. Jeśli ta opcja jest włączona, dostępu do rejestru jest przekierowywany do **HKEY_CURRENT_USER\Software\Classes**.  
  
 Przekierowanie nie jest globalnego. Dotyczy tylko struktury MFC i ATL przekierowanie rejestru.  
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
 `hInstTypeLib`  
 Dojście do wystąpienia modułu.  
  
 `lpszIndex`  
 Ciąg w formacie "\\\N", gdzie N to liczba całkowita indeks zasób biblioteki typów. Może mieć wartość NULL, jeśli indeks nie jest wymagane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
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
 `hInstTypeLib`  
 Dojście do modułu skojarzone z biblioteki typów.  
  
 `lpszIndex`  
 Ciąg w formacie "\\\N", gdzie N to liczba całkowita indeks zasób biblioteki typów. Może mieć wartość NULL, jeśli indeks nie jest wymagane.  
  
 *pbstrPath*  
 Przy powrocie pomyślne zawiera pełną ścieżkę modułu skojarzone z biblioteki typów.  
  
 `ppTypeLib`  
 Przy powrocie pomyślne zawiera wskaźnik na wskaźnik do biblioteki typów załadowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja pomocnika jest wykorzystywany przez [AtlRegisterTypeLib](#atlregistertypelib) i [AtlUnRegisterTypeLib](#atlunregistertypelib).  
  
##  <a name="atlupdateregistryfromresourced"></a>  AtlUpdateRegistryFromResourceD  
 Ta funkcja została uznana za przestarzałą w programie Visual Studio 2013 i zostanie usunięta w programie Visual Studio 2015.  
  
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
 *PT*  
 Wskaźnik do bieżącego obiektu.  
  
 *rdxOp*  
 Wartość wyliczenia wskazująca operacji, które należy wykonać funkcji. Znajdują się w sekcji uwag do dozwolonych wartości w tabeli.  
  
 `pItem`  
 Wskaźnik do danych, która ma być odczytywane lub zapisywane w rejestrze. Dane można również reprezentuje klucz do usunięcia z rejestru. Wartość domyślna to NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Makra [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) i [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) Rozwiń do funkcji, która wywołuje `RegistryDataExchange`.  
  
 Wartości wyliczenia możliwych, wskazujący, że należy wykonywać operacji funkcji zostały przedstawione w poniższej tabeli:  
  
|Wartość wyliczenia|Operacja|  
|----------------|---------------|  
|eReadFromReg|Odczytywanie danych z rejestru.|  
|eWriteToReg|Wpisywanie danych do rejestru.|  
|eDeleteFromReg|Usuń klucz z rejestru.|  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h

## <a name="see-also"></a>Zobacz też  
 [Funkcje](atl-functions.md) [makra wymiany danych rejestru](registry-data-exchange-macros.md)






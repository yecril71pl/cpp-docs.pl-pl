---
title: Klasa CAtlComModule
ms.date: 11/04/2016
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
ms.openlocfilehash: 270e6ca4dcb5c7701281cc2ac6c04e1d60093db3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499809"
---
# <a name="catlcommodule-class"></a>Klasa CAtlComModule

Ta klasa implementuje modułu serwera COM.

## <a name="syntax"></a>Składnia

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|Konstruktor.|
|[CAtlComModule:: ~ CAtlComModule](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|Wywołaj tę metodę, aby zaktualizować rejestr systemu dla każdego obiektu na mapie obiektu.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Wywołaj tę metodę, aby zarejestrować bibliotekę typów.|
|[CAtlComModule::UnregisterServer](#unregisterserver)|Wywołaj tę metodę, aby wyrejestrować każdy obiekt na mapie obiektu.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Wywołaj tę metodę, aby wyrejestrować biblioteki typów.|

## <a name="remarks"></a>Uwagi

`CAtlComModule` implementuje modułu serwera COM, umożliwiając klientowi dostęp do składników modułu.

Ta klasa zastępuje przestarzałe [CComModule](../../atl/reference/ccommodule-class.md) klasy stosowane we wcześniejszych wersjach ATL. Zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="catlcommodule"></a>  CAtlComModule::CAtlComModule

Konstruktor.

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje modułu.

##  <a name="dtor"></a>  CAtlComModule:: ~ CAtlComModule

Destruktor.

```
~CAtlComModule();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie fabryki klas.

##  <a name="registerserver"></a>  CAtlComModule::RegisterServer

Wywołaj tę metodę, aby zaktualizować rejestr systemu dla każdego obiektu na mapie obiektu.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
Wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowany. Wartość domyślna to FALSE.

*pCLSID*<br/>
Wskazuje identyfikator CLSID obiektu do zarejestrowania. Jeśli zostanie zarejestrowany o wartości NULL (wartość domyślna) wszystkie obiekty na mapie obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje funkcję globalnego [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).

##  <a name="registertypelib"></a>  CAtlComModule::RegisterTypeLib

Wywołaj tę metodę, aby zarejestrować bibliotekę typów.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Ciąg w formacie "\\\N", gdzie N to liczba całkowita indeksu zasobu biblioteki typów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Dodaje informacje o biblioteki typów do rejestru systemowego. Jeśli wystąpienie modułu zawiera wiele bibliotek typów, należy użyć pierwszej wersji tej metody, aby określić, biblioteki typów, które powinny być używane.

##  <a name="unregisterserver"></a>  CAtlComModule::UnregisterServer

Wywołaj tę metodę, aby wyrejestrować każdy obiekt na mapie obiektu.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
Wartość TRUE, jeśli można wyrejestrować biblioteki typów. Wartość domyślna to FALSE.

*pCLSID*<br/>
Wskazuje identyfikator CLSID obiektu do wyrejestrowania. Jeśli wartość NULL (wartość domyślna) wszystkie obiekty na mapie obiektu zostanie wyrejestrowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje funkcję globalnego [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

##  <a name="unregistertypelib"></a>  CAtlComModule::UnRegisterTypeLib

Wywołaj tę metodę, aby wyrejestrować biblioteki typów.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Ciąg w formacie "\\\N", gdzie N to liczba całkowita indeksu zasobu biblioteki typów.

### <a name="remarks"></a>Uwagi

Usuwa informacji na temat biblioteki typów z rejestru systemowego. Jeśli wystąpienie modułu zawiera wiele bibliotek typów, należy użyć pierwszej wersji tej metody, aby określić, biblioteki typów, które powinny być używane.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

## <a name="see-also"></a>Zobacz też

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)

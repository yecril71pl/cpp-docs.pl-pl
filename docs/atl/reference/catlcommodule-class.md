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
ms.openlocfilehash: 09adcb33ca9e6f8524063130d6aedca044d6ecb5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863215"
---
# <a name="catlcommodule-class"></a>Klasa CAtlComModule

Ta klasa implementuje moduł serwera COM.

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
|[CAtlComModule::RegisterServer](#registerserver)|Wywołaj tę metodę, aby zaktualizować rejestr systemu dla każdego obiektu na mapie obiektów.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Wywołaj tę metodę, aby zarejestrować bibliotekę typów.|
|[CAtlComModule::UnregisterServer](#unregisterserver)|Wywołaj tę metodę, aby wyrejestrować każdy obiekt na mapie obiektu.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Wywołaj tę metodę, aby wyrejestrować bibliotekę typów.|

## <a name="remarks"></a>Uwagi

`CAtlComModule` implementuje moduł serwera COM, umożliwiając klientowi dostęp do składników modułu.

Ta klasa zastępuje przestarzałą klasę [CComModule](../../atl/reference/ccommodule-class.md) używaną we wcześniejszych wersjach ATL. Zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="catlcommodule"></a>CAtlComModule::CAtlComModule

Konstruktor.

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje moduł.

##  <a name="dtor"></a>CAtlComModule:: ~ CAtlComModule

Destruktor.

```
~CAtlComModule();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie fabryki klas.

##  <a name="registerserver"></a>CAtlComModule::RegisterServer

Wywołaj tę metodę, aby zaktualizować rejestr systemu dla każdego obiektu na mapie obiektów.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
Ma wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowana. Wartość domyślna to FALSE.

*pCLSID*<br/>
Wskazuje identyfikator CLSID obiektu, który ma zostać zarejestrowany. W przypadku wartości NULL (wartość domyślna) wszystkie obiekty w mapie obiektów zostaną zarejestrowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje funkcję globalną [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).

##  <a name="registertypelib"></a>CAtlComModule::RegisterTypeLib

Wywołaj tę metodę, aby zarejestrować bibliotekę typów.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Ciąg w formacie "\\\N", gdzie N jest indeksem liczb całkowitych zasobu biblioteki typów.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Dodaje informacje o bibliotece typów do rejestru systemowego. Jeśli wystąpienie modułu zawiera wiele bibliotek typów, użyj pierwszej wersji tej metody, aby określić, która biblioteka typów powinna być używana.

##  <a name="unregisterserver"></a>CAtlComModule::UnregisterServer

Wywołaj tę metodę, aby wyrejestrować każdy obiekt na mapie obiektu.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
Ma wartość TRUE, jeśli biblioteka typów ma być wyrejestrowana. Wartość domyślna to FALSE.

*pCLSID*<br/>
Wskazuje identyfikator CLSID obiektu, który ma zostać wyrejestrowany. W przypadku wartości NULL (wartość domyślna) wszystkie obiekty w mapie obiektów zostaną wyrejestrowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołuje funkcję globalną [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

##  <a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib

Wywołaj tę metodę, aby wyrejestrować bibliotekę typów.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Ciąg w formacie "\\\N", gdzie N jest indeksem liczb całkowitych zasobu biblioteki typów.

### <a name="remarks"></a>Uwagi

Usuwa informacje o bibliotece typów z rejestru systemowego. Jeśli wystąpienie modułu zawiera wiele bibliotek typów, użyj pierwszej wersji tej metody, aby określić, która biblioteka typów powinna być używana.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="see-also"></a>Zobacz także

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)

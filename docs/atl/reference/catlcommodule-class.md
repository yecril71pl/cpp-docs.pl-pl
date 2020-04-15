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
ms.openlocfilehash: 68fdb48edc9304d9d74df6f36bd208cfd35ff307
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321481"
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
|[CAtlComModule::~CAtlComModule](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|Wywołanie tej metody, aby zaktualizować rejestr systemowy dla każdego obiektu na mapie obiektu.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Wywołanie tej metody, aby zarejestrować bibliotekę typów.|
|[CAtlComModule::Serwer wyrejestrowania](#unregisterserver)|Wywołanie tej metody, aby wyrejestrować każdy obiekt na mapie obiektu.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Wywołanie tej metody, aby wyrejestrować bibliotekę typów.|

## <a name="remarks"></a>Uwagi

`CAtlComModule`implementuje moduł serwera COM, umożliwiając klientowi dostęp do składników modułu.

Ta klasa zastępuje przestarzałe [CComModule](../../atl/reference/ccommodule-class.md) klasy używane we wcześniejszych wersjach ATL. Zobacz [klasy modułów ATL, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="catlcommodulecatlcommodule"></a><a name="catlcommodule"></a>CAtlComModule::CAtlComModule

Konstruktor.

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje moduł.

## <a name="catlcommodulecatlcommodule"></a><a name="dtor"></a>CAtlComModule::~CAtlComModule

Destruktor.

```
~CAtlComModule();
```

### <a name="remarks"></a>Uwagi

Uwalnia wszystkie fabryki klas.

## <a name="catlcommoduleregisterserver"></a><a name="registerserver"></a>CAtlComModule::RegisterServer

Wywołanie tej metody, aby zaktualizować rejestr systemowy dla każdego obiektu na mapie obiektu.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
PRAWDA, jeśli biblioteka typów ma być zarejestrowana. Wartością domyślną jest FAŁSZ.

*pCLSID (pCLSID)*<br/>
Wskazuje identyfikator CLSID obiektu, który ma zostać zarejestrowany. Jeśli wartość NULL (wartość domyślna), wszystkie obiekty na mapie obiektu zostaną zarejestrowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje funkcję globalną [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).

## <a name="catlcommoduleregistertypelib"></a><a name="registertypelib"></a>CAtlComModule::RegisterTypeLib

Wywołanie tej metody, aby zarejestrować bibliotekę typów.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Ciąg w formacie\\"\N", gdzie N jest indeksem liczb całkowitych zasobu TYPELIB.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Dodaje informacje o bibliotece typów do rejestru systemowego. Jeśli wystąpienie modułu zawiera wiele bibliotek typów, użyj pierwszej wersji tej metody, aby określić, która biblioteka typów powinna być używana.

## <a name="catlcommoduleunregisterserver"></a><a name="unregisterserver"></a>CAtlComModule::Serwer wyrejestrowania

Wywołanie tej metody, aby wyrejestrować każdy obiekt na mapie obiektu.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
PRAWDA, jeśli biblioteka typów ma być wyrejestrowana. Wartością domyślną jest FAŁSZ.

*pCLSID (pCLSID)*<br/>
Wskazuje identyfikator CLSID obiektu, który ma być wyrejestrowany. Jeśli wartość NULL (wartość domyślna), wszystkie obiekty na mapie obiektu zostaną wyrejestrowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje globalną funkcję [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

## <a name="catlcommoduleunregistertypelib"></a><a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib

Wywołanie tej metody, aby wyrejestrować bibliotekę typów.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
Ciąg w formacie\\"\N", gdzie N jest indeksem liczb całkowitych zasobu TYPELIB.

### <a name="remarks"></a>Uwagi

Usuwa informacje o bibliotece typów z rejestru systemowego. Jeśli wystąpienie modułu zawiera wiele bibliotek typów, użyj pierwszej wersji tej metody, aby określić, która biblioteka typów powinna być używana.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="see-also"></a>Zobacz też

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)

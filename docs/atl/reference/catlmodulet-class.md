---
title: Klasa CAtlModuleT
ms.date: 11/04/2016
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
helpviewer_keywords:
- CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
ms.openlocfilehash: 0d7673d634bad2d20dae63e4293f12e5530c4acd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534904"
---
# <a name="catlmodulet-class"></a>Klasa CAtlModuleT

Ta klasa implementuje modułu ATL.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa jest pochodną `CAtlModuleT`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|Inicjuje element danych zawierający identyfikator GUID bieżącego modułu.|
|[CAtlModuleT::RegisterAppId](#registerappid)|Dodaje plik EXE w rejestrze.|
|[CAtlModuleT::RegisterServer](#registerserver)|Dodaje usługę do rejestru.|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Usuwa plik EXE z rejestru.|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Usługa usuwa z rejestru.|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Aktualizuje informacje o pliku EXE w rejestrze.|

## <a name="remarks"></a>Uwagi

`CAtlModuleT`, pochodzące z [CAtlModule](../../atl/reference/catlmodule-class.md), implementuje plik wykonywalny (EXE) lub modułu ATL usługa (EXE). Modułowi wykonywalnemu jest serwerem lokalnym, poza procesem, moduł usługi jest aplikacji Windows, która działa w tle podczas uruchamiania Windows.

`CAtlModuleT` zapewnia obsługę inicjowania, rejestrowanie i wyrejestrowywanie modułu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="catlmodulet"></a>  CAtlModuleT::CAtlModuleT

Konstruktor.

```
CAtlModuleT() throw();
```

### <a name="remarks"></a>Uwagi

Wywołania [CAtlModuleT::InitLibId](#initlibid).

##  <a name="initlibid"></a>  CAtlModuleT::InitLibId

Inicjuje element danych zawierający identyfikator GUID bieżącego modułu.

```
static void InitLibId() throw();
```

### <a name="remarks"></a>Uwagi

Wywoływane przez konstruktora [CAtlModuleT::CAtlModuleT](#catlmodulet).

##  <a name="registerappid"></a>  CAtlModuleT::RegisterAppId

Dodaje plik EXE w rejestrze.

```
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="registerserver"></a>  CAtlModuleT::RegisterServer

Dodaje usługę do rejestru.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
Wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowany. Wartość domyślna to FALSE.

*pCLSID*<br/>
Wskazuje identyfikator CLSID obiektu do zarejestrowania. Jeśli zostanie zarejestrowany o wartości NULL (wartość domyślna) wszystkie obiekty na mapie obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="unregisterappid"></a>  CAtlModuleT::UnregisterAppId

Usuwa plik EXE z rejestru.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="unregisterserver"></a>  CAtlModuleT::UnregisterServer

Usługa usuwa z rejestru.

```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
Wartość TRUE, jeśli biblioteka typów jest również zostać wyrejestrowana.

*pCLSID*<br/>
Wskazuje identyfikator CLSID obiektu do wyrejestrowania. Jeśli wartość NULL (wartość domyślna) wszystkie obiekty na mapie obiektu zostanie wyrejestrowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="updateregistryappid"></a>  CAtlModuleT::UpdateRegistryAppId

Aktualizuje informacje o pliku EXE w rejestrze.

```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Parametry

*bRegister*<br/>
Zastrzeżone.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlModule](../../atl/reference/catlmodule-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)

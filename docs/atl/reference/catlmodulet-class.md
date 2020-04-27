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
ms.openlocfilehash: b07e60265570e66337a2d13007e9ad57c6f369e4
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167867"
---
# <a name="catlmodulet-class"></a>Klasa CAtlModuleT

Ta klasa implementuje moduł ATL.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa pochodna `CAtlModuleT`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|Inicjuje element członkowski danych zawierający identyfikator GUID bieżącego modułu.|
|[CAtlModuleT::RegisterAppId](#registerappid)|Dodaje plik EXE do rejestru.|
|[CAtlModuleT::RegisterServer](#registerserver)|Dodaje usługę do rejestru.|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Usuwa plik EXE z rejestru.|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Usuwa usługę z rejestru.|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Aktualizuje informacje o pliku EXE w rejestrze.|

## <a name="remarks"></a>Uwagi

`CAtlModuleT`pochodny from [CAtlModule](../../atl/reference/catlmodule-class.md)implementuje moduł plików wykonywalnych (exe) lub usług (exe) ATL. Moduł wykonywalny jest lokalnym serwerem poza procesem, natomiast moduł usługi jest aplikacją systemu Windows, która jest uruchamiana w tle podczas uruchamiania systemu Windows.

`CAtlModuleT`zapewnia obsługę inicjowania, rejestrowania i wyrejestrowywania modułu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>CAtlModuleT::CAtlModuleT

Konstruktor.

```cpp
CAtlModuleT() throw();
```

### <a name="remarks"></a>Uwagi

Wywołuje [CAtlModuleT:: InitLibId](#initlibid).

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a>CAtlModuleT::InitLibId

Inicjuje element członkowski danych zawierający identyfikator GUID bieżącego modułu.

```cpp
static void InitLibId() throw();
```

### <a name="remarks"></a>Uwagi

Wywoływane przez konstruktora [CAtlModuleT:: CAtlModuleT](#catlmodulet).

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a>CAtlModuleT::RegisterAppId

Dodaje plik EXE do rejestru.

```cpp
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a>CAtlModuleT::RegisterServer

Dodaje usługę do rejestru.

```cpp
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
Ma wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowana. Wartość domyślna to FALSE.

*pCLSID*<br/>
Wskazuje identyfikator CLSID obiektu, który ma zostać zarejestrowany. W przypadku wartości NULL (wartość domyślna) wszystkie obiekty w mapie obiektów zostaną zarejestrowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlModuleT::UnregisterAppId

Usuwa plik EXE z rejestru.

```cpp
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a>CAtlModuleT::UnregisterServer

Usuwa usługę z rejestru.

```cpp
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
Ma wartość TRUE, jeśli biblioteka typów jest również wyrejestrowana.

*pCLSID*<br/>
Wskazuje identyfikator CLSID obiektu, który ma zostać wyrejestrowany. W przypadku wartości NULL (wartość domyślna) wszystkie obiekty w mapie obiektów zostaną wyrejestrowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId

Aktualizuje informacje o pliku EXE w rejestrze.

```cpp
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Parametry

*bRegister*<br/>
Zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="see-also"></a>Zobacz także

[Klasa CAtlModule](../../atl/reference/catlmodule-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)

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
ms.openlocfilehash: bf64c073249b7426fafb430a708573d9d06d11fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321411"
---
# <a name="catlmodulet-class"></a>Klasa CAtlModuleT

Ta klasa implementuje moduł ATL.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa pochodzi `CAtlModuleT`od .

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|Inicjuje element członkowski danych zawierający identyfikator GUID bieżącego modułu.|
|[CAtlModuleT::RegisterAppId](#registerappid)|Dodaje EXE do rejestru.|
|[CAtlModuleT::RegisterServer](#registerserver)|Dodaje usługę do rejestru.|
|[CAtlModuleT:: UnregisterAppId](#unregisterappid)|Usuwa EXE z rejestru.|
|[CAtlModuleT::Wyrejestrowanie serwera](#unregisterserver)|Usuwa usługę z rejestru.|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Aktualizuje informacje EXE w rejestrze.|

## <a name="remarks"></a>Uwagi

`CAtlModuleT`, pochodzące z [CAtlModule](../../atl/reference/catlmodule-class.md), implementuje wykonywalny (EXE) lub service (EXE) moduł ATL. Moduł wykonywalny to lokalny serwer poza procesem, podczas gdy moduł usługi jest aplikacją systemu Windows działającą w tle podczas uruchamiania systemu Windows.

`CAtlModuleT`zapewnia obsługę inicjowania, rejestrowania i wyrejestrowania modułu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Catlmodule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>CAtlModuleT::CAtlModuleT

Konstruktor.

```
CAtlModuleT() throw();
```

### <a name="remarks"></a>Uwagi

Wywołuje [CAtlModuleT::InitLibId](#initlibid).

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a>CAtlModuleT::InitLibId

Inicjuje element członkowski danych zawierający identyfikator GUID bieżącego modułu.

```
static void InitLibId() throw();
```

### <a name="remarks"></a>Uwagi

Wywoływany przez [konstruktora CAtlModuleT::CAtlModuleT](#catlmodulet).

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a>CAtlModuleT::RegisterAppId

Dodaje EXE do rejestru.

```
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a>CAtlModuleT::RegisterServer

Dodaje usługę do rejestru.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
PRAWDA, jeśli biblioteka typów ma być zarejestrowana. Wartością domyślną jest FAŁSZ.

*pCLSID (pCLSID)*<br/>
Wskazuje identyfikator CLSID obiektu, który ma zostać zarejestrowany. Jeśli wartość NULL (wartość domyślna), wszystkie obiekty na mapie obiektu zostaną zarejestrowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlModuleT:: UnregisterAppId

Usuwa EXE z rejestru.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a>CAtlModuleT::Wyrejestrowanie serwera

Usuwa usługę z rejestru.

```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
PRAWDA, jeśli biblioteka typów ma być również wyrejestrowana.

*pCLSID (pCLSID)*<br/>
Wskazuje identyfikator CLSID obiektu, który ma być wyrejestrowany. Jeśli wartość NULL (wartość domyślna), wszystkie obiekty na mapie obiektu zostaną wyrejestrowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId

Aktualizuje informacje EXE w rejestrze.

```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Parametry

*Bregister*<br/>
Zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlModule](../../atl/reference/catlmodule-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)

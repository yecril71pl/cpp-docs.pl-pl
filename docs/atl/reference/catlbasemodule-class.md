---
title: Klasa CAtlBaseModule
ms.date: 11/04/2016
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
helpviewer_keywords:
- CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
ms.openlocfilehash: a55412eff18fd04ac4e41c0f001991c1cf725b9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321507"
---
# <a name="catlbasemodule-class"></a>Klasa CAtlBaseModule

Ta klasa jest tworzone w każdym projekcie ATL.

## <a name="syntax"></a>Składnia

```
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Dodaje wystąpienie zasobu do listy przechowywanych uchwytów.|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Zwraca dojście do określonego wystąpienia zasobu.|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Zwraca wystąpienie modułu `CAtlBaseModule` z obiektu.|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Zwraca wystąpienie zasobu `CAtlBaseModule` z obiektu.|
|[CAtlBaseModule::UsuńInstrykcję źródła](#removeresourceinstance)|Usuwa wystąpienie zasobu z listy przechowywanych uchwytów.|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Ustawia wystąpienie zasobu `CAtlBaseModule` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|Zmienna wskazująca, czy inicjowanie modułu nie powiodło się.|

## <a name="remarks"></a>Uwagi

Wystąpienie `CAtlBaseModule` o nazwie _AtlBaseModule jest obecny w każdym projekcie ATL, zawierający dojście do wystąpienia modułu, dojście do modułu zawierającego zasoby (które domyślnie są jednym i tym samym) oraz tablicę dojścia do modułów zapewniających zasoby podstawowe. `CAtlBaseModule`można bezpiecznie uzyskać dostęp z wielu wątków.

Ta klasa zastępuje przestarzałe [CComModule](../../atl/reference/ccommodule-class.md) klasy używane we wcześniejszych wersjach ATL.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance

Dodaje wystąpienie zasobu do listy przechowywanych uchwytów.

```
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst (WZT)*<br/>
Wystąpienie zasobu do dodania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli zasób został pomyślnie dodany, false w przeciwnym razie.

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule

Konstruktor.

```
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Uwagi

Tworzy `CAtlBaseModule`plik .

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt

Zwraca dojście do określonego wystąpienia zasobu.

```
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Parametry

*I*<br/>
Numer wystąpienia zasobu.

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście do wystąpienia zasobu lub NULL, jeśli nie istnieje żadne odpowiednie wystąpienie zasobu.

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance

Zwraca wystąpienie modułu `CAtlBaseModule` z obiektu.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wystąpienie modułu.

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance

Zwraca wystąpienie zasobu.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wystąpienie zasobu.

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>CAtlBaseModule::m_bInitFailed

Zmienna wskazująca, czy inicjowanie modułu nie powiodło się.

```
static bool m_bInitFailed;
```

### <a name="remarks"></a>Uwagi

Wartość true, jeśli moduł zainicjowany, false, jeśli nie można zainicjować.

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>CAtlBaseModule::UsuńInstrykcję źródła

Usuwa wystąpienie zasobu z listy przechowywanych uchwytów.

```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst (WZT)*<br/>
Wystąpienie zasobu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli zasób został pomyślnie usunięty, false w przeciwnym razie.

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>CAtlBaseModule::SetResourceInstance

Ustawia wystąpienie zasobu `CAtlBaseModule` obiektu.

```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst (WZT)*<br/>
Nowe wystąpienie zasobu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowane wystąpienie zasobu.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)

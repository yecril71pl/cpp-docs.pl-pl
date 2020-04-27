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
ms.openlocfilehash: d57d6e631cb287496a4ff5516e97e65ec0152e30
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168296"
---
# <a name="catlbasemodule-class"></a>Klasa CAtlBaseModule

Ta klasa jest tworzona w każdym projekcie ATL.

## <a name="syntax"></a>Składnia

```cpp
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
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Dodaje wystąpienie zasobu do listy przechowywanych dojść.|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Zwraca dojście do określonego wystąpienia zasobu.|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Zwraca wystąpienie modułu z `CAtlBaseModule` obiektu.|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Zwraca wystąpienie zasobu z `CAtlBaseModule` obiektu.|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Usuwa wystąpienie zasobu z listy przechowywanych dojść.|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Ustawia wystąpienie zasobu `CAtlBaseModule` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlBaseModule:: m_bInitFailed](#m_binitfailed)|Zmienna, która wskazuje, czy inicjowanie modułu nie powiodło się.|

## <a name="remarks"></a>Uwagi

Wystąpienie o `CAtlBaseModule` nazwie _AtlBaseModule jest obecne w każdym projekcie ATL, zawierającym dojście do wystąpienia modułu, dojście do modułu zawierającego zasoby (które domyślnie są takie same) i tablicą dojść do modułów udostępniających zasoby podstawowe. `CAtlBaseModule`można bezpiecznie uzyskać dostęp z wielu wątków.

Ta klasa zastępuje przestarzałą klasę [CComModule](../../atl/reference/ccommodule-class.md) używaną we wcześniejszych wersjach ATL.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore. h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance

Dodaje wystąpienie zasobu do listy przechowywanych dojść.

```cpp
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Wystąpienie zasobu do dodania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli zasób został pomyślnie dodany, w przeciwnym razie false.

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule

Konstruktor.

```cpp
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Uwagi

Tworzy `CAtlBaseModule`.

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt

Zwraca dojście do określonego wystąpienia zasobu.

```cpp
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Parametry

*Mam*<br/>
Liczba wystąpień zasobów.

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście do wystąpienia zasobu lub wartość NULL, jeśli nie istnieje odpowiednie wystąpienie zasobu.

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance

Zwraca wystąpienie modułu z `CAtlBaseModule` obiektu.

```cpp
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wystąpienie modułu.

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance

Zwraca wystąpienie zasobu.

```cpp
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wystąpienie zasobu.

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>CAtlBaseModule:: m_bInitFailed

Zmienna, która wskazuje, czy inicjowanie modułu nie powiodło się.

```cpp
static bool m_bInitFailed;
```

### <a name="remarks"></a>Uwagi

Ma wartość true, jeśli moduł został zainicjowany, wartość false, jeśli nie można jej zainicjować.

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>CAtlBaseModule::RemoveResourceInstance

Usuwa wystąpienie zasobu z listy przechowywanych dojść.

```cpp
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Wystąpienie zasobu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli zasób został pomyślnie usunięty, w przeciwnym razie false.

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>CAtlBaseModule::SetResourceInstance

Ustawia wystąpienie zasobu `CAtlBaseModule` obiektu.

```cpp
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Nowe wystąpienie zasobu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowane wystąpienie zasobu.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)

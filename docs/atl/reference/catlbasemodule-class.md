---
title: CAtlBaseModule Class
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
ms.openlocfilehash: d382d1fe7d50a2fdeefc9b477625580792de7d6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247155"
---
# <a name="catlbasemodule-class"></a>CAtlBaseModule Class

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
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Dodaje wystąpienie zasobu do listy przechowywanych uchwyty.|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Zwraca uchwyt do wystąpienia określonego zasobu.|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Zwraca wystąpienie modułu z `CAtlBaseModule` obiektu.|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Zwraca wystąpienie zasobu z `CAtlBaseModule` obiektu.|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Usuwa wystąpienia zasobu z listy przechowywanych uchwyty.|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Ustawia wystąpienia zasobu `CAtlBaseModule` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|Zmienna, która wskazuje, czy wystąpiło niepowodzenie inicjowania modułu.|

## <a name="remarks"></a>Uwagi

Wystąpienie `CAtlBaseModule` nazwane _AtlBaseModule znajduje się w każdy Projekt ATL, zawierający dojścia do wystąpienia modułu, dojścia do modułu zawierającego zasoby, (które domyślnie są takie same), a tablica dojść do modułów, podając podstawowe zasoby. `CAtlBaseModule` bezpiecznie możliwy z wielu wątków.

Ta klasa zastępuje przestarzałe [CComModule](../../atl/reference/ccommodule-class.md) klasy stosowane we wcześniejszych wersjach ATL.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

##  <a name="addresourceinstance"></a>  CAtlBaseModule::AddResourceInstance

Dodaje wystąpienie zasobu do listy przechowywanych uchwyty.

```
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Wystąpienie zasobu do dodania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli zasób został pomyślnie dodany, wartość false w przeciwnym razie.

##  <a name="catlbasemodule"></a>  CAtlBaseModule::CAtlBaseModule

Konstruktor.

```
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Uwagi

Tworzy `CAtlBaseModule`.

##  <a name="gethinstanceat"></a>  CAtlBaseModule::GetHInstanceAt

Zwraca uchwyt do wystąpienia określonego zasobu.

```
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Parametry

*i*<br/>
Liczba wystąpień zasobu.

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt wystąpienia zasobu lub wartość NULL, jeśli nie ma odpowiednich wystąpień zasobu.

##  <a name="getmoduleinstance"></a>  CAtlBaseModule::GetModuleInstance

Zwraca wystąpienie modułu z `CAtlBaseModule` obiektu.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wystąpienie modułu.

##  <a name="getresourceinstance"></a>  CAtlBaseModule::GetResourceInstance

Zwraca wystąpienie zasobu.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wystąpienie zasobu.

##  <a name="m_binitfailed"></a>  CAtlBaseModule::m_bInitFailed

Zmienna, która wskazuje, czy wystąpiło niepowodzenie inicjowania modułu.

```
static bool m_bInitFailed;
```

### <a name="remarks"></a>Uwagi

Wartość true, jeśli moduł zainicjowany, wartość false, jeśli nie można zainicjować.

##  <a name="removeresourceinstance"></a>  CAtlBaseModule::RemoveResourceInstance

Usuwa wystąpienia zasobu z listy przechowywanych uchwyty.

```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Wystąpienie zasobu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli zasób został pomyślnie usunięty, wartość false w przeciwnym razie.

##  <a name="setresourceinstance"></a>  CAtlBaseModule::SetResourceInstance

Ustawia wystąpienia zasobu `CAtlBaseModule` obiektu.

```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parametry

*hInst*<br/>
Nowe wystąpienie zasobu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wystąpienie zaktualizowanego zasobu.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)

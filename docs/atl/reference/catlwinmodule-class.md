---
title: Klasa CAtlWinModule
ms.date: 11/04/2016
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
ms.openlocfilehash: 5cdf13ebbb982ad8184a52dcf1a3e30d71e4e5b0
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167711"
---
# <a name="catlwinmodule-class"></a>Klasa CAtlWinModule

Ta klasa zapewnia obsługę składników okienek ATL.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|Konstruktor.|
|[CAtlWinModule:: ~ CAtlWinModule](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Dodaje obiekt danych.|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Zwraca wskaźnik do obiektu danych modułu okna.|

## <a name="remarks"></a>Uwagi

Ta klasa zapewnia obsługę wszystkich klas ATL, które wymagają funkcji okna.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

Ta metoda inicjuje i dodaje `_AtlCreateWndData` strukturę.

```cpp
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Wskaźnik na `_AtlCreateWndData` strukturę, która ma zostać zainicjowana i dodana do bieżącego modułu.

*pObject*<br/>
Wskaźnik do **tego** wskaźnika obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) , która inicjuje strukturę [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) . Ta struktura będzie przechowywać **ten** wskaźnik, używany do uzyskania wystąpienia klasy w procedurach okna.

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

Konstruktor.

```cpp
CAtlWinModule();
```

### <a name="remarks"></a>Uwagi

Jeśli inicjalizacja nie powiedzie się, zostanie zgłoszony wyjątek **EXCEPTION_NONCONTINUABLE** .

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a>CAtlWinModule:: ~ CAtlWinModule

Destruktor.

```cpp
~CAtlWinModule();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby.

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

Ta metoda zwraca wskaźnik do `_AtlCreateWndData` struktury.

```cpp
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do struktury, `_AtlCreateWndData` która została wcześniej dodana z [CAtlWinModule:: AddCreateWndData](#addcreatewnddata)lub null, jeśli żaden obiekt nie jest dostępny.

## <a name="see-also"></a>Zobacz także

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)

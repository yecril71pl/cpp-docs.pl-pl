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
ms.openlocfilehash: 40385fd592563837546b483bb80978cde6a56555
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321271"
---
# <a name="catlwinmodule-class"></a>Klasa CAtlWinModule

Ta klasa zapewnia obsługę składników okien ATL.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|Konstruktor.|
|[CAtlWinModule::~CAtlWinModule](#dtor)|Destruktor.|

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

**Nagłówek:** atlbase.h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

Ta metoda inicjuje `_AtlCreateWndData` i dodaje strukturę.

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parametry

*Pdata*<br/>
Wskaźnik do `_AtlCreateWndData` struktury, która ma zostać zainicjowana i dodana do bieżącego modułu.

*Pobject*<br/>
Wskaźnik do obiektu jest **ten** wskaźnik.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [AtlWinModuleAddCreateWndData,](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) który inicjuje strukturę [_AtlCreateWndData.](../../atl/reference/atlcreatewnddata-structure.md) Ta struktura będzie przechowywać **ten** wskaźnik, używany do uzyskania wystąpienia klasy w procedurach okna.

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

Konstruktor.

```
CAtlWinModule();
```

### <a name="remarks"></a>Uwagi

Jeśli inicjowanie nie powiedzie się, wywoływany jest **wyjątek EXCEPTION_NONCONTINUABLE.**

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a>CAtlWinModule::~CAtlWinModule

Destruktor.

```
~CAtlWinModule();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

Ta metoda zwraca wskaźnik `_AtlCreateWndData` do struktury.

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `_AtlCreateWndData` struktury wcześniej dodanej za pomocą [CAtlWinModule::AddCreateWndData](#addcreatewnddata)lub NULL, jeśli żaden obiekt nie jest dostępny.

## <a name="see-also"></a>Zobacz też

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)

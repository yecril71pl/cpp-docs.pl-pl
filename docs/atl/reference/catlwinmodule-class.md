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
ms.openlocfilehash: d0bc98fa48f84e67ab38106dea3fe22d5ad1757d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857354"
---
# <a name="catlwinmodule-class"></a>Klasa CAtlWinModule

Ta klasa zapewnia obsługę składników okienek ATL.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
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

##  <a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

Ta metoda inicjuje i dodaje strukturę `_AtlCreateWndData`.

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Wskaźnik do struktury `_AtlCreateWndData`, który ma zostać zainicjowany i dodany do bieżącego modułu.

*pObject*<br/>
Wskaźnik do **tego** wskaźnika obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) , która inicjuje strukturę [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) . Ta struktura będzie przechowywać **ten** wskaźnik, używany do uzyskania wystąpienia klasy w procedurach okna.

##  <a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

Konstruktor.

```
CAtlWinModule();
```

### <a name="remarks"></a>Uwagi

Jeśli inicjalizacja nie powiedzie się, zostanie zgłoszony wyjątek **EXCEPTION_NONCONTINUABLE** .

##  <a name="dtor"></a>CAtlWinModule:: ~ CAtlWinModule

Destruktor.

```
~CAtlWinModule();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby.

##  <a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

Ta metoda zwraca wskaźnik do struktury `_AtlCreateWndData`.

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do struktury `_AtlCreateWndData`, która została wcześniej dodana z [CAtlWinModule:: AddCreateWndData](#addcreatewnddata)lub null, jeśli żaden obiekt nie jest dostępny.

## <a name="see-also"></a>Zobacz także

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)

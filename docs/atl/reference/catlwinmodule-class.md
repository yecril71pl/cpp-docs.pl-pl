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
ms.openlocfilehash: 3e38aebf3eadceafad3e70463d5bcf2d26fef96e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561632"
---
# <a name="catlwinmodule-class"></a>Klasa CAtlWinModule

Ta klasa zapewnia obsługę składników obsługi okien ATL.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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

Ta klasa dostarcza obsługi dla wszystkich klas ATL, które wymagają funkcji obsługi okien.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="addcreatewnddata"></a>  CAtlWinModule::AddCreateWndData

Ta metoda inicjuje i dodaje `_AtlCreateWndData` struktury.

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Wskaźnik do `_AtlCreateWndData` struktury, inicjowanie i dodawane do bieżącego modułu.

*Obiekt*<br/>
Wskaźnik do obiektu **to** wskaźnika.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) które inicjuje [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury. Ta struktura będzie przechowywać **to** wskaźnika, używany do uzyskania wystąpienie klasy w procedury okna.

##  <a name="catlwinmodule"></a>  CAtlWinModule::CAtlWinModule

Konstruktor.

```
CAtlWinModule();
```

### <a name="remarks"></a>Uwagi

Jeśli inicjowanie zakończy się niepowodzeniem, **EXCEPTION_NONCONTINUABLE** zgłaszany jest wyjątek.

##  <a name="dtor"></a>  CAtlWinModule:: ~ CAtlWinModule

Destruktor.

```
~CAtlWinModule();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

##  <a name="extractcreatewnddata"></a>  CAtlWinModule::ExtractCreateWndData

Ta metoda zwraca wskaźnik do `_AtlCreateWndData` struktury.

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `_AtlCreateWndData` struktury, wcześniej dodany z [CAtlWinModule::AddCreateWndData](#addcreatewnddata), lub wartość NULL, jeśli żaden obiekt nie jest dostępna.

## <a name="see-also"></a>Zobacz też

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)

---
title: Funkcje globalne w trybie WinModule
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 3d7d001a2835514cc5385a7069c0bcda58cdd88e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329358"
---
# <a name="winmodule-global-functions"></a>Funkcje globalne w trybie WinModule

Te funkcje `_AtlCreateWndData` zapewniają obsługę operacji struktury.

> [!IMPORTANT]
> Funkcji wymienionych w poniższej tabeli nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Ta funkcja służy do inicjowania i dodawania `_AtlCreateWndData` struktury.|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Wywołanie tej funkcji, `_AtlCreateWndData` aby wyodrębnić istniejącą strukturę.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreateWndData

Ta funkcja służy do inicjowania i dodawania `_AtlCreateWndData` struktury.

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>Parametry

*pWinModule*<br/>
Wskaźnik do struktury [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) modułu.

*Pdata*<br/>
Wskaźnik do [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury, która ma zostać zainicjowana i dodana do bieżącego modułu.

*Pobject*<br/>
Wskaźnik do obiektu jest **ten** wskaźnik.

### <a name="remarks"></a>Uwagi

Inicjuje `_AtlCreateWndData` strukturę, która jest używana do przechowywania **tego** wskaźnika używanego do odwoływania się do `_ATL_WIN_MODULE70` wystąpień klasy i dodaje ją do listy, do której odwołuje się struktura modułu. Wywoływany przez [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData

Wywołanie tej funkcji, `_AtlCreateWndData` aby wyodrębnić istniejącą strukturę.

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>Parametry

*pWinModule*<br/>
Wskaźnik do struktury [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) modułu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do struktury [_AtlCreateWndData.](../../atl/reference/atlcreatewnddata-structure.md)

### <a name="remarks"></a>Uwagi

Ta funkcja wyodrębni `_AtlCreateWndData` istniejącą strukturę z listy, `_ATL_WIN_MODULE70` do których odwołuje się struktura modułu.

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)

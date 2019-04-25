---
title: WinModule Global Functions
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 0e7450ea2a42c0b35dc5a6d1b77dfb0f2acb9520
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196862"
---
# <a name="winmodule-global-functions"></a>WinModule Global Functions

Te funkcje zapewniają obsługę `_AtlCreateWndData` struktury operacji.

> [!IMPORTANT]
> Funkcje wymienione w poniższej tabeli nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Ta funkcja jest używana do inicjowania i dodawania `_AtlCreateWndData` struktury.|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Wywołaj tę funkcję, aby wyodrębnić istniejącą `_AtlCreateWndData` struktury.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="atlwinmoduleaddcreatewnddata"></a>  AtlWinModuleAddCreateWndData

Ta funkcja jest używana do inicjowania i dodawania `_AtlCreateWndData` struktury.

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>Parametry

*pWinModule*<br/>
Wskaźnik do modułu [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) struktury.

*pData*<br/>
Wskaźnik do [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury, inicjowanie i dodawane do bieżącego modułu.

*pObject*<br/>
Wskaźnik do obiektu **to** wskaźnika.

### <a name="remarks"></a>Uwagi

Inicjuje `_AtlCreateWndData` struktury, która jest używana do przechowywania **to** wskaźnik umożliwia odwoływanie się do wystąpienia klasy i dodaje go do listy odwołuje się moduł `_ATL_WIN_MODULE70` struktury. Wywoływane przez [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).

##  <a name="atlwinmoduleextractcreatewnddata"></a>  AtlWinModuleExtractCreateWndData

Wywołaj tę funkcję, aby wyodrębnić istniejącą `_AtlCreateWndData` struktury.

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>Parametry

*pWinModule*<br/>
Wskaźnik do modułu [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) struktury.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) struktury.

### <a name="remarks"></a>Uwagi

Ta funkcja będzie wyodrębnić istniejącą `_AtlCreateWndData` struktury z listy odwołuje się moduł `_ATL_WIN_MODULE70` struktury.

## <a name="see-also"></a>Zobacz także

[Funkcje](../../atl/reference/atl-functions.md)

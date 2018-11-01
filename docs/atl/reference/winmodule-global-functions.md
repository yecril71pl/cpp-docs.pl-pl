---
title: Globalne elementu Winmodule
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 7c46f4da53bcf1e8a64cc6baad9ca748d1edb310
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578324"
---
# <a name="winmodule-global-functions"></a>Globalne elementu Winmodule

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

*Obiekt*<br/>
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

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)

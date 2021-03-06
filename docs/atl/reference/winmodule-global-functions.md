---
title: WinModule funkcje globalne
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 1f1dcb325f8844a74b3dd831a51050083e7ea552
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834404"
---
# <a name="winmodule-global-functions"></a>WinModule funkcje globalne

Te funkcje zapewniają obsługę `_AtlCreateWndData` operacji struktury.

> [!IMPORTANT]
> Funkcje wymienione w poniższej tabeli nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

|Nazwa|Opis|
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Ta funkcja służy do inicjowania i dodawania `_AtlCreateWndData` struktury.|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Wywołaj tę funkcję, aby wyodrębnić istniejącą `_AtlCreateWndData` strukturę.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a> AtlWinModuleAddCreateWndData

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

*pData*<br/>
Wskaźnik do struktury [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) , który ma zostać zainicjowany i dodany do bieżącego modułu.

*pObject*<br/>
Wskaźnik na **`this`** wskaźnik obiektu.

### <a name="remarks"></a>Uwagi

Inicjuje `_AtlCreateWndData` strukturę, która jest używana do przechowywania **`this`** wskaźnika używanego do odwoływania się do wystąpień klasy i dodaje go do listy, do której odwołuje się `_ATL_WIN_MODULE70` Struktura modułu. Wywoływane przez [CAtlWinModule:: AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a> AtlWinModuleExtractCreateWndData

Wywołaj tę funkcję, aby wyodrębnić istniejącą `_AtlCreateWndData` strukturę.

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>Parametry

*pWinModule*<br/>
Wskaźnik do struktury [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) modułu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do struktury [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) .

### <a name="remarks"></a>Uwagi

Ta funkcja spowoduje wyodrębnienie istniejącej `_AtlCreateWndData` struktury z listy przywoływanej przez strukturę modułu `_ATL_WIN_MODULE70` .

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)

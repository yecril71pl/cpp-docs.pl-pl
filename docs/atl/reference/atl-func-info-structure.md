---
title: Struktura _ATL_FUNC_INFO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5f3b759591333a41c3bc9da083e8e724249d13d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="atlfuncinfo-structure"></a>Struktura _ATL_FUNC_INFO
Zawiera informacje o typie opisuje metody lub właściwości w elemencie dispinterface.  
  
## <a name="syntax"></a>Składnia  
  
```
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```  
  
## <a name="members"></a>Elementy członkowskie  
 **cc**  
 Konwencja wywoływania. Korzystając z tej struktury z [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) klasy, ten element członkowski musi być **CC_STDCALL**. `CC_CDECL` jest to jedyna opcja obsługiwana w systemie Windows CE dla `CALLCONV` pole `_ATL_FUNC_INFO` struktury. Wszelkie inne wartości są nieobsługiwane w związku z tym niezdefiniowane zachowanie.  
  
 **vtReturn**  
 Typ wariantu funkcji zwracają wartość.  
  
 **nParams**  
 Liczba parametrów funkcji.  
  
 **pVarTypes**  
 Tablica typów variant parametrów funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Wewnętrznie ATL używa tej struktury do przechowywania informacji uzyskanych z biblioteki typów. Konieczne może być bezpośrednio manipulowania tej struktury, podając informacje o typie dla programu obsługi zdarzeń używane z [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) klasy i [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) makra.  
  
## <a name="example"></a>Przykład  
 Podana metoda dispinterface w pliku IDL:  
  
 [!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]  
  
 należy zdefiniować `_ATL_FUNC_INFO` struktury:  
  
 [!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury](../../atl/reference/atl-structures.md)   
 [Klasa IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)






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
ms.openlocfilehash: 8852deacfd36ba988b9b31bdad363c05aee12b6e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882211"
---
# <a name="atlfuncinfo-structure"></a>Struktura _ATL_FUNC_INFO
Zawiera informacje o typie opisuje metody lub właściwości na dispinterface.  
  
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
 `cc`  
 Konwencja wywoływania. Korzystając z tej struktury z [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) klasy, ten element członkowski musi być CC_STDCALL. `CC_CDECL` jest to jedyna opcja obsługiwana w Windows CE dla `CALLCONV` pole `_ATL_FUNC_INFO` struktury. Dowolna inna wartość nie jest obsługiwany związku z tym jego zachowanie jest niezdefiniowane.  
  
 `vtReturn`  
 Typ wariantu funkcji zwraca wartość.  
  
 `nParams`  
 Liczba parametrów funkcji.  
  
 `pVarTypes`  
 Tablica typu variant typy parametrów funkcji.  
  
## <a name="remarks"></a>Uwagi  
 ATL używa wewnętrznie, ta struktura do przechowywania informacji uzyskanych z biblioteki typów. Może być konieczne do manipulowania tej struktury bezpośrednio, jeśli podasz informacje o typie dla programu obsługi zdarzeń używane z [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) klasy i [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) makra.  
  
## <a name="example"></a>Przykład  
 Podana metoda dispinterface zdefiniowana w pliku IDL:  
  
 [!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]  
  
 należy zdefiniować `_ATL_FUNC_INFO` strukturę:  
  
 [!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: atlcom.h  
  
## <a name="see-also"></a>Zobacz też  
  [Klasy i struktury](../../atl/reference/atl-classes.md)  
 [Klasa IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)






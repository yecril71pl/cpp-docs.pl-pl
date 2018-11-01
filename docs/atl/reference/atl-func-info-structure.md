---
title: Struktura _ATL_FUNC_INFO
ms.date: 11/04/2016
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
ms.openlocfilehash: 8398bc999e9a62d03990fd1b205ad438b6428431
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554027"
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

`cc`<br/>
Konwencja wywoływania. Korzystając z tej struktury z [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) klasy, ten element członkowski musi być CC_STDCALL. `CC_CDECL` jest to jedyna opcja obsługiwana w Windows CE dla `CALLCONV` pole `_ATL_FUNC_INFO` struktury. Dowolna inna wartość nie jest obsługiwany związku z tym jego zachowanie jest niezdefiniowane.

`vtReturn`<br/>
Typ wariantu funkcji zwraca wartość.

`nParams`<br/>
Liczba parametrów funkcji.

`pVarTypes`<br/>
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

[Klasy i struktury](../../atl/reference/atl-classes.md)<br/>
[Klasa IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)


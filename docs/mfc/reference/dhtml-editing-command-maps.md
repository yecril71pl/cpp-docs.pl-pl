---
title: Mapy poleceń edycji DHTML
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: 62b388eb178be018655ea2b2be00d7321da50335
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365821"
---
# <a name="dhtml-editing-command-maps"></a>Mapy poleceń edycji DHTML

Następujące makra mogą być używane do mapowania poleceń edycji DHTML w klasach pochodnych [CHtmlEditView.](../../mfc/reference/chtmleditview-class.md) Aby uzyskać przykład ich użycia, zobacz [HTMLEdytuj przykład](../../overview/visual-cpp-samples.md).

### <a name="dhtml-editing-command-map-macros"></a>Makra mapy poleceń edycji DHTML

|||
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Deklaruje mapę poleceń edycji DHTML w klasie.|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Rozpoczyna definicję mapy poleceń edycji DHTML w klasie.|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Oznacza koniec mapy poleceń edycji DHTML.|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Mapuje identyfikator polecenia na polecenie edycji HTML.|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Mapuje identyfikator polecenia na polecenie edycji HTML i program obsługi wiadomości.|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Mapuje identyfikator polecenia na polecenie edycji HTML i element interfejsu użytkownika.|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Mapuje identyfikator polecenia na polecenie edycji HTML, program obsługi wiadomości i element interfejsu użytkownika.|

## <a name="declare_dhtmlediting_cmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a>DECLARE_DHTMLEDITING_CMDMAP

Deklaruje mapę poleceń edycji DHTML w klasie.

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Nazwa klasy.

### <a name="remarks"></a>Uwagi

To makro ma być używane w definicji [klas chtmlEditView](../../mfc/reference/chtmleditview-class.md)pochodnych.

Użyj [BEGIN_DHTMLEDITING_CMDMAP,](#begin_dhtmlediting_cmdmap) aby zaimplementować mapę.

### <a name="example"></a>Przykład

Zobacz [HTMLEdytuj przykład](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

## <a name="begin_dhtmlediting_cmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a>BEGIN_DHTMLEDITING_CMDMAP

Rozpoczyna definicję mapy poleceń edycji DHTML w klasie.

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Nazwa klasy zawierającej mapę poleceń edycji DHTML. Ta klasa powinna pochodzić bezpośrednio lub pośrednio z [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) i zawierać [makro DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) w jego definicji klasy.

### <a name="remarks"></a>Uwagi

Dodaj mapę poleceń edycji DHTML do klasy, aby mapować polecenia interfejsu użytkownika do poleceń edycji HTML.

Umieść makro BEGIN_DHTMLEDITING_CMDMAP w pliku implementacji klasy (.cpp), a następnie [DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) makra dla poleceń, które klasa ma mapować (na przykład od ID_EDIT_CUT do IDM_CUT). Użyj [makra END_DHTMLEDITING_CMDMAP,](#end_dhtmlediting_cmdmap) aby oznaczyć koniec mapy zdarzeń.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

## <a name="end_dhtmlediting_cmdmap"></a><a name="end_dhtmlediting_cmdmap"></a>END_DHTMLEDITING_CMDMAP

Oznacza koniec mapy poleceń edycji DHTML.

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>Uwagi

Używaj w połączeniu z [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).

### <a name="example"></a>Przykład

Zobacz [HTMLEdytuj przykład](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

## <a name="dhtmlediting_cmd_entry"></a><a name="dhtmlediting_cmd_entry"></a>DHTMLEDITING_CMD_ENTRY

Mapuje identyfikator polecenia na polecenie edycji HTML.

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>Parametry

*identyfikator cmdID*<br/>
Identyfikator polecenia (na przykład ID_EDIT_COPY).

*dhtmlcmdID (dhtmlcmdID)*<br/>
Polecenie edycji HTML, do którego *jest mapą cmdID* (na przykład IDM_COPY).

### <a name="example"></a>Przykład

Zobacz [HTMLEdytuj przykład](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

## <a name="dhtmlediting_cmd_entry_func"></a><a name="dhtmlediting_cmd_entry_func"></a>DHTMLEDITING_CMD_ENTRY_FUNC

Mapuje identyfikator polecenia na polecenie edycji HTML i program obsługi wiadomości.

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>Parametry

*identyfikator cmdID*<br/>
Identyfikator polecenia (na przykład ID_EDIT_COPY).

*dhtmlcmdID (dhtmlcmdID)*<br/>
Polecenie edycji HTML, do którego *jest mapą cmdID* (na przykład IDM_COPY).

*member_func_name*<br/>
Nazwa funkcji obsługi wiadomości, do której jest mapowane polecenie.

### <a name="example"></a>Przykład

Zobacz [HTMLEdytuj przykład](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

## <a name="dhtmlediting_cmd_entry_type"></a><a name="dhtmlediting_cmd_entry_type"></a>DHTMLEDITING_CMD_ENTRY_TYPE

Mapuje identyfikator polecenia na polecenie edycji HTML i element interfejsu użytkownika.

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>Parametry

*identyfikator cmdID*<br/>
Identyfikator polecenia (na przykład ID_EDIT_COPY).

*dhtmlcmdID (dhtmlcmdID)*<br/>
Polecenie edycji HTML, do którego *jest mapą cmdID* (na przykład IDM_COPY).

*elemType (elemType)*<br/>
Typ elementu interfejsu użytkownika; jednego z AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX lub AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Przykład

Zobacz [HTMLEdytuj przykład](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

## <a name="dhtmlediting_cmd_entry_func_type"></a><a name="dhtmlediting_cmd_entry_func_type"></a>DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

Mapuje identyfikator polecenia na polecenie edycji HTML, program obsługi wiadomości i element interfejsu użytkownika.

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>Parametry

*identyfikator cmdID*<br/>
Identyfikator polecenia (na przykład ID_EDIT_COPY).

*dhtmlcmdID (dhtmlcmdID)*<br/>
Polecenie edycji HTML, do którego *jest mapą cmdID* (na przykład IDM_COPY).

*member_func_name*<br/>
Nazwa funkcji obsługi wiadomości, do której jest mapowane polecenie.

*elemType (elemType)*<br/>
Typ elementu interfejsu użytkownika; jednego z AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX lub AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Przykład

Zobacz [HTMLEdytuj przykład](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)

---
title: Mapy poleceń edycji DHTML
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: f4bbfb500e8de9594bbaa334b4e227caeaa845da
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837414"
---
# <a name="dhtml-editing-command-maps"></a>Mapy poleceń edycji DHTML

Poniższe makra mogą służyć do mapowania poleceń edycji DHTML w klasach pochodnych [CHtmlEditView](../../mfc/reference/chtmleditview-class.md). Aby zapoznać się z przykładem ich użycia, zobacz [przykład HtmlEdit](../../overview/visual-cpp-samples.md).

### <a name="dhtml-editing-command-map-macros"></a>Makra mapy poleceń edycji DHTML

|Nazwa|Opis|
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Deklaruje mapę poleceń edycji w formacie DHTML w klasie.|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Uruchamia definicję mapy poleceń edycji w formacie DHTML w klasie.|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Oznacza koniec mapy poleceń edycji w formacie DHTML.|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Mapuje identyfikator polecenia na polecenie HTML Editing.|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Mapuje identyfikator polecenia na polecenie edycji HTML i procedurę obsługi komunikatów.|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Mapuje identyfikator polecenia na polecenie HTML Editing i element interfejsu użytkownika.|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Mapuje identyfikator polecenia na polecenie HTML Editing, procedurę obsługi komunikatów i element interfejsu użytkownika.|

## <a name="declare_dhtmlediting_cmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a> DECLARE_DHTMLEDITING_CMDMAP

Deklaruje mapę poleceń edycji w formacie DHTML w klasie.

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parametry

*Nazwą*<br/>
Nazwa klasy.

### <a name="remarks"></a>Uwagi

To makro jest używane w definicji klas pochodnych [CHtmlEditView](../../mfc/reference/chtmleditview-class.md).

Użyj [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) , aby zaimplementować mapę.

### <a name="example"></a>Przykład

Zobacz [przykład HtmlEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml. h

## <a name="begin_dhtmlediting_cmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a> BEGIN_DHTMLEDITING_CMDMAP

Uruchamia definicję mapy poleceń edycji w formacie DHTML w klasie.

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parametry

*Nazwą*<br/>
Nazwa klasy zawierającej mapę poleceń edytowania DHTML. Ta klasa powinna dziedziczyć bezpośrednio lub pośrednio z [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) i zawierać makro [DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) w ramach definicji klasy.

### <a name="remarks"></a>Uwagi

Dodaj mapę poleceń edycji w formacie DHTML do klasy, aby zamapować polecenia interfejsu użytkownika na polecenia edycji HTML.

Umieść makro BEGIN_DHTMLEDITING_CMDMAP w pliku implementacji klasy (CPP), a następnie [DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) makra dla poleceń, które Klasa ma mapować (na przykład z ID_EDIT_CUT do IDM_CUT). Użyj makra [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) , aby oznaczyć koniec mapy zdarzeń.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml. h

## <a name="end_dhtmlediting_cmdmap"></a><a name="end_dhtmlediting_cmdmap"></a> END_DHTMLEDITING_CMDMAP

Oznacza koniec mapy poleceń edycji w formacie DHTML.

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>Uwagi

Użyj w połączeniu z [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).

### <a name="example"></a>Przykład

Zobacz [przykład HtmlEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml. h

## <a name="dhtmlediting_cmd_entry"></a><a name="dhtmlediting_cmd_entry"></a> DHTMLEDITING_CMD_ENTRY

Mapuje identyfikator polecenia na polecenie HTML Editing.

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia (na przykład ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Polecenie HTML Editing, do którego *cmdID* Maps (na przykład IDM_COPY).

### <a name="example"></a>Przykład

Zobacz [przykład HtmlEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml. h

## <a name="dhtmlediting_cmd_entry_func"></a><a name="dhtmlediting_cmd_entry_func"></a> DHTMLEDITING_CMD_ENTRY_FUNC

Mapuje identyfikator polecenia na polecenie edycji HTML i procedurę obsługi komunikatów.

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia (na przykład ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Polecenie HTML Editing, do którego *cmdID* Maps (na przykład IDM_COPY).

*member_func_name*<br/>
Nazwa funkcji obsługi komunikatów, do której zostało zamapowane polecenie.

### <a name="example"></a>Przykład

Zobacz [przykład HtmlEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml. h

## <a name="dhtmlediting_cmd_entry_type"></a><a name="dhtmlediting_cmd_entry_type"></a> DHTMLEDITING_CMD_ENTRY_TYPE

Mapuje identyfikator polecenia na polecenie HTML Editing i element interfejsu użytkownika.

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia (na przykład ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Polecenie HTML Editing, do którego *cmdID* Maps (na przykład IDM_COPY).

*elemType*<br/>
Typ elementu interfejsu użytkownika; jeden z AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX lub AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Przykład

Zobacz [przykład HtmlEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml. h

## <a name="dhtmlediting_cmd_entry_func_type"></a><a name="dhtmlediting_cmd_entry_func_type"></a> DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

Mapuje identyfikator polecenia na polecenie HTML Editing, procedurę obsługi komunikatów i element interfejsu użytkownika.

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia (na przykład ID_EDIT_COPY).

*dhtmlcmdID*<br/>
Polecenie HTML Editing, do którego *cmdID* Maps (na przykład IDM_COPY).

*member_func_name*<br/>
Nazwa funkcji obsługi komunikatów, do której zostało zamapowane polecenie.

*elemType*<br/>
Typ elementu interfejsu użytkownika; jeden z AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX lub AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Przykład

Zobacz [przykład HtmlEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)

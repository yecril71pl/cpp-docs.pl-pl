---
title: Mapy poleceń edycji DHTML
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: 7f420619983283c225ca8fca23c5ea349def1d1b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776157"
---
# <a name="dhtml-editing-command-maps"></a>Mapy poleceń edycji DHTML

Następujące makra może służyć do mapy poleceń edycji DHTML [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-klas pochodnych. Na przykład ich użycie zobacz [przykładowe HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="dhtml-editing-command-map-macros"></a>Makra mapy poleceń edycji DHTML

|||
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|Deklaruje DHTML mapy poleceń edycji w klasie.|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|Uruchamia definicji DHTML mapy poleceń edycji w obrębie klasy.|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|Oznacza koniec mapy poleceń edycji DHTML.|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|Polecenie edytowania HTML mapuje identyfikator polecenia.|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|Mapuje identyfikator polecenia dla polecenia edycji HTML i obsługi wiadomości.|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|Mapuje identyfikator polecenia dla polecenia edycji HTML i elementu interfejsu użytkownika.|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|Mapuje identyfikator polecenia do edytowania polecenia, program obsługi komunikatów i elementu interfejsu użytkownika HTML.|

##  <a name="declare_dhtmlediting_cmdmap"></a>  DECLARE_DHTMLEDITING_CMDMAP

Deklaruje DHTML mapy poleceń edycji w klasie.

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parametry

*className*<br/>
Nazwa klasy.

### <a name="remarks"></a>Uwagi

To makro, które ma być używane w definicji [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-klas pochodnych.

Użyj [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) do zaimplementowania mapy.

### <a name="example"></a>Przykład

Zobacz [przykładowe HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

##  <a name="begin_dhtmlediting_cmdmap"></a>  BEGIN_DHTMLEDITING_CMDMAP

Uruchamia definicji DHTML mapy poleceń edycji w obrębie klasy.

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>Parametry

*className*<br/>
Nazwa klasy zawierającej mapy poleceń edycji DHTML. Ta klasa powinna pochodzić bezpośrednio lub pośrednio od [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) i obejmują [DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) makra w ramach swojej definicji klasy.

### <a name="remarks"></a>Uwagi

Mapy poleceń edycji DHTML należy dodać do swojej klasy do mapowania poleceń interfejsu użytkownika HTML polecenia edycji.

BEGIN_DHTMLEDITING_CMDMAP — makro należy umieścić w pliku implementacji (.cpp) klasy następuje [DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) makra dla poleceń, klasa jest do mapowania (np. z id_edit_cut — aby IDM_CUT). Użyj [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) makra, aby zaznaczyć koniec Mapa zdarzeń.

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

##  <a name="end_dhtmlediting_cmdmap"></a>  END_DHTMLEDITING_CMDMAP

Oznacza koniec mapy poleceń edycji DHTML.

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>Uwagi

Używany w połączeniu z [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap).

### <a name="example"></a>Przykład

Zobacz [przykładowe HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

##  <a name="dhtmlediting_cmd_entry"></a>  DHTMLEDITING_CMD_ENTRY

Polecenie edytowania HTML mapuje identyfikator polecenia.

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia (na przykład id_edit_copy —).

*dhtmlcmdID*<br/>
Edytowania polecenia, do którego HTML *cmdID* map (na przykład IDM_COPY).

### <a name="example"></a>Przykład

Zobacz [przykładowe HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

##  <a name="dhtmlediting_cmd_entry_func"></a>  DHTMLEDITING_CMD_ENTRY_FUNC

Mapuje identyfikator polecenia dla polecenia edycji HTML i obsługi wiadomości.

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia (na przykład id_edit_copy —).

*dhtmlcmdID*<br/>
Edytowania polecenia, do którego HTML *cmdID* map (na przykład IDM_COPY).

*member_func_name*<br/>
Nazwa funkcji obsługi wiadomości, na który jest mapowany polecenia.

### <a name="example"></a>Przykład

Zobacz [przykładowe HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

##  <a name="dhtmlediting_cmd_entry_type"></a>  DHTMLEDITING_CMD_ENTRY_TYPE

Mapuje identyfikator polecenia dla polecenia edycji HTML i elementu interfejsu użytkownika.

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia (na przykład id_edit_copy —).

*dhtmlcmdID*<br/>
Edytowania polecenia, do którego HTML *cmdID* map (na przykład IDM_COPY).

*elemType*<br/>
Typ elementu interfejsu użytkownika; jeden z AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX lub AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Przykład

Zobacz [przykładowe HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

##  <a name="dhtmlediting_cmd_entry_func_type"></a>  DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

Mapuje identyfikator polecenia do edytowania polecenia, program obsługi komunikatów i elementu interfejsu użytkownika HTML.

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia (na przykład id_edit_copy —).

*dhtmlcmdID*<br/>
Edytowania polecenia, do którego HTML *cmdID* map (na przykład IDM_COPY).

*member_func_name*<br/>
Nazwa funkcji obsługi wiadomości, na który jest mapowany polecenia.

*elemType*<br/>
Typ elementu interfejsu użytkownika; jeden z AFX_UI_ELEMTYPE_NORMAL, AFX_UI_ELEMTYPE_CHECKBOX lub AFX_UI_ELEMTYPE_RADIO.

### <a name="example"></a>Przykład

Zobacz [przykładowe HTMLEdit](../../overview/visual-cpp-samples.md).

### <a name="requirements"></a>Wymagania

  **Nagłówek** afxhtml.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)

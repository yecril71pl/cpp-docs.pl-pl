---
title: Struktura DELETEITEMSTRUCT
ms.date: 11/04/2016
f1_keywords:
- DELETEITEMSTRUCT
helpviewer_keywords:
- DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
ms.openlocfilehash: dd1f48fd584016dab740bc8a6bd05ff3b756e41b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486885"
---
# <a name="deleteitemstruct-structure"></a>Struktura DELETEITEMSTRUCT

`DELETEITEMSTRUCT` Struktury w tym artykule opisano usunięty rysowanych przez właściciela pola listy lub pola kombi element.

## <a name="syntax"></a>Składnia

```
typedef struct tagDELETEITEMSTRUCT { /* ditms */
    UINT CtlType;
    UINT CtlID;
    UINT itemID;
    HWND hwndItem;
    UINT itemData;
} DELETEITEMSTRUCT;
```

#### <a name="parameters"></a>Parametry

*CtlType*<br/>
Określa ODT_LISTBOX (pole listy rysowane przez właściciela) lub ODT_COMBOBOX (pole kombi rysowanych przez właściciela).

*CtlID*<br/>
Określa identyfikator pola listy lub pola kombi.

*Identyfikator elementu*<br/>
Określa indeks elementu w polu listy lub pola kombi usuwany.

*hwndItem*<br/>
Identyfikuje formant.

*itemData*<br/>
Określa dane zdefiniowane przez aplikację dla elementu. Ta wartość jest przekazywana do formantu w *lParam* parametru komunikat, który dodaje element do listy, pole lub pola kombi.

## <a name="remarks"></a>Uwagi

Gdy element zostanie usunięty z listy, pole lub pola kombi lub pola listy lub pola kombi jest niszczony, Windows wysyła komunikat WM_DELETEITEM do właściciela dla każdego usuniętego elementu. *LParam* parametr wiadomości zawiera wskaźnik do tej struktury.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)


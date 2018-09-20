---
title: Struktura DELETEITEMSTRUCT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DELETEITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb5b9d710bef136893c66208480056f6bc6390d3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429711"
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



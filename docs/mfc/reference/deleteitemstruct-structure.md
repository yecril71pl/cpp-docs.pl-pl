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
ms.openlocfilehash: 5c844ad428143c82e8214eab74262b326bf2c9a4
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123243"
---
# <a name="deleteitemstruct-structure"></a>Struktura DELETEITEMSTRUCT
`DELETEITEMSTRUCT` Struktury opisuje usunięty rysowanych przez właściciela pole listy lub pola kombi element.  
  
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
 *CtlType*  
 Określa ODT_LISTBOX (pole listy rysowane przez właściciela) lub ODT_COMBOBOX (pole kombi rysowanych przez właściciela).  
  
 *CtlID*  
 Określa identyfikator listy lub pola kombi.  
  
 *Identyfikator elementu*  
 Określa indeks elementu w polu listy lub pola kombi usuwana.  
  
 *hwndItem*  
 Identyfikuje formant.  
  
 *itemData*  
 Określa dane zdefiniowane przez aplikację dla elementu. Ta wartość jest przekazywana do kontrolki *lParam* parametru komunikat, który dodaje element do listy lub pola kombi.  
  
## <a name="remarks"></a>Uwagi  
 Element zostanie usunięty z listy lub pola kombi lub pola listy lub pola kombi zostanie zniszczony, system Windows wysyła wiadomość WM_DELETEITEM do właściciela dla każdego usuniętego elementu. *LParam* parametr wiadomości zawiera wskaźnik do tej struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)



---
title: Struktura DELETEITEMSTRUCT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DELETEITEMSTRUCT
dev_langs: C++
helpviewer_keywords: DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5be80d8b139f04daa0c44fc2808f61538843e3e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 `CtlType`  
 Określa **ODT_LISTBOX** (pole listy rysowane przez właściciela) lub **ODT_COMBOBOX** (pole kombi rysowanych przez właściciela).  
  
 `CtlID`  
 Określa identyfikator listy lub pola kombi.  
  
 `itemID`  
 Określa indeks elementu w polu listy lub pola kombi usuwana.  
  
 `hwndItem`  
 Identyfikuje formant.  
  
 `itemData`  
 Określa dane zdefiniowane przez aplikację dla elementu. Ta wartość jest przekazywana do kontrolki **lParam** parametru komunikat, który dodaje element do listy lub pola kombi.  
  
## <a name="remarks"></a>Uwagi  
 Gdy element zostanie usunięty z listy lub pola kombi lub pola listy lub pola kombi zostanie zniszczony, system Windows wysyła `WM_DELETEITEM` komunikat do właściciela dla każdego usuniętego elementu. **LParam** parametr wiadomości zawiera wskaźnik do tej struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)



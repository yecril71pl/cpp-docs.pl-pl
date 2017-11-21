---
title: Struktura COMPAREITEMSTRUCT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COMPAREITEMSTRUCT
dev_langs: C++
helpviewer_keywords: COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0ae9a4b8ab74ef4bf8b3a6445cf5d7faa8818c5a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compareitemstruct-structure"></a>Struktura COMPAREITEMSTRUCT
`COMPAREITEMSTRUCT` Struktury dostarcza identyfikatorów i aplikacja dostarczona danych dla dwóch elementów w polu posortowana lista rysowanych przez właściciela lub pola kombi.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct tagCOMPAREITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    HWND hwndItem;  
    UINT itemID1;  
    DWORD itemData1;  
    UINT itemID2;  
    DWORD itemData2;  
} COMPAREITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>Parametry  
 `CtlType`  
 **ODT_LISTBOX** (który określa rysowania przez właściciela pole listy) lub **ODT_COMBOBOX** (który określa rysowania przez właściciela pole kombi).  
  
 `CtlID`  
 Identyfikator formantu pole listy lub pola kombi.  
  
 `hwndItem`  
 Uchwyt okna formantu.  
  
 *itemID1*  
 Indeks pierwszego elementu w polu listy lub pola kombi są porównywane.  
  
 *itemData1*  
 Dane dostarczone przez aplikację pierwszego elementu porównywane. Ta wartość została przekazana wywołania dodania elementu do pola kombi lub listy.  
  
 *itemID2*  
 Indeks drugiego elementu w polu listy lub pola kombi są porównywane.  
  
 *itemData2*  
 Dane dostarczone przez aplikację drugiego elementu porównywane. Ta wartość została przekazana wywołania dodania elementu do pola kombi lub listy.  
  
## <a name="remarks"></a>Uwagi  
 Zawsze, gdy aplikacja dodaje nowy element pole listy rysowane przez właściciela lub pola kombi utworzone za pomocą **cbs_sort —** lub **lbs_sort —** stylu, system Windows wysyła właściciela `WM_COMPAREITEM` wiadomości. `lParam` Parametr wiadomości zawiera długi wskaźnik do `COMPAREITEMSTRUCT` struktury. Po otrzymaniu komunikatu, właściciel porównuje dwa elementy i zwraca wartość wskazującą, który element sortuje przed innych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)


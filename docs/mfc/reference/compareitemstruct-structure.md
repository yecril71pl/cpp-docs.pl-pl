---
title: Struktura COMPAREITEMSTRUCT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COMPAREITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a54b4f4749e7865d793559a9cb5f475c1d57898
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078261"
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
 *CtlType*  
 **ODT_LISTBOX** (który określa rysowania przez właściciela pole listy) lub **ODT_COMBOBOX** (który określa rysowania przez właściciela pole kombi).  
  
 *CtlID*  
 Identyfikator formantu pole listy lub pola kombi.  
  
 *hwndItem*  
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
 Zawsze, gdy aplikacja dodaje nowy element pole listy rysowane przez właściciela lub pola kombi utworzone za pomocą **cbs_sort —** lub **lbs_sort —** stylu, system Windows wysyła właściciela WM_COMPAREITEM wiadomości. *LParam* parametr wiadomości zawiera długi wskaźnik do `COMPAREITEMSTRUCT` struktury. Po otrzymaniu komunikatu, właściciel porównuje dwa elementy i zwraca wartość wskazującą, który element sortuje przed innych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winuser.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)


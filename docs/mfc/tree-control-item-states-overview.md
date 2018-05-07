---
title: Przegląd stanów elementu formantu drzewa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bc62308642492aa00a139fb15cc9e6cdcfc3247
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tree-control-item-states-overview"></a>Przegląd stanów elementu kontrolki drzewa
Każdy element formantu drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) ma określony stan bieżący. Na przykład można wybrać element, wyłączone, rozwinięty i tak dalej. W większości przypadków drzewie automatycznie ustawia stan elementu, aby odzwierciedlić akcje użytkownika, takie jak zaznaczenie elementu. Jednak można również ustawić stan elementu za pomocą [SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate) funkcji Członkowskich i pobrać bieżący stan elementu za pomocą [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate) funkcję elementu członkowskiego. Aby uzyskać pełną listę stanów elementu, zobacz [stałe kontrolki widok drzewa](http://msdn.microsoft.com/library/windows/desktop/bb759985) w zestawie Windows SDK.  
  
 Bieżący stan elementu jest określona przez `nState` parametru. Formant drzewa mogą ulec zmianie stanu elementu, aby odzwierciedlić akcji użytkownika, na przykład wybranie element lub ustawienie fokus na elemencie. Ponadto aplikacja może zmienić stan elementu, aby wyłączyć lub ukryć element lub określić nakładki obrazu lub obraz stanu.  
  
 Określ lub Zmień stan elementu `nStateMask` parametr określa, które stanu usługi bits można ustawić i `nState` parametr zawiera nowe wartości tych usługi BITS. Na przykład poniższy przykład umożliwia zmianę bieżącego stanu elementu nadrzędnego (określonego przez `hParentItem`) w `CTreeCtrl` obiektu (`m_treeCtrl`) do **TVIS_EXPANDPARTIAL**:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]  
  
 Innym przykładem zmiany stanu jest ustawienie elementu nakładki obrazów. Aby to osiągnąć, `nStateMask` musi zawierać `TVIS_OVERLAYMASK` wartości, i `nState` musi zawierać jeden indeks obrazu nakładki przesunięte osiem bitów w lewo przy użyciu [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) makra. Indeks może być 0, aby określić Brak obrazu nakładki. Nakładki obrazów muszą zostały dodane do listy nakładki obrazów formantu drzewa przez poprzednie wywołanie [CImageList::SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) funkcji. Funkcja określa jeden indeks obrazu, aby dodać; jest to indeks używany z **INDEXTOOVERLAYMASK** makra. Formant drzewa może mieć maksymalnie cztery nakładki obrazów.  
  
 Można ustawić elementu obraz stanu, `nStateMask` musi zawierać `TVIS_STATEIMAGEMASK` wartości, i `nState` musi zawierać jeden indeks obrazu stanu przesunięte 12 bitów w lewo przy użyciu [INDEXTOSTATEIMAGEMASK](http://msdn.microsoft.com/library/windows/desktop/bb775597) makra. Indeks może być 0, aby określić nie obrazu stanu. Aby uzyskać więcej informacji o obrazach nakładce i stanu, zobacz [listy obrazów formantu drzewa](../mfc/tree-control-image-lists.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)


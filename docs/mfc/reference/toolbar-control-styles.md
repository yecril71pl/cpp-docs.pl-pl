---
title: Style formantu toolBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1958c83ef5a0eec5f3c7f5873451edd3839146be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373198"
---
# <a name="toolbar-control-styles"></a>Style formantu ToolBar
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) ma zestaw styl flagi, które określają wygląd i zachowanie przycisku. Kombinacja flag można ustawić przez wywołanie metody [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle). W tym temacie wymieniono wartości flag styl i ich znaczenie.  
  
## <a name="property-values"></a>Wartości właściwości  
 Typ przycisku, który reprezentuje formantu określa następujące wartości:  
  
 TBBS_BUTTON  
 Przycisk standardowe (ustawienie domyślne).  
  
 TBBS_CHECKBOX  
 pole wyboru.  
  
 TBBS_CHECKGROUP  
 Początek grupy pola wyboru.  
  
 TBBS_GROUP  
 Początek grupy przycisków.  
  
 TBBS_SEPARATOR  
 Separator.  
  
 Następujące wartości reprezentują bieżący stan formantu:  
  
 TBBS_CHECKED  
 Pole wyboru jest zaznaczone.  
  
 TBBS_DISABLED  
 Kontrolka jest wyłączona.  
  
 TBBS_INDETERMINATE  
 Pole wyboru jest w stanie nieokreślonym.  
  
 TBBS_PRESSED  
 Przycisk jest naciśnięty.  
  
 Następująca wartość zmienia układ przycisku w pasku narzędzi:  
  
 TBBS_BREAK  
 Umieszcza w nowym wierszu lub w nowej kolumnie elementu bez oddzielające kolumnami.  
  
## <a name="remarks"></a>Uwagi  
 Bieżący styl jest przechowywany w [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle). Nie należy ustawiać nową wartość w `m_nStyle` bezpośrednio, ponieważ niektóre klasy pochodne wykonywać dodatkowego przetwarzania podczas wywoływania `SetStyles`.  
  
 Menedżer visual określa wygląd przycisków w każdym stanie. Zobacz [Menedżer wizualizacji](../../mfc/visualization-manager.md) Aby uzyskać więcej informacji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtoolbarbutton.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)   
 [Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Menedżer wizualizacji](../../mfc/visualization-manager.md)



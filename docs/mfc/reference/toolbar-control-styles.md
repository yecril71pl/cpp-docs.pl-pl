---
title: Style formantu toolBar | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 426620f5c4282858d28e80494c1f2a53a3da0fa3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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



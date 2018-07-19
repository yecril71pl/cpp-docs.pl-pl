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
ms.openlocfilehash: 35b5b87944f2b0f9ce78adbe42b59d92b98a6e5a
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885838"
---
# <a name="toolbar-control-styles"></a>Style formantu ToolBar
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) ma zestaw flag style, które określają wygląd i zachowanie przycisku. Można ustawić kombinację tych flag, wywołując [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle). Ten temat zawiera listę wartości flagi styl i ich znaczenie.  
  
## <a name="property-values"></a>Wartości właściwości  
 Następujące wartości określają typ przycisku, który reprezentuje kontrolkę:  
  
 TBBS_BUTTON  
 Przycisk standardowe (domyślne).  
  
 TBBS_CHECKBOX  
 Pole wyboru.  
  
 TBBS_CHECKGROUP  
 Początek grupy pól wyboru.  
  
 TBBS_GROUP  
 Początek grupy przycisków.  
  
 TBBS_SEPARATOR  
 Separator.  
  
 Następujące wartości reprezentują bieżący stan kontrolki:  
  
 TBBS_CHECKED  
 Pole wyboru jest zaznaczone.  
  
 TBBS_DISABLED  
 Kontrolka jest wyłączona.  
  
 TBBS_INDETERMINATE  
 Pole wyboru jest w stanie nieokreślonym.  
  
 TBBS_PRESSED  
 Naciśnięciu przycisku.  
  
 Następująca wartość zmienia układ przycisk na pasku narzędzi:  
  
 TBBS_BREAK  
 Umieszcza elementu w nowym wierszu lub w nowej kolumnie bez oddzielenie kolumn.  
  
## <a name="remarks"></a>Uwagi  
 Bieżący styl są przechowywane w [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle). Nie należy ustawiać nową wartość w `m_nStyle` bezpośrednio, ponieważ niektóre klasy pochodne wykonywać dodatkowego przetwarzania podczas wywoływania `SetStyles`.  
  
 Wizualne manager określa wygląd przycisków w każdym stanie. Zobacz [Menedżer wizualizacji](../../mfc/visualization-manager.md) Aby uzyskać więcej informacji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtoolbarbutton.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)   
 [Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Menedżer wizualizacji](../../mfc/visualization-manager.md)



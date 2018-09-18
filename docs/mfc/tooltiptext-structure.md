---
title: Struktura TOOLTIPTEXT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TOOLTIPTEXT
dev_langs:
- C++
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82c06b98acec18e845fd1353875c1453c4bee8b1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097162"
---
# <a name="tooltiptext-structure"></a>Struktura TOOLTIPTEXT
Na piśmie swoje [obsługi powiadomień Porada narzędzie](../mfc/handling-ttn-needtext-notification-for-tool-tips.md), należy użyć **TOOLTIPTEXT** struktury. Elementy członkowskie **TOOLTIPTEXT** struktury są:  
  
```cpp
typedef struct {
    NMHDR     hdr;        // required for all WM_NOTIFY messages
    LPTSTR    lpszText;   // see below
    TCHAR     szText[80]; // buffer for tool tip text
    HINSTANCE hinst;      // see below
    UINT      uflags;     // flag indicating how to interpret the
                          // idFrom member of the NMHDR structure
                          // that is included in the structure
} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;
```
  
 *HDR*  
 Określa narzędzie, które wymaga tekstu. Jedynym członkiem tej struktury, który może być konieczne jest identyfikator formantu polecenia. Identyfikator polecenia kontrolki będą znajdować się w *idFrom* członkiem **NMHDR** struktury, uzyskać dostęp przy użyciu składni `hdr.idFrom`. Zobacz [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) dyskusję na temat elementów członkowskich **NMHDR** struktury.  
  
 *lpszText*  
 Adres ciąg wyświetlany tekst dla narzędzia.  
  
 *szText*  
 Bufor, który odbiera tekst wskazówki. Aplikację można skopiować tekst do tego buforu jako alternatywę do określania adresu ciąg.  
  
 *hinst*  
 Dojście wystąpienia, które zawiera ciąg, który ma być używany jako tekst wskazówki. Jeśli *lpszText* to adres elementu tekst wskazówki ten element członkowski ma wartość NULL.  
  
Podczas obsługi `TTN_NEEDTEXT` powiadomień wiadomości, określ ciąg, który ma być wyświetlany w jednym z następujących sposobów:  
  
-   Skopiuj tekst do buforu określonego przez *szText* elementu członkowskiego.  
  
-   Skopiuj adres buforu, który zawiera tekst, który ma *lpszText* elementu członkowskiego.  
  
-   Skopiuj identyfikator zasobu ciągu do *lpszText* elementu członkowskiego, a następnie skopiuj dojście wystąpienia, które zawiera zasób do *hinst* elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)


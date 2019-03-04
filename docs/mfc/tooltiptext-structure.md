---
title: Struktura TOOLTIPTEXT
ms.date: 11/04/2016
f1_keywords:
- TOOLTIPTEXT
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
ms.openlocfilehash: 7d77ca7dc55273e6084e919323ed71e55fa68a2c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260598"
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

*hdr*<br/>
Określa narzędzie, które wymaga tekstu. Jedynym członkiem tej struktury, który może być konieczne jest identyfikator formantu polecenia. Identyfikator polecenia kontrolki będą znajdować się w *idFrom* członkiem **NMHDR** struktury, uzyskać dostęp przy użyciu składni `hdr.idFrom`. Zobacz [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) dyskusję na temat elementów członkowskich **NMHDR** struktury.

*lpszText*<br/>
Adres ciąg wyświetlany tekst dla narzędzia.

*szText*<br/>
Bufor, który odbiera tekst wskazówki. Aplikację można skopiować tekst do tego buforu jako alternatywę do określania adresu ciąg.

*hinst*<br/>
Dojście wystąpienia, które zawiera ciąg, który ma być używany jako tekst wskazówki. Jeśli *lpszText* to adres elementu tekst wskazówki ten element członkowski ma wartość NULL.

Podczas obsługi `TTN_NEEDTEXT` powiadomień wiadomości, określ ciąg, który ma być wyświetlany w jednym z następujących sposobów:

- Skopiuj tekst do buforu określonego przez *szText* elementu członkowskiego.

- Skopiuj adres buforu, który zawiera tekst, który ma *lpszText* elementu członkowskiego.

- Skopiuj identyfikator zasobu ciągu do *lpszText* elementu członkowskiego, a następnie skopiuj dojście wystąpienia, które zawiera zasób do *hinst* elementu członkowskiego.

## <a name="see-also"></a>Zobacz także

[Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

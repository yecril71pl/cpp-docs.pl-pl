---
title: Struktura TOOLTIPTEXT
ms.date: 11/04/2016
f1_keywords:
- TOOLTIPTEXT
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
ms.openlocfilehash: 80b95225a277a7985c30e5ea453597b06e501753
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513302"
---
# <a name="tooltiptext-structure"></a>Struktura TOOLTIPTEXT

W przypadku pisania [procedury obsługi powiadomień etykietki narzędzia](../mfc/handling-ttn-needtext-notification-for-tool-tips.md)należy użyć struktury **ToolTipText** . Elementy członkowskie struktury **ToolTipText** są następujące:

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
Identyfikuje narzędzie, które wymaga tekstu. Jedynym członkiem tej struktury może być wymagany identyfikator polecenia kontrolki. Identyfikator polecenia kontrolki będzie znajdować się w *idFrom* składowej struktury **NMHDR** , do którego zostanie uzyskany `hdr.idFrom`dostęp ze składnią. Zobacz [NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) , aby zapoznać się z omówieniem elementów członkowskich struktury **NMHDR** .

*lpszText*<br/>
Adres ciągu, w którym jest wyświetlany tekst dla narzędzia.

*szText*<br/>
Bufor, który odbiera tekst etykietki narzędzia. Aplikacja może skopiować tekst do tego buforu jako alternatywę do określenia adresu ciągu.

*hinst*<br/>
Dojście wystąpienia zawierające ciąg, który ma być używany jako tekst etykietki narzędzia. Jeśli *lpszText* jest adresem tekstu etykietki narzędzia, ten element członkowski ma wartość null.

Podczas obsługi `TTN_NEEDTEXT` komunikatu powiadomienia należy określić ciąg, który ma być wyświetlany w jeden z następujących sposobów:

- Skopiuj tekst do buforu określonego przez element członkowski *szText* .

- Skopiuj adres buforu, który zawiera tekst do elementu członkowskiego *lpszText* .

- Skopiuj identyfikator zasobu ciągu do elementu członkowskiego *lpszText* i skopiuj dojście wystąpienia zawierające zasób do elementu członkowskiego *hinst* .

## <a name="see-also"></a>Zobacz także

[Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

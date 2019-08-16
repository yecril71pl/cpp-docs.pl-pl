---
title: Ustawianie klawisza dostępu
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: 7b49f24039b130f74693e7567f5287476126f225
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511218"
---
# <a name="setting-a-hot-key"></a>Ustawianie klawisza dostępu

Aplikacja może korzystać z informacji dostarczonych przez kontrolkę klawisza dostępu ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) na jeden z dwóch sposobów:

- Skonfiguruj globalny klawisz dostępu w celu aktywowania okna niepodrzędnego, wysyłając do okna komunikat [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey) , który ma zostać aktywowany.

- Skonfiguruj odpowiedni dla wątku klawisz dostępu, wywołując funkcję systemu Windows [funkcję RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey).

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

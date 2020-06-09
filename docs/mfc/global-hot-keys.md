---
title: Globalne klawisze dostępu
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- CHotKeyCtrl class [MFC], global hot keys
- access keys [MFC], hot keys
- global hot keys [MFC]
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
ms.openlocfilehash: 5fdcfbef1db0d20126f8eac144f74f8b92410504
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618738"
---
# <a name="global-hot-keys"></a>Globalne klawisze dostępu

Globalny klawisz dostępu jest skojarzony z określonym oknem niepodrzędnym. Umożliwia użytkownikowi aktywowanie okna z dowolnej części systemu. Aplikacja ustawia globalny klawisz dostępu dla określonego okna przez wysłanie komunikatu [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey) do tego okna. Na przykład, jeśli `m_HotKeyCtrl` jest obiektem [CHotKeyCtrl](reference/chotkeyctrl-class.md) i `pMainWnd` jest wskaźnikiem do okna, które ma zostać aktywowane po naciśnięciu klawisza skrótu, można użyć poniższego kodu do skojarzenia klawisza dostępu określonego w kontrolce z oknem wskazywanym przez `pMainWnd` .

[!code-cpp[NVC_MFCControlLadenDialog#18](codesnippet/cpp/global-hot-keys_1.cpp)]

Za każdym razem, gdy użytkownik naciśnie globalny klawisz dostępu, określone okno odbiera komunikat [WM_SYSCOMMAND](/windows/win32/menurc/wm-syscommand) , który określa **SC_HOTKEY** jako typ polecenia. Ten komunikat powoduje także aktywowanie okna, które je odbiera. Ponieważ ten komunikat nie zawiera żadnych informacji dotyczących dokładnego klawisza, który został naciśnięty, użycie tej metody nie pozwala na rozróżnienie między różnymi klawiszami dostępu, które mogą być dołączone do tego samego okna. Klawisz dostępu pozostaje ważny do momentu, gdy aplikacja, która wysłała **WM_SETHOTKEY** kończy pracę.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHotKeyCtrl](using-chotkeyctrl.md)<br/>
[Formanty](controls-mfc.md)

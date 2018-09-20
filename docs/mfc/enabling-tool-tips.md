---
title: Włączanie etykietek narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing tool tips [MFC]
- enabling tool tips [MFC]
- tool tips [MFC], initializing
- tool tips [MFC], enabling
ms.assetid: 06b7c889-7722-4ce6-8b88-9efa50fe6369
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 968d31b49c6d2b2fe5a5f69e04f58f17de8df5a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440488"
---
# <a name="enabling-tool-tips"></a>Włączanie etykietek narzędzi

Można włączyć narzędzie Porada obsługę formantów podrzędnych okna (np. kontrolki na formularzu widoku lub okno dialogowe).

### <a name="to-enable-tool-tips-for-the-child-controls-of-a-window"></a>Aby włączyć etykietki narzędzi dla formantów podrzędnych okna

1. Wywołaj `EnableToolTips` okna, dla którego chcesz podać etykietek narzędzi.

1. Podaj ciąg dla każdego formantu w Twojej [powiadomienia TTN_NEEDTEXT](../mfc/handling-ttn-needtext-notification-for-tool-tips.md) programu obsługi. Program obsługi jest w mapie komunikatów okna, który zawiera formanty podrzędne (na przykład klasy widoku formularza). Ta procedura obsługi powinna wywołać funkcję, identyfikuje formant i ustawia **pszText** do określania tekstu, używane przez formantem etykietki narzędzia.

## <a name="see-also"></a>Zobacz też

[Etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)


---
title: Dostosowywanie elementu nagłówka&#39;wygląd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75e32021420848e7493d9652bb37cb12fa4df56b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055468"
---
# <a name="customizing-the-header-item39s-appearance"></a>Dostosowywanie elementu nagłówka&#39;wygląd

Ustawiając *dwStyle* parametru podczas pierwszego tworzenia formantu nagłówka ([CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create)), można zdefiniować wygląd i zachowanie nagłówka elementów lub nagłówka samej kontrolki.

Poniżej przedstawiono niektóre spośród style, które można ustawić, a ich celem:

- Aby element nagłówka wyglądać tak, jak przycisk, użyj **HDS_BUTTONS** stylu.

   Użyj tego stylu, jeśli chcesz do wykonywania akcji w odpowiedzi na kliknięcia myszy na elemencie nagłówka, takich jak sortowanie danych według określonej kolumny, jak to zrobić w programie Microsoft Outlook.

- Aby nadać elementy nagłówka wygląd "aktywne śledzenie", gdy kursor myszy przesuwa się nad nimi, należy użyć **HDS_HOTTRACK** stylu.

   Aktywne śledzenie wyświetla 3D konspektu przesuwany wskaźnik myszy nad elementem, w przeciwnym razie prostego paska.

- Aby wskazać, kontrolki nagłówka powinien być ukryty, należy użyć **HDS_HIDDEN** stylu.

   **HDS_HIDDEN** styl wskazuje, że kontrolki nagłówka jest przeznaczony do użycia jako kontener danych i Wizualna kontrola. Ten styl nie automatycznie ukrywać kontrolki, ale zamiast tego ma wpływ na zachowanie `CHeaderCtrl::Layout`. Wartość zwracana w *cy* członkiem `WINDOWPOS` struktury będą równe zeru wskazujący, że kontrolka nie powinny być widoczne dla użytkownika.

Aby uzyskać więcej informacji o tych właściwościach, zobacz [elementów](/windows/desktop/Controls/header-controls) w zestawie Windows SDK. Aby dowiedzieć się, jak dodawanie elementów do formantu nagłówka, zobacz [Dodawanie elementów do formantu nagłówka](../mfc/adding-items-to-the-header-control.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)


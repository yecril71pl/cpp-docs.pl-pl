---
title: Dostosowywanie elementu nagłówka&#39;wygląd s | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: e09f8bc0b61e22435ee348968f117940b57132e3
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930878"
---
# <a name="customizing-the-header-item39s-appearance"></a>Dostosowywanie elementu nagłówka&#39;wygląd s
Przez ustawienie *dwStyle* parametru podczas tworzenia formantu nagłówka ([CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create)), można określić wygląd i zachowanie nagłówka elementy lub nagłówka samą kontrolką.  
  
 Oto przykładowy style, które można ustawić, a ich przeznaczenie:  
  
-   Aby element nagłówka wygląd przycisku polecenia, użyj **HDS_BUTTONS** stylu.  
  
     Użyj tego stylu, jeśli chcesz wykonywania akcji w odpowiedzi na kliknięcie myszą w elemencie nagłówka, takie jak sortowanie według określonej kolumny danych, co jest wykonywane w programie Microsoft Outlook.  
  
-   Aby dać elementów nagłówka wygląd "aktywne śledzenie", gdy wskaźnik myszy przesuwa się nad nimi, należy użyć **HDS_HOTTRACK** stylu.  
  
     Aktywne śledzenie wyświetla 3D konspektu jako wskaźnik myszy przesuwa się nad elementu w innym przypadku płaskiej paska.  
  
-   Aby wskazać formantu nagłówka powinien być ukryty, użyj **HDS_HIDDEN** stylu.  
  
     **HDS_HIDDEN** styl wskazuje, że formantu nagłówka jest przeznaczony do użycia jako kontener danych i nie visual formantu. Ten styl nie ukrywa automatycznie formantu, ale zamiast tego wpływa na działanie `CHeaderCtrl::Layout`. Wartość zwracana w *cy* członkiem `WINDOWPOS` struktury będą miały wartość zero wskazujący, że kontrolka nie powinny być widoczne dla użytkownika.  
  
 Aby uzyskać więcej informacji na temat tych właściwości, zobacz [elementów](http://msdn.microsoft.com/library/windows/desktop/bb775238) w zestawie Windows SDK. Aby uzyskać informacje dotyczące dodawania elementów do formantu nagłówka, zobacz [Dodawanie elementów do formantu nagłówka](../mfc/adding-items-to-the-header-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)


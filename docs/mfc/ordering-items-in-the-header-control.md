---
title: Określanie kolejności elementów w formancie nagłówka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DS_DRAGDROP
dev_langs:
- C++
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60139821c1b15673fac0fb8f9ec3925cbfa6dc31
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052100"
---
# <a name="ordering-items-in-the-header-control"></a>Określanie kolejności elementów w formancie nagłówka

Po [dodać elementów do formantu nagłówka](../mfc/adding-items-to-the-header-control.md), można manipulować i uzyskać informacje na temat ich kolejność, za pomocą następujących funkcji:

- [CHeaderCtrl::GetOrderArray](../mfc/reference/cheaderctrl-class.md#getorderarray) i [CHeaderCtrl::SetOrderArray](../mfc/reference/cheaderctrl-class.md#setorderarray)

   Pobiera i ustawia kolejność elementów nagłówka od lewej do prawej.

- [CHeaderCtrl::OrderToIndex](../mfc/reference/cheaderctrl-class.md#ordertoindex).

   Pobiera wartość indeksu dla elementu określonego nagłówka.

Oprócz poprzedniego funkcji elementów członkowskich hds_dragdrop — styl zezwala użytkownikowi na przeciąganie i upuszczanie elementy nagłówka w formancie nagłówka. Aby uzyskać więcej informacji, zobacz [Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka](../mfc/providing-drag-and-drop-support-for-header-items.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)


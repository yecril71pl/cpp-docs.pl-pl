---
title: Likwidowanie formantu listy
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: 5004026da6bb309cc2c966384724b7b98e254e1d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508700"
---
# <a name="destroying-the-list-control"></a>Likwidowanie formantu listy

Jeśli obiekt [CListCtrl](../mfc/reference/clistctrl-class.md) zostanie osadzony jako element członkowski danych widoku lub klasy okna dialogowego, zostanie zniszczony, gdy jego właściciel zostanie zniszczony. Jeśli używasz [CListView](../mfc/reference/clistview-class.md), struktura niszczy formant, gdy niszczy widok.

Jeśli ustawisz dla niektórych danych listy dane, które mają być przechowywane w aplikacji, a nie w kontrolce listy, należy rozmieścić jej cofanie alokacji. Aby uzyskać więcej informacji, zobacz [elementy wywołania zwrotnego i Maska wywołania zwrotnego](/windows/win32/Controls/using-list-view-controls) w Windows SDK.

Ponadto użytkownik jest odpowiedzialny za cofnięcie przydziału list obrazów utworzonych i skojarzonych z obiektem kontrolki listy.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

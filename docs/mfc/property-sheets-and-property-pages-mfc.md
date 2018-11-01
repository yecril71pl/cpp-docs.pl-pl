---
title: Arkusze właściwości i strony właściwości (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
ms.openlocfilehash: 971b8cde1560e54f87269e8b85a41cdec55c091d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445399"
---
# <a name="property-sheets-and-property-pages-mfc"></a>Arkusze właściwości i strony właściwości (MFC)

MFC [okno dialogowe](../mfc/dialog-boxes.md) można wykonać na "kartę okna dialogowego" się przez dołączenie arkusze właściwości i strony właściwości. Tego rodzaju okno dialogowe, podobnie jak wiele okien dialogowych w programie Microsoft Word, Excel i Visual C++ o nazwie "arkusz właściwości" w MFC, prawdopodobnie zawiera stos arkuszy z kartami, podobnie jak w stosie foldery plików zaobserwować wzdłużnego lub grupy systemu windows kaskadowy. Formanty na pierwszej karcie są widoczne; labeled karty jest widoczny na tylnej karty. Arkusze właściwości są szczególnie przydatne w przypadku zarządzania dużą liczbą właściwości lub ustawień, które dość starannego dzielą się na kilka grup. Zazwyczaj jeden arkusz właściwości może uprościć interfejsu użytkownika, zastępując wiele oddzielnych okien dialogowych.

Począwszy od wersji 4.0 MFC arkusze właściwości i strony właściwości są implementowane przy użyciu typowych kontrolek, które pochodzą z wersją Windows 95 i Windows NT 3.51 lub nowszej.

Arkusze właściwości są implementowane za pomocą klasy [CPropertySheet](../mfc/reference/cpropertysheet-class.md) i [CPropertyPage](../mfc/reference/cpropertypage-class.md) (opisanego w *odwołanie MFC*). `CPropertySheet` Definiuje ogólny okno dialogowe, które mogą zawierać wiele "strony" na podstawie `CPropertyPage`.

Aby uzyskać informacje na temat tworzenia i pracy z arkuszy właściwości, zobacz temat [arkusze właściwości](../mfc/property-sheets-mfc.md).

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Arkusze właściwości i strony właściwości w MFC](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[Wymiana danych](../mfc/exchanging-data.md)<br/>
[Tworzenie niemodalnego arkusza właściwości](../mfc/creating-a-modeless-property-sheet.md)<br/>
[Obsługa przycisku Zastosuj](../mfc/handling-the-apply-button.md)


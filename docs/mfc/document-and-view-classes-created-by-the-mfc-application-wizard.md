---
title: Klasy dokumentów i widoków tworzone przez kreatora aplikacji MFC
ms.date: 11/04/2016
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
ms.openlocfilehash: 95b50e34d612c3b8f5dea2f8b469bd6c65182d41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408031"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>Klasy dokumentów i widoków tworzone przez kreatora aplikacji MFC

Kreator aplikacji MFC zapewnia łatwiej rozpocząć pracę w rozwoju programu, tworząc klasy szkieletowych dokumentów i widoków dla Ciebie. Następnie możesz [mapowania poleceń i komunikatów w ramach tych zajęć](../mfc/reference/mapping-messages-to-functions.md) i użyć Edytor kodu źródłowego języka Visual C++ do zapisania swoich funkcji elementów członkowskich.

Klasy dokumentów, tworzone przez Kreatora aplikacji MFC jest pochodną klasy [CDocument](../mfc/reference/cdocument-class.md). Widok klasy jest tworzony na podstawie [CView](../mfc/reference/cview-class.md). Nazwy, Kreator aplikacji zapewnia te klasy i pliki zawierające ich opierają się na nazwę projektu, należy podać w oknie dialogowym Kreatora aplikacji. W Kreatorze aplikacji można użyć strony wygenerowane klasy, aby zmienić domyślne nazwy.

Niektóre aplikacje mogą wymagać więcej niż jednej klasy dokumentu, widoku klasy lub klasy okien ramowych. Aby uzyskać więcej informacji, zobacz [wiele typów dokumentów, widoków i ramek Windows](../mfc/multiple-document-types-views-and-frame-windows.md).

## <a name="see-also"></a>Zobacz także

[Architektura dokument/widok](../mfc/document-view-architecture.md)

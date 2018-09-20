---
title: Dokumentów i wyświetlanie klas tworzone przez Kreatora aplikacji MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb1a1fc6c35bfb9589e827d798cb112640fa9b2f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417621"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>Klasy dokumentów i widoków tworzone przez kreatora aplikacji MFC

Kreator aplikacji MFC zapewnia łatwiej rozpocząć pracę w rozwoju programu, tworząc klasy szkieletowych dokumentów i widoków dla Ciebie. Następnie możesz [mapowania poleceń i komunikatów w ramach tych zajęć](../mfc/reference/mapping-messages-to-functions.md) i użyć Edytor kodu źródłowego języka Visual C++ do zapisania swoich funkcji elementów członkowskich.

Klasy dokumentów, tworzone przez Kreatora aplikacji MFC jest pochodną klasy [CDocument](../mfc/reference/cdocument-class.md). Widok klasy jest tworzony na podstawie [CView](../mfc/reference/cview-class.md). Nazwy, Kreator aplikacji zapewnia te klasy i pliki zawierające ich opierają się na nazwę projektu, należy podać w oknie dialogowym Kreatora aplikacji. W Kreatorze aplikacji można użyć strony wygenerowane klasy, aby zmienić domyślne nazwy.

Niektóre aplikacje mogą wymagać więcej niż jednej klasy dokumentu, widoku klasy lub klasy okien ramowych. Aby uzyskać więcej informacji, zobacz [wiele typów dokumentów, widoków i ramek Windows](../mfc/multiple-document-types-views-and-frame-windows.md).

## <a name="see-also"></a>Zobacz też

[Architektura dokument/widok](../mfc/document-view-architecture.md)


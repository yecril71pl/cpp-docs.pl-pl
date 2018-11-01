---
title: Tworzenie dokumentu widoku
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], creating
- views [MFC], and frame windows
- views [MFC], creating
- tables [MFC]
- MFC, views
- document/view architecture [MFC], creating document/view
- object creators
- MFC, documents
- tables [MFC], objects each MFC object creates
ms.assetid: bda14f41-ed50-439d-af9e-591174e7dd64
ms.openlocfilehash: eccc65df784d000f8dccc244e295da522658b626
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633564"
---
# <a name="documentview-creation"></a>Tworzenie dokumentu/widoku

Struktura dostarcza implementacje **New** i **Otwórz** polecenia (między innymi) na **pliku** menu. Tworzenie nowego dokumentu skojarzonego widoku i ramki okna jest wspólnego nakładu pracy obiekt aplikacji, szablon dokumentu, nowo utworzonego dokumentu i okno ramowe nowo utworzony. W poniższej tabeli podsumowano, obiekty, które tworzyć co.

### <a name="object-creators"></a>Twórcy obiektu

|Kreator|Tworzy|
|-------------|-------------|
|Obiekt aplikacji|Szablon dokumentu|
|Szablon dokumentu|dokument|
|Szablon dokumentu|Okno ramowe|
|Okno ramowe|Widok|

## <a name="see-also"></a>Zobacz też

[Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Tworzenie szablonu dokumentu](../mfc/document-template-creation.md)<br/>
[Relacje między obiektami MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)


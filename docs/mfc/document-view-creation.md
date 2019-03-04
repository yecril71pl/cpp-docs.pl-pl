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
ms.openlocfilehash: b5f9b783e8e14744a816fd63b327ed95d9da8e8a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304954"
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

## <a name="see-also"></a>Zobacz także

[Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Tworzenie szablonu dokumentu](../mfc/document-template-creation.md)<br/>
[Relacje między obiektami MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)

---
title: Tworzenie widoku dokumentu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 894bb5a0b3a4c86d764fc6f4a0e4b9ae18422669
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931856"
---
# <a name="documentview-creation"></a>Tworzenie dokumentu/widoku
Platformę dostarcza implementacji **nowy** i **Otwórz** poleceń (między innymi) na **pliku** menu. Tworzenie nowego dokumentu skojarzonego widoku i ramki okna jest współpracy nakładu pracy między obiektu aplikacji, szablon dokumentu, nowo utworzonego dokumentu i okno ramowe nowo utworzony. W poniższej tabeli przedstawiono obiekty, które tworzenie co.  
  
### <a name="object-creators"></a>Twórcy obiektu  
  
|Kreator|Tworzy|  
|-------------|-------------|  
|obiekt aplikacji|Szablon dokumentu|  
|Szablon dokumentu|dokument|  
|Szablon dokumentu|Okna ramowe|  
|Okna ramowe|Widok|  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Tworzenie szablonu dokumentu](../mfc/document-template-creation.md)   
 [Relacje między obiektami MFC](../mfc/relationships-among-mfc-objects.md)   
 [Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)


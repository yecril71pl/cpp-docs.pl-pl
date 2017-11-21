---
title: Tworzenie widoku dokumentu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e98f6e4b1b9ecd5848c2701043aa9b0b7dcea7d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="documentview-creation"></a>Tworzenie dokumentu/widoku
Platformę dostarcza implementacji `New` i **Otwórz** poleceń (między innymi) na **pliku** menu. Tworzenie nowego dokumentu skojarzonego widoku i ramki okna jest współpracy nakładu pracy między obiektu aplikacji, szablon dokumentu, nowo utworzonego dokumentu i okno ramowe nowo utworzony. W poniższej tabeli przedstawiono obiekty, które tworzenie co.  
  
### <a name="object-creators"></a>Twórcy obiektu  
  
|Kreator|Tworzy|  
|-------------|-------------|  
|Obiekt aplikacji|Szablon dokumentu|  
|Szablon dokumentu|dokument|  
|Szablon dokumentu|Okna ramowe|  
|Okna ramowe|Widok|  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Tworzenie szablonu dokumentu](../mfc/document-template-creation.md)   
 [Relacje między obiektami MFC](../mfc/relationships-among-mfc-objects.md)   
 [Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)


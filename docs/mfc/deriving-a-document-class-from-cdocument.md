---
title: Wyprowadzanie klasy dokumentów z obiektu CDocument | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 698957d4e307ad1f099d5aef7de131c538ee4871
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="deriving-a-document-class-from-cdocument"></a>Wyprowadzanie klasy dokumentów z obiektu CDocument
Dokumenty zawierają i zarządzać danymi aplikacji. Aby używać klasy dokumentów dostarczonych przez Kreatora aplikacji MFC, wykonaj następujące czynności:  
  
-   Klasa wyprowadzona z **CDocument** dla każdego typu dokumentu.  
  
-   Dodaj element członkowski zmienne do przechowywania danych każdy dokument.  
  
-   Zastąpienie **CDocument**w `Serialize` funkcji członkowskiej we własnej klasy dokumentu. `Serialize` zapisuje i odczytuje dane dokumentu do i z dysku.  
  
## <a name="other-document-functions-often-overridden"></a>Inne funkcje dokumentu często zastępowane  
 Można także zastąpić inne **CDocument** funkcji elementów członkowskich. W szczególności często należy zastąpić [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) i [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) zainicjować elementy członkowskie danych dokumentu i [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) do zniszczenia dynamicznie przydzielane danych. Zawiera informacje o możliwym do zastąpienia członków, klasa [CDocument](../mfc/reference/cdocument-class.md) w *odwołania MFC*.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie dokumentów](../mfc/using-documents.md)


---
title: Zarządzanie danymi za pomocą zmiennych danych dokumentu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ca7c673f47510282e129eab2538008400eb2fb9
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929435"
---
# <a name="managing-data-with-document-data-variables"></a>Zarządzanie danymi za pomocą zmiennych danych dokumentu
Implementuje danych dokumentu jako zmienne Członkowskie klasy dokumentu. Na przykład program bazgrołów deklaruje element członkowski danych typu `CObList` — połączonej listy, która przechowuje wskaźniki do `CObject` obiektów. Ta lista służy do przechowywania tablice punktów, które tworzą odręcznej Rysowanie linii.  
  
 Sposobu implementacji dokumentu elementu członkowskiego danych zależy od charakteru aplikacji. Aby ułatwić wychodzących, MFC dostarcza grupę "klasy kolekcji" — tablic, list i map (słowniki), łącznie z kolekcjami na podstawie szablonów języka C++ — wraz z klas, które zapewniają różne typy danych, takich jak `CString`, `CRect`, `CPoint`, `CSize`, i `CTime`. Aby uzyskać więcej informacji na temat tych klas, zobacz [Przegląd biblioteki klas](../mfc/class-library-overview.md) w *odwołania MFC*.  
  
 Podczas definiowania danych elementów członkowskich dokumentu zostanie dodany do klasy dokumentu, aby ustawić i Pobierz elementy danych i wykonywać inne przydatne operacje na nich zazwyczaj funkcji elementów członkowskich.  
  
 Widoków dostępu do obiektu dokumentu przy użyciu widoku wskaźnik do dokumentu, zainstalowane w widoku w czasie tworzenia. This, wskaźnik w widoku funkcje Członkowskie mogą pobierać wywołując `CView` funkcji członkowskiej `GetDocument`. Należy rzutować ten wskaźnik do typu dokumentu. Następnie można dostęp do dokumentów publicznych elementów członkowskich za pomocą wskaźnika.  
  
 Transfer danych częste musi mieć bezpośredni dostęp lub chcesz użyć niepubliczne elementy członkowskie klasy dokumentu, można wprowadzić widoku klasy friend (w C++ warunki) klasy dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie dokumentów](../mfc/using-documents.md)


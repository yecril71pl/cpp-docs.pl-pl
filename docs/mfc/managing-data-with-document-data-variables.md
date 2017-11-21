---
title: "Zarządzanie danymi za pomocą zmiennych danych dokumentu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: af24c461d579ee784487697cc376d9e8f0816643
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="managing-data-with-document-data-variables"></a>Zarządzanie danymi za pomocą zmiennych danych dokumentu
Implementuje danych dokumentu jako zmienne Członkowskie klasy dokumentu. Na przykład program bazgrołów deklaruje element członkowski danych typu `CObList` — połączonej listy, która przechowuje wskaźniki do `CObject` obiektów. Ta lista służy do przechowywania tablice punktów, które tworzą odręcznej Rysowanie linii.  
  
 Sposobu implementacji dokumentu elementu członkowskiego danych zależy od charakteru aplikacji. Aby ułatwić wychodzących, MFC dostarcza grupę "klasy kolekcji" — tablic, list i map (słowniki), łącznie z kolekcjami na podstawie szablonów języka C++ — wraz z klas, które zapewniają różne typy danych, takich jak `CString`, `CRect`, `CPoint`, `CSize`, i `CTime`. Aby uzyskać więcej informacji na temat tych klas, zobacz [Przegląd biblioteki klas](../mfc/class-library-overview.md) w *odwołania MFC*.  
  
 Podczas definiowania danych elementów członkowskich dokumentu zostanie dodany do klasy dokumentu, aby ustawić i Pobierz elementy danych i wykonywać inne przydatne operacje na nich zazwyczaj funkcji elementów członkowskich.  
  
 Widoków dostępu do obiektu dokumentu przy użyciu widoku wskaźnik do dokumentu, zainstalowane w widoku w czasie tworzenia. This, wskaźnik w widoku funkcje Członkowskie mogą pobierać wywołując `CView` funkcji członkowskiej **GetDocument**. Należy rzutować ten wskaźnik do typu dokumentu. Następnie można dostęp do dokumentów publicznych elementów członkowskich za pomocą wskaźnika.  
  
 Transfer danych częste musi mieć bezpośredni dostęp lub chcesz użyć niepubliczne elementy członkowskie klasy dokumentu, można wprowadzić widoku klasy friend (w C++ warunki) klasy dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie dokumentów](../mfc/using-documents.md)


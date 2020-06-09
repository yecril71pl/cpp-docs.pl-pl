---
title: Zarządzanie danymi za pomocą zmiennych danych dokumentu
ms.date: 11/04/2016
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
ms.openlocfilehash: 3d845b0fc3d00369d44c21c04a3fb7e3b8d6189e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618322"
---
# <a name="managing-data-with-document-data-variables"></a>Zarządzanie danymi za pomocą zmiennych danych dokumentu

Zaimplementuj dane dokumentu jako zmienne składowe klasy dokumentu. Na przykład program Bazgrołs deklaruje składową danych typu `CObList` — połączoną listę, która przechowuje wskaźniki do `CObject` obiektów. Ta lista służy do przechowywania tablic punktów tworzących rysowanie linii odręcznej.

Sposób implementacji danych elementu członkowskiego dokumentu zależy od charakteru aplikacji. Aby ułatwić Ci, MFC dostarcza grupę "klasy kolekcji" — tablice, listy i mapy (słowniki), w tym kolekcje oparte na szablonach języka C++ — oraz klasy, które hermetyzują różne typy danych, takie jak,, `CString` , `CRect` `CPoint` `CSize` i `CTime` . Aby uzyskać więcej informacji na temat tych klas, zobacz [Omówienie biblioteki klas](class-library-overview.md) w *dokumentacji MFC*.

Gdy definiujesz dane elementu członkowskiego dokumentu, zazwyczaj dodasz funkcje członkowskie do klasy dokumentu, aby ustawić i pobrać elementy danych i wykonać inne użyteczne operacje na nich.

Twoje widoki uzyskują dostęp do obiektu dokumentu przy użyciu wskaźnika widoku do dokumentu, który jest instalowany w widoku podczas tworzenia. Możesz pobrać ten wskaźnik w funkcjach składowych widoku, wywołując `CView` funkcję członkowską `GetDocument` . Upewnij się, że ten wskaźnik jest rzutowany na własny typ dokumentu. Następnie można uzyskać dostęp do członków dokumentu publicznego za pomocą wskaźnika.

Jeśli częste przesyłanie danych wymaga bezpośredniego dostępu lub chcesz użyć niepublicznych elementów członkowskich klasy dokumentu, możesz chcieć, aby Twoja Klasa widoku była znajoma (w warunkach C++) klasy dokumentu.

## <a name="see-also"></a>Zobacz też

[Używanie dokumentów](using-documents.md)

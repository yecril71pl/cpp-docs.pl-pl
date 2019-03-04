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
ms.openlocfilehash: dc21bd4b3dbe7609a33af4b4f93f15a3f5c9a64e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259974"
---
# <a name="managing-data-with-document-data-variables"></a>Zarządzanie danymi za pomocą zmiennych danych dokumentu

Implementowanie danych dokumentu jako zmienne Członkowskie klasy dokumentu. Na przykład program bazgrołów deklaruje element członkowski danych typu `CObList` — połączonej listy, która przechowuje wskaźniki do `CObject` obiektów. Ta lista jest używana do przechowywania tablic punkty, które tworzą freehand Rysowanie linii.

Sposób implementacji dokumentu element członkowski danych zależy od charakteru aplikacji. Aby okazać się pomocny, MFC dostarcza grupę "klasy kolekcji" — tablic, list i map (słowniki), łącznie z kolekcjami, na podstawie szablonów języka C++ — wraz z klas, które zapewniają różne typy danych, takich jak `CString`, `CRect`, `CPoint`, `CSize`, i `CTime`. Aby uzyskać więcej informacji na temat tych klas, zobacz [Przegląd biblioteki klas](../mfc/class-library-overview.md) w *odwołanie MFC*.

Podczas definiowania dokumentu element członkowski danych zazwyczaj dodasz funkcji składowych do klasy dokumentu, aby ustawić i pobieranie elementów danych i wykonywać na nich inne przydatne operacje.

Widoków dostęp do obiektu dokumentu przy użyciu widoku wskaźnik do dokumentu, zainstalowane w widoku w czasie jego tworzenia. Możesz pobrać ten wskaźnik w widoku elementów członkowskich, wywołując `CView` funkcja elementu członkowskiego `GetDocument`. Pamiętaj rzutować wskaźnik do typu dokumentu. Tak powstały dokumenty publiczne elementy członkowskie za pomocą wskaźnika.

Transfer danych często wymaga bezpośredniego dostępu lub chcesz użyć niepubliczne składowe klasy dokumentu, można utworzyć widoku klasy friend (w warunkach C++), klasy dokumentu.

## <a name="see-also"></a>Zobacz także

[Używanie dokumentów](../mfc/using-documents.md)

---
title: 'Porady: konwertowanie istniejącej wstążki MFC na zasób wstążki'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
ms.openlocfilehash: 2ba2907a95018948670847282fd09e0a71a8c106
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509580"
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>Porady: konwertowanie istniejącej wstążki MFC na zasób wstążki

Zasoby wstążki są łatwiejsze do wizualizacji, modyfikowania i obsłudze niż ręcznie zakodowane wstążki. W tym temacie opisano, jak przekonwertować ręcznie zakodowane wstążki w projekcie MFC na zasób wstążki.

Musi mieć istniejący projekt MFC, który zawiera kod, który używa klasy wstążek MFC, na przykład [klasa CMFCRibbonBar](../mfc/reference/cmfcribbonbar-class.md).

### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>Aby przekonwertować wstążki MFC na zasób wstążki

1. W programie Visual Studio w istniejącym projekcie MFC, otwórz plik źródłowy gdzie `CMFCRibbonBar` obiekt jest zainicjowany. Zazwyczaj plik jest mainfrm.cpp. Dodaj następujący kod po kodzie inicjowania dla wstążki.

```
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");

```

   Zapisz i zamknij plik.

1. Tworzenie i uruchamianie aplikacji MFC, a następnie w programie Notatnik, otwórz RibbonOutput.txt i skopiuj jego zawartość.

1. W programie Visual Studio na **projektu** menu, kliknij przycisk **Dodaj zasób**. W **Dodaj zasób** okno dialogowe, wybierz opcję **wstążki** a następnie kliknij przycisk **New**.

   Visual Studio tworzy zasób Wstążki i otwiera go w widoku Projekt. Identyfikator zasobu wstążki jest IDR_RIBBON1, która jest wyświetlana w **widok zasobów**. Wstążka jest zdefiniowana w pliku XML ribbon1.mfcribbon ms.

1. W programie Visual Studio Otwórz ribbon1.mfcribbon ms, usunąć jej zawartość, a następnie wklej zawartość RibbonOutput.txt, które wcześniej zostały skopiowane. Zapisz i zamknij ribbon1.mfcribbon ms.

1. Ponownie otwórz plik źródłowy, w którym zainicjowano obiektu CMFCRibbonBar (zazwyczaj mainfrm.cpp) i komentarz istniejącego kodu wstążki. Dodaj następujący kod po kodzie, który zostanie oznaczone jako komentarz.

```
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);

```

1. Skompiluj projekt, a następnie uruchom program.

## <a name="see-also"></a>Zobacz też

[Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)


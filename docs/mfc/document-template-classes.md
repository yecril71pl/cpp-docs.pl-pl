---
title: Klasy szablonów dokumentów
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: b15263005f8bd6a8fdc9f9f29ea268fe8a6b95a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448077"
---
# <a name="document-template-classes"></a>Klasy szablonów dokumentów

Szablon dokumentu obiektów koordynacji tworzenia dokumentu, widoku i ramki okna obiektów, kiedy nowy dokument lub utworzony widok.

[CDocTemplate](../mfc/reference/cdoctemplate-class.md)<br/>
Klasa bazowa dla szablonów dokumentów. Nigdy nie użyjesz tej klasy bezpośrednio; Zamiast tego należy użyć jest jedną z innych szablonów dokumentów klas pochodzących z tej klasy.

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
Szablon dla dokumentów w interfejsu wielu dokumentów (MDI). Aplikacje MDI mogą mieć wiele dokumentów, Otwórz w danym momencie.

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
Szablon służący do dokumentów interfejsu pojedynczego dokumentu (SDI). Aplikacje SDI mają tylko jeden dokument, Otwórz w danym momencie.

## <a name="related-class"></a>Klasy pokrewne

[CCreateContext](../mfc/reference/ccreatecontext-structure.md)<br/>
Struktura przekazywane przez szablon dokumentu do funkcji tworzenia okna do koordynowania Tworzenie obiektów dokumentu, widoku i ramki okna.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)


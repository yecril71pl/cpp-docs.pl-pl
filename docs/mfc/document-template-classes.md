---
title: Klasy szablonów dokumentów
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: 2589bc8f04e791f73529af91ffb148c2c717cd08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164992"
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

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../mfc/class-library-overview.md)

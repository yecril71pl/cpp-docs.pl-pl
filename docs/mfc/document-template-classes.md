---
title: Klasy szablonów dokumentów
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: 82b9ce4c242df7c85ada0722b2c1e993a0cf3f81
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446914"
---
# <a name="document-template-classes"></a>Klasy szablonów dokumentów

Obiekty szablonu dokumentu koordynują Tworzenie obiektów dokumentów, widoków i okien ramowych podczas tworzenia nowego dokumentu lub widoku.

[CDocTemplate](../mfc/reference/cdoctemplate-class.md)<br/>
Klasa bazowa dla szablonów dokumentów. Nigdy nie będziesz używać tej klasy bezpośrednio; Zamiast tego należy użyć jednej z innych klas szablonów dokumentu pochodnych od tej klasy.

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
Szablon dokumentów w interfejsie wielu dokumentów (MDI). Aplikacje MDI mogą mieć otwarte jednocześnie wiele dokumentów.

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
Szablon dokumentów w interfejsie pojedynczego dokumentu (SDI). Aplikacje SDI mają otwarty tylko jeden dokument w danym momencie.

## <a name="related-class"></a>Klasy pokrewne

[CCreateContext](../mfc/reference/ccreatecontext-structure.md)<br/>
Struktura przenoszona przez szablon dokumentu do funkcji tworzenia okna w celu koordynowania tworzenia obiektów dokumentów, widoków i okien ramowych.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)

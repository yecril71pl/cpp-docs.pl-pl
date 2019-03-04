---
title: Drukowanie i podgląd wydruku
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
ms.openlocfilehash: 4ca6663aefce219fad4d2e3be74215d2a78206a8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263666"
---
# <a name="printing-and-print-preview"></a>Drukowanie i podgląd wydruku

Biblioteka MFC obsługuje drukowanie i Podgląd wydruku dla dokumentów programu za pomocą klasy [CView](../mfc/reference/cview-class.md). Dla podstawowych drukowania i podglądu wydruku, po prostu zastąpić klasy widoku [OnDraw](../mfc/reference/cview-class.md#ondraw) funkcji członkowskiej, co należy zrobić, mimo to. Tę funkcję można rysować na widok na ekranie, aby drukarki kontekst urządzenia dla właściwa drukarka, lub do kontekstu urządzenia, która symuluje drukarki na ekranie.

Można również dodać kod, aby zarządzać drukowanie dokumentów wielostronicowych i w wersji zapoznawczej, stronicowanie drukowanych dokumentów i dodawanie nagłówków i stopek do nich.

Tej rodziny artykułów opisano, jak drukowanie jest zaimplementowane w bibliotece Microsoft Foundation Class Library (MFC) oraz korzystać z zalet Architektura drukowania, które są wbudowane w platformę. Artykuły wyjaśniono również, jak biblioteka MFC obsługuje łatwa implementacja funkcji podglądu wydruku i jak można używać i modyfikować tę funkcję.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Drukowanie](../mfc/printing.md)

- [Architektura podglądu wydruku](../mfc/print-preview-architecture.md)

- [Próbki](../visual-cpp-samples.md)

## <a name="see-also"></a>Zobacz także

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)

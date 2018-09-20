---
title: Drukowanie i Podgląd wydruku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9aad5c69f6466ea8803cb466c5e5529f3dce1340
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374456"
---
# <a name="printing-and-print-preview"></a>Drukowanie i podgląd wydruku

Biblioteka MFC obsługuje drukowanie i Podgląd wydruku dla dokumentów programu za pomocą klasy [CView](../mfc/reference/cview-class.md). Dla podstawowych drukowania i podglądu wydruku, po prostu zastąpić klasy widoku [OnDraw](../mfc/reference/cview-class.md#ondraw) funkcji członkowskiej, co należy zrobić, mimo to. Tę funkcję można rysować na widok na ekranie, aby drukarki kontekst urządzenia dla właściwa drukarka, lub do kontekstu urządzenia, która symuluje drukarki na ekranie.

Można również dodać kod, aby zarządzać drukowanie dokumentów wielostronicowych i w wersji zapoznawczej, stronicowanie drukowanych dokumentów i dodawanie nagłówków i stopek do nich.

Tej rodziny artykułów opisano, jak drukowanie jest zaimplementowane w bibliotece Microsoft Foundation Class Library (MFC) oraz korzystać z zalet Architektura drukowania, które są wbudowane w platformę. Artykuły wyjaśniono również, jak biblioteka MFC obsługuje łatwa implementacja funkcji podglądu wydruku i jak można używać i modyfikować tę funkcję.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Drukowanie](../mfc/printing.md)

- [Architektura podglądu wydruku](../mfc/print-preview-architecture.md)

- [Próbki](../visual-cpp-samples.md)

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)

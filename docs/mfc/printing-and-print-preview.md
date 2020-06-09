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
ms.openlocfilehash: 26ced8172a36d34883d6b65997bb3a81fdc3c319
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625280"
---
# <a name="printing-and-print-preview"></a>Drukowanie i podgląd wydruku

MFC obsługuje drukowanie i Podgląd wydruku dokumentów programu za pośrednictwem klasy [CView](reference/cview-class.md). W przypadku drukowania podstawowego i podglądu wydruku wystarczy przesłonić funkcję członkowską [OnDraw](reference/cview-class.md#ondraw) klasy widoku, którą należy wykonać mimo to. Ta funkcja może narysować do widoku na ekranie, do kontekstu urządzenia drukarki dla rzeczywistej drukarki lub do kontekstu urządzenia, który symuluje drukarkę na ekranie.

Możesz również dodać kod, aby zarządzać dokumentami wielostronicowymi i wersjami zapoznawczymi, podzielić się na strony drukowanymi dokumentami oraz dodać do nich nagłówki i stopki.

W tej rodzinie artykułów wyjaśniono, jak drukowanie jest zaimplementowane w biblioteka MFC (MFC) i jak korzystać z architektury drukowania już wbudowanej w platformę. W tych artykułach wyjaśniono również, jak MFC obsługuje łatwą implementację funkcji Podgląd wydruku oraz jak można ich używać i modyfikować.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Drukowanie](printing.md)

- [Architektura podglądu wydruku](print-preview-architecture.md)

- [Przykład](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](user-interface-elements-mfc.md)

---
title: Drukowanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e03e750941be02385ac4d5b7463d5b6f32997b6a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373951"
---
# <a name="printing"></a>Drukowanie

Program Microsoft Windows implementuje wyświetlania niezależnych od urządzenia. W MFC, oznacza to, że ten sam wywołania rysowania, w `OnDraw` funkcji składowej klasy widoku, odpowiedzialność za rysunek na ekranie, a także na innych urządzeniach, takie jak drukarki. Podgląd wydruku urządzenie docelowe jest symulowane wydruk do wyświetlenia.

##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> Twoja rola w drukowaniu, a w ramach roli

Klasa widoku ma następujące obowiązki:

- Poinformuj platformę liczbę stron znajdują się w dokumencie.

- Po wyświetleniu monitu, aby wydrukować stronę na określonym, narysuj część dokumentu.

- Przydzielanie i Cofnij Przydział czcionek, lub inne zasoby interface (GDI) urządzenia grafiki potrzeby związane z drukowaniem.

- Jeśli to konieczne, Wyślij dowolny znak ucieczki kody potrzebne, aby zmienić tryb drukarki przed wydrukowaniem danej strony, na przykład, aby zmienić orientację drukowania na zasadzie na stronie.

Obowiązki struktury są następujące:

- Wyświetlanie **drukowania** okno dialogowe.

- Tworzenie [CDC](../mfc/reference/cdc-class.md) obiekt do drukarki.

- Wywołaj [StartDoc](../mfc/reference/cdc-class.md#startdoc) i [EndDoc](../mfc/reference/cdc-class.md#enddoc) funkcje elementów członkowskich `CDC` obiektu.

- Wielokrotne wywołania [StartPage](../mfc/reference/cdc-class.md#startpage) funkcji składowej typu `CDC` obiektu informuje klasa widoku strony, na które mają być drukowane, a następnie wywołaj [EndPage](../mfc/reference/cdc-class.md#endpage) funkcji składowej typu `CDC` obiektu.

- Wywoływanie funkcji możliwym do zastąpienia w widoku w odpowiednim czasie.

W następujących artykułach omówiono, jak platforma obsługuje drukowanie i Podgląd wydruku:

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Jak jest wykonywane Drukowanie domyślne](../mfc/how-default-printing-is-done.md)

- [Dokumenty wielostronicowe](../mfc/multipage-documents.md)

- [Nagłówki i stopki](../mfc/headers-and-footers.md)

- [Alokowanie zasobów GDI związane z drukowaniem](../mfc/allocating-gdi-resources.md)

- [Podgląd wydruku](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>Zobacz też

[Drukowanie i podgląd wydruku](../mfc/printing-and-print-preview.md)


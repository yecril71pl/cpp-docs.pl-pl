---
title: Drukowanie
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: a46096592c9983d04d2122bfabb56ece9346c4bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371205"
---
# <a name="printing"></a>Drukowanie

System Microsoft Windows implementuje wyświetlanie niezależne od urządzenia. W MFC oznacza to, że te `OnDraw` same wywołania rysunku, w funkcji elementu członkowskiego klasy widoku, są odpowiedzialne za rysowanie na wyświetlaczu i na innych urządzeniach, takich jak drukarki. W przypadku podglądu wydruku urządzenie docelowe jest symulowanym wyjściem drukarki do wyświetlacza.

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>Twoja rola w druku a rola frameworka

Klasa widoku ma następujące obowiązki:

- Poinformuj platformę, ile stron znajduje się w dokumencie.

- Gdy zostaniesz poproszony o wydrukowanie określonej strony, narysuj tę część dokumentu.

- Przydzielanie i przydzielanie dowolnych czcionek lub innych zasobów interfejsu urządzenia graficznego (GDI) potrzebnych do drukowania.

- W razie potrzeby przed wydrukowaniem danej strony należy wysłać kody unikowe potrzebne do zmiany trybu drukarki, na przykład w celu zmiany orientacji drukowania na stronie.

Zakres odpowiedzialności ram jest następujący:

- Wyświetl okno dialogowe **Drukowanie.**

- Utwórz obiekt [CDC](../mfc/reference/cdc-class.md) dla drukarki.

- Wywołanie funkcji elementu członkowskiego [StartDoc](../mfc/reference/cdc-class.md#startdoc) `CDC` i [EndDoc](../mfc/reference/cdc-class.md#enddoc) obiektu.

- Wielokrotnie wywołać funkcję elementu członkowskiego `CDC` [StartPage](../mfc/reference/cdc-class.md#startpage) obiektu, poinformować klasę widoku, która strona powinna być `CDC` wydrukowana, i wywołać [endpage](../mfc/reference/cdc-class.md#endpage) funkcji elementu członkowskiego obiektu.

- Wywołać zastępowalne funkcje w widoku w odpowiednim czasie.

W poniższych artykułach omówiono sposób, w jaki struktura obsługuje drukowanie i drukowanie wersji zapoznawczej:

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Jak odbywa się drukowanie domyślne](../mfc/how-default-printing-is-done.md)

- [Dokumenty wielostronicowe](../mfc/multipage-documents.md)

- [Nagłówki i stopki](../mfc/headers-and-footers.md)

- [Przydzielanie zasobów GDI do drukowania](../mfc/allocating-gdi-resources.md)

- [Podgląd wydruku](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>Zobacz też

[Drukowanie i podgląd wydruku](../mfc/printing-and-print-preview.md)

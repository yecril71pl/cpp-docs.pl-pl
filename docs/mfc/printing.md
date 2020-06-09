---
title: Drukowanie
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: 3d2ef494be66171cbcbf2b8b9e19c29c8bdc5c2f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619804"
---
# <a name="printing"></a>Drukowanie

System Microsoft Windows implementuje ekran niezależny od urządzenia. W MFC oznacza to, że te same wywołania rysowania, w `OnDraw` funkcji składowej klasy widoku, są odpowiedzialne za rysowanie na ekranie i na innych urządzeniach, takich jak drukarki. W przypadku wersji zapoznawczej drukowania urządzenie docelowe jest symulowanym wyjściem drukarki do ekranu.

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>Rola w programie drukowania a rola struktury

Klasa widoku ma następujące obowiązki:

- Poinformuj strukturę, ile stron znajduje się w dokumencie.

- Gdy zostanie wyświetlony monit o wydrukowanie określonej strony, narysuj tę część dokumentu.

- Przydzielanie i cofanie alokacji wszelkich czcionek lub innych zasobów interfejsu graficznego (GDI) wymaganych do drukowania.

- W razie potrzeby Wyślij wszelkie Kody ucieczki potrzebne do zmiany trybu drukarki przed drukowaniem danej strony, na przykład, aby zmienić orientację drukowania dla poszczególnych stron.

Obowiązki struktury są następujące:

- Wyświetl okno dialogowe **Drukowanie** .

- Utwórz obiekt [przechwytywania](reference/cdc-class.md) zmian dla drukarki.

- Wywołaj funkcje członkowskie [StartDoc](reference/cdc-class.md#startdoc) i [EndDoc](reference/cdc-class.md#enddoc) `CDC` obiektu.

- Wielokrotnie Wywołaj [StartPage](reference/cdc-class.md#startpage) funkcję elementu członkowskiego StartPage `CDC` obiektu, poinformuj klasę widoku, którą stronę należy wydrukować, i Wywołaj [EndPage](reference/cdc-class.md#endpage) funkcję elementu członkowskiego EndPage `CDC` obiektu.

- Wywołaj funkcje zamiarowe w widoku w odpowiednim czasie.

W poniższych artykułach omówiono, jak struktura obsługuje drukowanie i Podgląd wydruku:

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Jak odbywa się drukowanie domyślne](how-default-printing-is-done.md)

- [Dokumenty wielostronicowe](multipage-documents.md)

- [Nagłówki i stopki](headers-and-footers.md)

- [Alokowanie zasobów GDI do drukowania](allocating-gdi-resources.md)

- [Podgląd wydruku](print-preview-architecture.md)

## <a name="see-also"></a>Zobacz też

[Drukowanie i podgląd wydruku](printing-and-print-preview.md)

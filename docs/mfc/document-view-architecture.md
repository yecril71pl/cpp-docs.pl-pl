---
title: Architektury dokumentu widoku
ms.date: 11/19/2018
helpviewer_keywords:
- CView class [MFC], view architecture
- CDocument class [MFC]
- MFC, views
- views [MFC], MFC document/view model
- document objects [MFC]
- document objects [MFC], MFC document/view model
- MFC, documents
- documents [MFC], MFC document/view model
- document objects [MFC], document/view architecture
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
ms.openlocfilehash: ec933d29474695c1b94b72e712d68a9b3a08bd4e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326585"
---
# <a name="documentview-architecture"></a>Architektura dokument/widok

Domyślnie Kreator aplikacji MFC tworzy szkielet aplikacji za pomocą klasy dokumentów i klasa widoku. MFC oddziela zarządzania danymi na te dwie klasy. Dokument przechowuje dane i zarządza drukowanie danych i służy do koordynowania aktualizowanie wielu widoków danych. Widok przedstawia dane i zarządza nimi interakcji użytkownika z nim, w tym wybór i edytowania.

W tym modelu obiektu dokumentu MFC odczytuje i zapisuje dane w magazynie trwałym. Dokument mogą również zawierać interfejs z danymi, wszędzie tam, gdzie znajduje się on (na przykład w bazie danych). Obiekt osobny widok zarządza wyświetlania danych z renderowania danych w oknie na wybór użytkownika i edytowanie danych. Widok, uzyskuje dostęp do wyświetlania danych z dokumentu i komunikuje się w dokumencie wszelkie zmiany danych.

Chociaż można łatwo zastąpić lub zignorować separacji dokument/widok, istnieją istotnych powodów do wykonania tego modelu w większości przypadków. Jest jednym z najlepszych, gdy będziesz potrzebować wielu widoków tego samego dokumentu, takie jak arkusz kalkulacyjny i widoku wykresu. Model dokument/widok umożliwia obiekt osobny widok reprezentują każdego widoku danych, podczas wspólnego kodu do wszystkich widoków (takich jak aparat obliczeń) może znajdować się w dokumencie. Dokument również przejmuje zadania aktualizowania wszystkich widoków zmianie danych.

Architektury dokument/widok MFC sprawia, że łatwo jest obsługiwać wiele widoków, wiele typów dokumentów, okna podziału i inne funkcje przydatne interfejsu użytkownika.

Części najbardziej widoczne, zarówno dla użytkownika, jak i dla Ciebie programisty, struktura MFC są dokument i widok. Większość pracy w opracowywaniu aplikacji z architekturą przechodzi do zapisywania dokumentów i wyświetlanie klas. Rodzina tego artykułu opisano:

- Celów dokumentów i widoków oraz sposobu interakcji w ramach.

- Co należy zrobić, aby ich wykonania.

Serce dokument/widok przedstawiono cztery klucza klasy:

[CDocument](../mfc/reference/cdocument-class.md) (lub [COleDocument](../mfc/reference/coledocument-class.md)) klasa obsługuje obiekty używane do przechowywania lub kontroli programu danych i zapewnia podstawowe funkcje dla klas dokumentów zdefiniowanych przez programistę. Dokument reprezentuje jednostkę danych użytkownik zwykle zostanie otwarty przy użyciu polecenia Otwórz menu Plik i zapisuje za pomocą polecenia Zapisz w menu Plik.

[CView](../mfc/reference/cview-class.md) (lub jeden z wielu klas pochodnych) udostępnia podstawowe funkcje dla klas widoków zdefiniowanych przez programistę. Widok jest dołączony do dokumentu i działa jako pośrednik między dokumentem i użytkownikiem: widok renderuje obraz dokumentu na ekranie i interpretuje dane wejściowe użytkownika jako operacje na dokumencie. Widok Ponadto renderuje obraz dla zarówno drukowania i podglądu wydruku.

[CFrameWnd](../mfc/reference/cframewnd-class.md) (lub jeden z jego odmiany) obsługuje obiekty, które zapewnia ramkę wokół jednego lub wielu widoków dokumentu.

[CDocTemplate](../mfc/reference/cdoctemplate-class.md) (lub [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) lub [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)) obsługuje obiekt, który koordynuje jeden lub więcej istniejących dokumentów danego typu i zarządza, tworząc poprawny dokument, widoku i ramki okna obiektów dla tego typu.

Na poniższej ilustracji przedstawiono relację między dokumentem i jej widok.

![Widok jest częścią dokumentu, który jest wyświetlany](../mfc/media/vc379n1.gif "widok jest częścią dokumentu, który jest wyświetlany") <br/>
Dokument i widok

Implementacja dokument/widok w bibliotece klas oddziela dane z jego wyświetlania i użytkownika operacje na danych. Wszystkie zmiany danych są zarządzane za pośrednictwem klasy dokumentu. Widok wywołuje dostępu i zaktualizować dane w tym interfejsie.

Dokumenty, ich skojarzone widoków i ramki okna widoki są tworzone przez szablon dokumentu. Szablon dokumentu, który jest odpowiedzialny za tworzenie i zarządzanie nimi wszystkich dokumentów typu dokumentu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Portret architektury dokument/widok](../mfc/a-portrait-of-the-document-view-architecture.md)

- [Zalety architektury dokument/widok](../mfc/advantages-of-the-document-view-architecture.md)

- [Dokument i Widok klas tworzone przez Kreatora aplikacji](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [Alternatywy dla architektury dokument/widok](../mfc/alternatives-to-the-document-view-architecture.md)

- [Dodawanie wielu widoków do pojedynczego dokumentu](../mfc/adding-multiple-views-to-a-single-document.md)

- [Używanie dokumentów](../mfc/using-documents.md)

- [Używanie widoków](../mfc/using-views.md)

- [Wiele typów dokumentów, widoków i okien ramowych](../mfc/multiple-document-types-views-and-frame-windows.md)

- [Inicjowanie i oczyszczanie dokumentów i widoków](../mfc/initializing-and-cleaning-up-documents-and-views.md)

- [Inicjowanie własne dodatki do dokumentu i Widok klas](../mfc/creating-new-documents-windows-and-views.md)

- [Używanie klas baz danych z dokumentami i widokami](../data/mfc-using-database-classes-with-documents-and-views.md)

- [Używanie klas baz danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md)

- [Przykłady](../visual-cpp-samples.md)

## <a name="see-also"></a>Zobacz także

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)<br/>
[Windows](../mfc/windows.md)<br/>
[Okna ramowe](../mfc/frame-windows.md)<br/>
[Szablony dokumentów i proces tworzenia dokumentu/widoku](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)<br/>
[Tworzenie nowych dokumentów, okien i widoków](../mfc/creating-new-documents-windows-and-views.md)

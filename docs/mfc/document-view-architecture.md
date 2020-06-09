---
title: Architektura dokumentu-widoku
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
ms.openlocfilehash: a74aeba651d385cf3a5386e94ec20e4e56b7cd57
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624788"
---
# <a name="documentview-architecture"></a>Architektura dokument/widok

Domyślnie Kreator aplikacji MFC tworzy szkielet aplikacji z klasą dokumentu i klasą widoku. MFC oddziela zarządzanie danymi do tych dwóch klas. Dokument przechowuje dane i zarządza drukowaniem danych i koordynuje aktualizację wielu widoków danych. Widok wyświetla dane i zarządza interakcją z użytkownikiem, z uwzględnieniem zaznaczania i edytowania.

W tym modelu obiekt dokumentu MFC odczytuje i zapisuje dane w magazynie trwałym. Dokument może również dostarczyć interfejs do danych w dowolnym miejscu, w którym się znajduje (na przykład w bazie danych). Oddzielny obiekt widoku zarządza wyświetlaniem danych, ponieważ renderuje dane w oknie do wybranych przez użytkownika i edytowania danych. Widok pobiera dane z dokumentu i powiadamia z powrotem do dokumentu o wszelkich zmianach danych.

Mimo że można łatwo przesłonić lub zignorować separację dokumentów/widoków, istnieją atrakcyjne przyczyny tego modelu w większości przypadków. Jednym z najlepszych jest, gdy potrzebujesz wielu widoków tego samego dokumentu, takich jak arkusz kalkulacyjny i widok wykresu. Model dokumentu/widoku umożliwia osobny obiekt widoku reprezentujący każdy widok danych, podczas gdy kod wspólnych dla wszystkich widoków (takich jak aparat obliczeniowy) może znajdować się w dokumencie. Dokument pobiera również zadania aktualizowania wszystkich widoków za każdym razem, gdy zmieniają się dane.

Architektura dokumentu/widoku MFC ułatwia obsługę wielu widoków, wielu typów dokumentów, okien rozdzielacza i innych cennych funkcji interfejsu użytkownika.

Części platformy MFC, które są najbardziej widoczne zarówno dla użytkownika, jak i dla Ciebie, programista, to dokument i widok. Większość pracy w tworzeniu aplikacji za pomocą struktury polega na pisaniu dokumentów i klas widoków. W tym artykule opisano:

- Cele dokumentów i widoków oraz sposób ich działania w strukturze.

- Co należy zrobić, aby je wdrożyć.

Na początku dokumentu/widoku są cztery kluczowe klasy:

Klasa [CDocument](reference/cdocument-class.md) (lub [COleDocument](reference/coledocument-class.md)) obsługuje obiekty używane do przechowywania i kontrolowania danych programu i zapewnia podstawowe funkcje dla klas dokumentów zdefiniowanych przez programistę. Dokument reprezentuje jednostkę danych, którą użytkownik zazwyczaj otwiera, za pomocą polecenia Otwórz w menu plik i zapisuje przy użyciu polecenia Zapisz w menu plik.

[CView](reference/cview-class.md) (lub jedna z wielu klas pochodnych) oferuje podstawowe funkcje dla klas widoków zdefiniowanych przez programistę. Widok jest dołączony do dokumentu i działa jako pośrednik między dokumentem a użytkownikiem: widok renderuje obraz dokumentu na ekranie i interpretuje dane wejściowe użytkownika jako operacje na dokumencie. Widok służy również do renderowania obrazu dla drukowania i podglądu wydruku.

[Obiektu CFrameWnd](reference/cframewnd-class.md) (lub jedna z jej odmian) obsługuje obiekty, które udostępniają ramkę wokół jednego lub kilku widoków dokumentu.

[CDocTemplate](reference/cdoctemplate-class.md) (lub [CSingleDocTemplate](reference/csingledoctemplate-class.md) lub [CMultiDocTemplate](reference/cmultidoctemplate-class.md)) obsługuje obiekt, który koordynuje jeden lub więcej istniejących dokumentów danego typu i zarządza tworzeniem poprawnych obiektów dokumentów, widoków i okien ramowych dla tego typu.

Poniższy rysunek przedstawia relację między dokumentem a jego widokiem.

![Widok jest częścią wyświetlanego dokumentu](../mfc/media/vc379n1.gif "Widok jest częścią wyświetlanego dokumentu") <br/>
Dokument i widok

Implementacja dokumentu/widoku w bibliotece klas oddziela same dane od ich wyświetlania i od operacji użytkownika na danych. Wszystkie zmiany danych są zarządzane za pomocą klasy dokumentu. Widok wywołuje ten interfejs, aby uzyskać dostęp do danych i je zaktualizować.

Dokumenty, skojarzone z nimi widoki i okna ramowe, które są tworzone przez tę ramkę przez szablon dokumentu. Szablon dokumentu jest odpowiedzialny za tworzenie i zarządzanie wszystkimi dokumentami jednego typu dokumentu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Pionowa architektura dokumentu/widoku](a-portrait-of-the-document-view-architecture.md)

- [Zalety architektury dokument/widok](advantages-of-the-document-view-architecture.md)

- [Klasy dokumentów i widoków tworzone przez Kreatora aplikacji](document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [Alternatywy dla architektury dokumentu/widoku](alternatives-to-the-document-view-architecture.md)

- [Dodawanie wielu widoków do pojedynczego dokumentu](adding-multiple-views-to-a-single-document.md)

- [Używanie dokumentów](using-documents.md)

- [Używanie widoków](using-views.md)

- [Wiele typów dokumentów, widoków i okien ramowych](multiple-document-types-views-and-frame-windows.md)

- [Inicjowanie i oczyszczanie dokumentów i widoków](initializing-and-cleaning-up-documents-and-views.md)

- [Inicjowanie własnych dodatków do & Documents View Classes](creating-new-documents-windows-and-views.md)

- [Używanie klas baz danych z dokumentami i widokami](../data/mfc-using-database-classes-with-documents-and-views.md)

- [Używanie klas baz danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md)

- [Samples](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](user-interface-elements-mfc.md)<br/>
[Windows](windows.md)<br/>
[Okna ramowe](frame-windows.md)<br/>
[Szablony dokumentów i proces tworzenia dokumentu/widoku](document-templates-and-the-document-view-creation-process.md)<br/>
[Tworzenie dokumentu/widoku](document-view-creation.md)<br/>
[Tworzenie nowych dokumentów, okien i widoków](creating-new-documents-windows-and-views.md)

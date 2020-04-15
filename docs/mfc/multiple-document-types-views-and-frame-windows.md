---
title: Wiele typów dokumentów, widoków i okien ramowych
ms.date: 11/19/2018
helpviewer_keywords:
- static splitter windows [MFC]
- multiple views [MFC]
- multiple document types [MFC]
- multiple views [MFC], frame windows
- document classes [MFC], multiple
- documents [MFC], multiple types of
- splitter windows [MFC], dynamic
- dynamic splitter windows [MFC]
- windows [MFC], dynamic splitter
- windows [MFC], static splitter
- multiple frame windows [MFC]
- splitter windows [MFC], static
ms.assetid: c6b9e4e0-7c9c-45f1-a804-aeac39c9a128
ms.openlocfilehash: 5d8cec0a4ba1580e7ac5fb0e3b81052de08223fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370720"
---
# <a name="multiple-document-types-views-and-frame-windows"></a>Wiele typów dokumentów, widoków i okien ramowych

Standardowa relacja między dokumentem, jego widokiem i jego oknem ramki jest opisana w [dokumencie/utworzeniu widoku](../mfc/document-view-creation.md). Wiele aplikacji obsługuje jeden typ dokumentu (ale prawdopodobnie wiele otwartych dokumentów tego typu) z jednym widokiem w dokumencie i tylko jednym oknem ramki na dokument. Ale niektóre aplikacje mogą wymagać zmiany jednego lub więcej z tych wartości domyślnych.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Wiele typów dokumentów](#_core_multiple_document_types)

- [Wiele widoków](#_core_multiple_views)

- [Wiele okien ramek](#_core_multiple_frame_windows)

- [Okna rozdzielacza](#_core_splitter_windows)

## <a name="multiple-document-types"></a><a name="_core_multiple_document_types"></a>Wiele typów dokumentów

Kreator aplikacji MFC tworzy dla Ciebie klasę pojedynczego dokumentu. W niektórych przypadkach jednak może być konieczne obsługiwanie więcej niż jednego typu dokumentu. Na przykład aplikacja może wymagać dokumentów arkusza i wykresu. Każdy typ dokumentu jest reprezentowany przez własną klasę dokumentu i prawdopodobnie przez własną klasę widoku. Gdy użytkownik wybierze polecenie Plik nowy, w ramach zostanie wyświetlone okno dialogowe z listą obsługiwanych typów dokumentów. Następnie tworzy dokument typu, który użytkownik wybiera. Każdy typ dokumentu jest zarządzany przez własny obiekt szablonu dokumentu.

Aby utworzyć dodatkowe klasy dokumentów, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md). Wybierz [CDocument](../mfc/reference/cdocument-class.md) jako typ klasy, aby pochodzić z żądanych informacji o dokumencie i podać je. Następnie zaimplementuj dane nowej klasy.

Aby poinformować strukturę o dodatkowej klasie dokumentu, należy dodać drugie [wywołanie addDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) w zastąpień [initinstance](../mfc/reference/cwinapp-class.md#initinstance) klasy aplikacji. Aby uzyskać więcej informacji, zobacz [Szablony dokumentów](../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="multiple-views"></a><a name="_core_multiple_views"></a>Wiele widoków

Wiele dokumentów wymaga tylko jednego widoku, ale możliwe jest obsługę więcej niż jednego widoku pojedynczego dokumentu. Aby ułatwić implementowanie wielu widoków, obiekt dokumentu przechowuje listę jego widoków, udostępnia funkcje członkowskie do dodawania i usuwania widoków i udostępnia [updateAllViews](../mfc/reference/cdocument-class.md#updateallviews) funkcji elementu członkowskiego do poinformowania wielu widoków, gdy dane dokumentu uległy zmianie.

MFC obsługuje trzy typowe interfejsy użytkownika wymagające wielu widoków w tym samym dokumencie. Modele te są następujące:

- Wyświetlanie obiektów tej samej klasy, każdy w osobnym oknie ramki dokumentu MDI.

   Można obsługiwać tworzenie drugiego okna ramki w dokumencie. Użytkownik może wybrać polecenie Nowe okno, aby otworzyć drugą ramkę z widokiem tego samego dokumentu, a następnie użyć dwóch ramek do jednoczesnego wyświetlania różnych części dokumentu. Struktura obsługuje polecenie Nowe okno w menu Okno dla aplikacji MDI przez powielanie początkowego okna ramki i widoku dołączonego do dokumentu.

- Wyświetlanie obiektów tej samej klasy w tym samym oknie ramki dokumentu.

   Okna rozdzielacza dzielą przestrzeń widoku pojedynczego okna dokumentu na wiele oddzielnych widoków dokumentu. Struktura tworzy wiele obiektów widoku z tej samej klasy widoku. Aby uzyskać więcej informacji, zobacz [Rozdzielacz systemu Windows](#_core_splitter_windows).

- Wyświetlanie obiektów różnych klas w oknie pojedynczej ramki.

   W tym modelu odmiany okna rozdzielacza wiele widoków współużytkuje jedno okno ramki. Widoki są zbudowane z różnych klas, każdy widok zapewniając inny sposób wyświetlania tego samego dokumentu. Na przykład jeden widok może wyświetlać dokument edytora tekstu w trybie normalnym, podczas gdy drugi widok pokazuje go w trybie konspektu. Formant rozdzielacza umożliwia użytkownikowi dostosowanie względnych rozmiarów widoków.

Na poniższej ilustracji, podzielonej na części a, b i c, przedstawiono trzy modele interfejsu użytkownika w kolejności przedstawionej powyżej.

![Wiele&#45;widok interfejsów użytkownika](../mfc/media/vc37a71.gif "Wiele&#45;widok interfejsów użytkownika") <br/>
Interfejsy użytkownika z wieloma widokami

Struktura zapewnia te modele, implementując polecenie Nowe okno i zapewniając klasę [CSplitterWnd](../mfc/reference/csplitterwnd-class.md), jak omówiono w [rozdzielacz systemu Windows](#_core_splitter_windows). Można zaimplementować inne modele przy użyciu tych jako punkt wyjścia. Aby zapoznać się z przykładowymi programami ilustruwuj różne konfiguracje widoków, okien ramek i rozdzielacza, zobacz [Przykłady MFC](../overview/visual-cpp-samples.md#mfc-samples).

Aby uzyskać `UpdateAllViews`więcej informacji na temat , zobacz klasę [CView](../mfc/reference/cview-class.md) w *odwołaniu MFC* i [przykładzie Bazgroły](../overview/visual-cpp-samples.md).

## <a name="multiple-frame-windows"></a><a name="_core_multiple_frame_windows"></a>Okna z wieloma ramkami

Za pomocą polecenia Nowe okno w menu Okno dla aplikacji MDI można utworzyć drugie okno ramki w tym samym dokumencie. Aby uzyskać więcej informacji, zobacz pierwszy model na rysunku Interfejsy użytkownika wielu widoków.

## <a name="splitter-windows"></a><a name="_core_splitter_windows"></a>Rozdzielacz systemu Windows

W oknie rozdzielacza okno jest lub może być podzielone na dwa lub więcej przewijanych okienek. Formant rozdzielacza (lub "pole podziału") w ramce okna obok pasków przewijania umożliwia użytkownikowi dostosowanie względnych rozmiarów okienek. Każde okienko jest widokiem w tym samym dokumencie. W rozdzielaczach "dynamicznych" widoki są tej samej klasy, jak pokazano w części b rysunku interfejsów użytkownika wielokrotnego widoku. W "statycznych" rozdzielaczy widoki mogą być z różnych klas. Okna rozdzielacza obu rodzajów są obsługiwane przez klasę [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).

Dynamiczne okna rozdzielacza z widokami tej samej klasy umożliwiają użytkownikowi dzielenie okna na wiele okienek do woli, a następnie przewijanie różnych okienek, aby wyświetlić różne części dokumentu. Użytkownik może również rozświetlić okno, aby usunąć dodatkowe widoki. Okna rozdzielacza dodane do [próbki bazgrołów](../overview/visual-cpp-samples.md) są przykładem. W tym temacie opisano technikę tworzenia okien rozdzielacza dynamicznego. Dynamiczne okno rozdzielacza jest wyświetlane w części b rysunku Interfejsy użytkownika wielokrotnego widoku.

Statyczne okna rozdzielacza, z widokami różnych klas, zaczynają się od okna podzielonego na wiele okienek, z których każdy ma inny cel. Na przykład w edytorze bitmap języka Visual C++ okno obrazu pokazuje dwa okienka obok siebie. W lewym okienku wyświetlany jest obraz mapy bitowej o żywotności. W prawym okienku wyświetlany jest powiększony lub powiększony obraz tej samej mapy bitowej. Okienka są oddzielone "pasek rozdzielacza", który użytkownik może przeciągnąć, aby zmienić względne rozmiary okienek. Statyczne okno rozdzielacza jest wyświetlane w części c rysunku Interfejsy użytkownika wielokrotnego widoku.

Aby uzyskać więcej informacji, zobacz klasę [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) w *próbkach odniesienia MFC* i [MFC](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Zobacz też

[Architektura dokumentu/widoku](../mfc/document-view-architecture.md)

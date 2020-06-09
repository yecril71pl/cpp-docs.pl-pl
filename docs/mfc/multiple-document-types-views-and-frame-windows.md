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
ms.openlocfilehash: 873903aadc1596fbc56f9a0b0b98dbc5a948113d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619968"
---
# <a name="multiple-document-types-views-and-frame-windows"></a>Wiele typów dokumentów, widoków i okien ramowych

Standardowa relacja między dokumentem, jego widokiem i oknem ramki jest opisana w temacie [Tworzenie dokumentu/widoku](document-view-creation.md). Wiele aplikacji obsługuje pojedynczy typ dokumentu (ale prawdopodobnie wiele otwartych dokumentów tego typu) z pojedynczym widokiem dokumentu i tylko jednym oknem ramki na każdy dokument. Niektóre aplikacje mogą jednak wymagać zmiany co najmniej jednego z tych ustawień domyślnych.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Wiele typów dokumentów](#_core_multiple_document_types)

- [Wiele widoków](#_core_multiple_views)

- [Wiele okien ramowych](#_core_multiple_frame_windows)

- [Okna rozdzielacza](#_core_splitter_windows)

## <a name="multiple-document-types"></a><a name="_core_multiple_document_types"></a>Wiele typów dokumentów

Kreator aplikacji MFC tworzy dla Ciebie jedną klasę dokumentu. W niektórych przypadkach może być konieczne obsługę więcej niż jednego typu dokumentu. Na przykład aplikacja może potrzebować dokumentów arkusza i wykresu. Każdy typ dokumentu jest reprezentowany przez własną klasę dokumentu i prawdopodobnie według własnej klasy widoku. Gdy użytkownik wybierze polecenie plik nowy, w strukturze zostanie wyświetlone okno dialogowe zawierające listę obsługiwanych typów dokumentów. Następnie tworzy dokument typu wybranego przez użytkownika. Każdy typ dokumentu jest zarządzany przez swój własny obiekt szablonu dokumentu.

Aby utworzyć dodatkowe klasy dokumentów, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md). Wybierz [CDocument](reference/cdocument-class.md) jako typ klasy, z której ma pochodzić i podaj żądane informacje o dokumencie. Następnie Zaimplementuj dane nowej klasy.

Aby uzyskać informacje o klasie dodatkowej dokumentu, należy dodać drugie wywołanie do [AddDocTemplate](reference/cwinapp-class.md#adddoctemplate) w zastąpieniu [InitInstance](reference/cwinapp-class.md#initinstance) klasy aplikacji. Aby uzyskać więcej informacji, zobacz [Szablony dokumentów](document-templates-and-the-document-view-creation-process.md).

## <a name="multiple-views"></a><a name="_core_multiple_views"></a>Wiele widoków

Wiele dokumentów wymaga tylko jednego widoku, ale można obsługiwać więcej niż jeden widok pojedynczego dokumentu. Aby pomóc w zaimplementowaniu wielu widoków, obiekt dokumentu zachowuje listę widoków, udostępnia funkcje członkowskie do dodawania i usuwania widoków oraz dostarcza funkcję składową [funkcji UpdateAllViews](reference/cdocument-class.md#updateallviews) , która umożliwia wyświetlanie wielu widoków, gdy dane dokumentu uległy zmianie.

MFC obsługuje trzy popularne interfejsy użytkownika wymagające wielu widoków w tym samym dokumencie. Są to następujące modele:

- Wyświetl obiekty tej samej klasy, każdy w osobnym oknie ramki dokumentu MDI.

   Możesz chcieć obsługiwać Tworzenie drugiego okna ramki na dokumencie. Użytkownik może wybrać nowe polecenie okna, aby otworzyć drugą ramkę z widokiem tego samego dokumentu, a następnie użyć dwóch ramek, aby jednocześnie wyświetlić różne fragmenty dokumentu. Platforma obsługuje nowe okno polecenia w menu okna dla aplikacji MDI przez duplikowanie okna początkowej ramki i widoku dołączonego do dokumentu.

- Wyświetl obiekty tej samej klasy w tym samym oknie ramki dokumentu.

   Okna rozdzielacza dzielą obszar widoku pojedynczego dokumentu na wiele oddzielnych widoków dokumentu. Struktura tworzy wiele obiektów widoku z tej samej klasy widoku. Aby uzyskać więcej informacji, zobacz [rozdzielacz okna](#_core_splitter_windows).

- Wyświetl obiekty różnych klas w jednym oknie ramki.

   W tym modelu, odmiana okna rozdzielacza, wiele widoków, udostępnia pojedyncze okno klatki. Widoki są zbudowane z różnych klas, każdy widok udostępnia inny sposób wyświetlania tego samego dokumentu. Na przykład jeden widok może wyświetlić dokument przetwarzania wyrazów w trybie normalnym, podczas gdy inny widok pokazuje go w trybie konspektu. Kontrolka rozdzielacza umożliwia użytkownikowi dostosowanie względnych rozmiarów widoków.

Poniższy rysunek, podzielony na części a, b i c, pokazuje trzy modele interfejsu użytkownika w podanej kolejności.

![Wiele&#45;Wyświetl interfejsy użytkownika](../mfc/media/vc37a71.gif "Wiele&#45;Wyświetl interfejsy użytkownika") <br/>
Interfejsy użytkownika z wieloma widokami

Struktura zapewnia te modele, implementując nowe okno polecenia i dostarczając klasy [CSplitterWnd](reference/csplitterwnd-class.md), jak opisano w [oknach rozdzielacza](#_core_splitter_windows). Możesz zaimplementować inne modele, używając ich jako punktu początkowego. W przypadku przykładowych programów, które ilustrują różne konfiguracje widoków, okien ramowych i rozdzielaczy, zobacz [MFC Samples](../overview/visual-cpp-samples.md#mfc-samples).

Aby uzyskać więcej informacji na temat `UpdateAllViews` , zobacz Klasa [CView](reference/cview-class.md) w *dokumentacji MFC* i [przykładu bazgrołów](../overview/visual-cpp-samples.md).

## <a name="multiple-frame-windows"></a><a name="_core_multiple_frame_windows"></a>Wiele okien ramowych

Możesz użyć nowego okna polecenie w menu okno dla aplikacji MDI do utworzenia drugiego okna ramki w tym samym dokumencie. Aby uzyskać więcej informacji, zapoznaj się z pierwszym modelem na rysunku interfejs użytkownika z wieloma widokami.

## <a name="splitter-windows"></a><a name="_core_splitter_windows"></a>Okna rozdzielacza

W oknie rozdzielacza okno jest lub może być podzielone na co najmniej dwa okienka przewijane. Kontrolka rozdzielacza (lub pole podziału) w ramce okna obok pasków przewijania umożliwia użytkownikowi dostosowanie względnych rozmiarów okienek. Wszystkie okienka są widokami tego samego dokumentu. W przypadku rozdzielaczy "dynamiczny" widoki są tej samej klasy, jak pokazano w części b rysunku interfejsy użytkownika z wieloma widokami. W przypadku rozdzielaczy "static" widoki mogą być różne. Okna rozdzielacza obu rodzajów są obsługiwane przez klasę [CSplitterWnd](reference/csplitterwnd-class.md).

Dynamiczne okna podziału, z widokami tej samej klasy, Zezwalaj użytkownikowi na dzielenie okna na wiele okienek w programie, a następnie przewiń różne okienka, aby zobaczyć różne części dokumentu. Użytkownik może także rozdzielić okno, aby usunąć dodatkowe widoki. W przykładzie rozdzielacza dodany do [przykładu bazgrołów](../overview/visual-cpp-samples.md) jest przykładem. W tym temacie opisano technikę tworzenia dynamicznych okien rozdzielacza. Dynamiczne okno rozdzielacza jest wyświetlane w części b rysunku interfejsy użytkownika z wieloma widokami.

Statyczne okna podziału, z widokami różnych klas, Rozpocznij od podziału okna do wielu okienek, z których każdy ma inny cel. Na przykład w edytorze mapy bitowej Visual C++ okno obraz przedstawia dwa okienka obok siebie. W okienku po lewej stronie jest wyświetlany obraz rozmiaru dla mapy bitowej. W okienku po prawej stronie jest wyświetlany powiększony lub powiększony obraz tej samej mapy bitowej. Okienka są oddzielone "paskiem podziału", które użytkownik może przeciągnąć, aby zmienić względne rozmiary okienek. Statyczne okno rozdzielacza jest wyświetlane w części c rysunku interfejsy użytkownika z wieloma widokami.

Aby uzyskać więcej informacji, zobacz Klasa [CSplitterWnd](reference/csplitterwnd-class.md) w *dokumentacji MFC* i [przykładach MFC](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Zobacz też

[Architektura dokumentu/widoku](document-view-architecture.md)

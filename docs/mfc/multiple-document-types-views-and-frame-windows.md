---
title: Wiele typów dokumentów, widoków i ramek Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a488a3d46d60762f73406ea6f604761804277aa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429776"
---
# <a name="multiple-document-types-views-and-frame-windows"></a>Wiele typów dokumentów, widoków i okien ramowych

Standardowa relacji między dokumentem, jej widok oraz jego ramki okna jest opisana w [tworzenia dokumentu/widoku](../mfc/document-view-creation.md). Wiele aplikacji obsługuje pojedynczego dokumentu typu (ale prawdopodobnie wiele otwarte dokumenty tego typu) z jednym widokiem dokumentu i tylko jeden ramki okna dla dokumentu. Jednak niektóre aplikacje muszą zmieniać co najmniej jedną z tych wartości domyślnych.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Typy dokumentów wielokrotnych](#_core_multiple_document_types)

- [Wiele widoków](#_core_multiple_views)

- [Wiele okien ramowych](#_core_multiple_frame_windows)

- [Okna podziału](#_core_splitter_windows)

##  <a name="_core_multiple_document_types"></a> Typy dokumentów wielokrotnych

Kreator aplikacji MFC tworzy klasę pojedynczego dokumentu. Jednak w niektórych przypadkach może być konieczne obsługuje więcej niż jeden typ dokumentu. Na przykład aplikacja może być konieczne dokumenty arkuszy i wykresów. Każdy typ dokumentu jest reprezentowany przez własną klasy dokumentów i prawdopodobnie własnej klasy widoku. Gdy użytkownik wybierze polecenie Nowy plik, struktura Wyświetla okno dialogowe, które zawiera listę typów obsługiwanych dokumentu. Następnie tworzy dokument, gdy użytkownik wybierze typu. Każdy typ dokumentu jest zarządzany przez obiekt swój własny szablon dokumentu.

Aby utworzyć klasy dodatkowych dokumentów, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md). Wybierz [CDocument](../mfc/reference/cdocument-class.md) jako typ klasy pochodzi od i podać informacje żądany dokument. Następnie można wdrożyć nową klasę danych.

Aby umożliwić framework klasy dodatkowych dokumentów można dowiedzieć się, należy dodać drugie wywołanie [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) w klasie aplikacji [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) zastąpienia. Aby uzyskać więcej informacji, zobacz [szablonów dokumentów](../mfc/document-templates-and-the-document-view-creation-process.md).

##  <a name="_core_multiple_views"></a> Wiele widoków

Wiele dokumentów wymaga tylko pojedynczy widok, ale istnieje możliwość obsługi więcej niż jeden widok pojedynczego dokumentu. Aby ułatwić wdrożenie wielu widoków, obiekt dokumentu przechowuje listę widokach, dostarcza funkcji elementów członkowskich do dodawania i usuwania widoków i dostarcza [funkcji UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) funkcję członkowską umożliwienie wielu widoków wiedział, kiedy dane dokumentu został zmieniony.

Biblioteka MFC obsługuje trzy wspólnych interfejsów użytkownika wymagających wielu widoków do tego samego dokumentu. Te modele są:

- Pokaż obiekty tej samej klasy, każdy w osobnym oknie ramki dokumentu MDI.

     Możesz chcieć obsługują tworzenie drugiego okna ramki dokumentu. Użytkownik może wybrać polecenie nowe okno, aby otworzyć drugiego ramki pod kątem tego samego dokumentu, a następnie użyć dwóch ramek, aby jednocześnie wyświetlić różne części dokumentu. Platforma obsługuje polecenie nowe okno w menu Okno dla aplikacji MDI, duplikując początkowej ramki okna i widoku dołączony do dokumentu.

- Pokaż obiekty tej samej klasy, w tym samym oknie ramki dokumentu.

     Okna podziału Podziel obszar widoku okna pojedynczego dokumentu na wiele oddzielnych widoków dokumentu. Szablon tworzy wiele obiektów widoku z tej samej klasy widoku. Aby uzyskać więcej informacji, zobacz [Windows rozdzielacz](#_core_splitter_windows).

- Pokaż obiekty różnych klas w jednej ramki okna.

     W tym modelu odmianą okno rozdzielacza wielu widoków udostępnianie jednej ramki okna. Widoki są konstruowane na podstawie różnych klas poszczególnych widokach, podając inny sposób, aby wyświetlić ten sam dokument. Na przykład jeden widok może wyświetlać dokumentu edytora tekstów w trybie normalnym, a w innych widokach pojawia się w tryb konspektu. Formant Splitter — umożliwia użytkownikowi dostosowanie względne rozmiary widoków.

Poniższy rysunek podzielony na części, b i c, przedstawia trzy modele interfejsu użytkownika w kolejności, przedstawione powyżej.

![Wiele&#45;wyświetlić interfejsy użytkownika](../mfc/media/vc37a71.gif "vc37a71") widoku wielu interfejsów użytkownika

Struktura zapewnia tych modeli, implementując polecenie nowe okno i udostępnienie klasy [CSplitterWnd](../mfc/reference/csplitterwnd-class.md), zgodnie z opisem w [Windows rozdzielacz](#_core_splitter_windows). Możesz zaimplementować innych modeli przy użyciu je jako punkt początkowy. Aby uzyskać przykładowe programy, które ilustrują różne konfiguracje widoków, oknami ramek i rozdzielaczy, zobacz [próbki MFC](../visual-cpp-samples.md).

Aby uzyskać więcej informacji na temat `UpdateAllViews`, można znaleźć klasy [CView](../mfc/reference/cview-class.md) w *odwołanie MFC* i [próbki Bazgroły](../visual-cpp-samples.md).

##  <a name="_core_multiple_frame_windows"></a> Wiele Windows ramki

Polecenie nowe okno w menu Okno dla aplikacji MDI utworzyć drugi ramki okna tego samego dokumentu. Aby uzyskać więcej informacji Zobacz pierwszy model na rysunku widoku wielu interfejsów użytkownika.

##  <a name="_core_splitter_windows"></a> Splitter — Windows

Okno rozdzielacza okna jest lub można podzielić na dwie lub więcej przewijany okienka. Rozdzielacz kontrolki (lub "Podziel okno") w ramki okna obok pasków przewijania umożliwia użytkownik może dostosować względne rozmiary okienek. Każde okienko jest widok tego samego dokumentu. W "dynamiczne" rozdzielaczy widoki są tej samej klasy przedstawione w części b rysunek widoku wielu interfejsów użytkownika. W "statyczne" rozdzielaczy widoków może być różnych klas. Okna podziału obu rodzajów są obsługiwane przez klasę [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).

Dynamiczne okna podziału, za pomocą widoków tej samej klasy Zezwalaj użytkownikowi na dzielenie okna w wiele okienek z życzeniem, a następnie przewiń listę różnych okienek, aby wyświetlić różne części dokumentu. Użytkownik może także cofnąć podziału okna, aby usunąć dodatkowe widoki. Okna podziału dodane do [próbki Bazgroły](../visual-cpp-samples.md) służą jako przykład. Ten temat opisuje techniki tworzenia dynamiczne okna podziału. Dynamiczne okno rozdzielacza jest wyświetlany w części b rysunek widoku wielu interfejsów użytkownika.

Statyczne okna podziału, za pomocą widoków różnymi klasami, rozpoczynać się okna podzielić na wiele okienek, każdy z innego celu. Na przykład do edytora mapy bitowej Visual C++ okna obraz pokazuje dwa okienka obok siebie. W okienku po lewej stronie wyświetlane life-sized obraz lustrzany mapy bitowej. Prawe okienko wyświetla powiększonego lub pomniejszenie obraz lustrzany mapy bitowej, ten sam. Okienka są oddzielone "pasek podziału", który użytkownik można przeciągnąć, aby zmieniać względne rozmiary okienek. Okno statyczny rozdzielacz jest wyświetlany w części c rysunek widoku wielu interfejsów użytkownika.

Aby uzyskać więcej informacji, zobacz klasy [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) w *odwołanie MFC* i [próbki MFC](../visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz też

[Architektura dokument/widok](../mfc/document-view-architecture.md)


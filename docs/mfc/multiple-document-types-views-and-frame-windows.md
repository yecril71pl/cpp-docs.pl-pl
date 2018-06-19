---
title: Wiele typów dokumentów, widoków i okien ramowych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5640c3bb66bee0641b0c153ae10dc146bb1c1dd8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352161"
---
# <a name="multiple-document-types-views-and-frame-windows"></a>Wiele typów dokumentów, widoków i okien ramowych
Standardowe relacji między dokumentu, jego widoku i ramki okna jest opisany w [tworzenia dokumentu/widoku](../mfc/document-view-creation.md). Wiele aplikacji obsługuje jeden dokument typu (ale prawdopodobnie wielu otwarte dokumenty tego typu) z jednego widoku na tylko jedną ramkę okna w dokumencie i dokumentów. Jednak niektóre aplikacje mogą należy zmodyfikować co najmniej jednego z tych wartości domyślnych.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Wiele typów dokumentów](#_core_multiple_document_types)  
  
-   [Wiele widoków](#_core_multiple_views)  
  
-   [Wiele okien ramowych](#_core_multiple_frame_windows)  
  
-   [Okna podziału](#_core_splitter_windows)  
  
##  <a name="_core_multiple_document_types"></a> Wiele typów dokumentów  
 Kreator aplikacji MFC utworzy klasę pojedynczego dokumentu. Jednak w niektórych przypadkach może być konieczne obsługuje więcej niż jeden typ dokumentu. Na przykład aplikacja może być konieczne dokumenty arkuszy i wykresów. Każdego typu dokumentu jest reprezentowana przez własnej klasy dokumentu i prawdopodobnie własnej klasy widoku. Gdy użytkownik wybierze polecenie Nowy plik, platformę Wyświetla okno dialogowe, który zawiera listę typów obsługiwanych dokumentu. Następnie tworzy dokumentu przez użytkownika typu. Każdy typ dokumentu jest zarządzana przez obiekt własny szablon dokumentu.  
  
 Aby utworzyć klasy dodatkowych dokumentów, zobacz [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md). Wybierz [CDocument](../mfc/reference/cdocument-class.md) jako typ klasy dziedziczyć i podawanie informacji żądanych dokumentów. Następnie można wdrożyć nową klasę danych.  
  
 Aby umożliwić framework informacje o klasie dodatkowe dokumentu, należy dodać drugie wywołanie [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) w klasie aplikacji [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) zastąpienia. Aby uzyskać więcej informacji, zobacz [szablonów dokumentów](../mfc/document-templates-and-the-document-view-creation-process.md).  
  
##  <a name="_core_multiple_views"></a> Wiele widoków  
 Wiele dokumentów wymaga tylko jednego widoku, ale istnieje możliwość obsługuje więcej niż jeden widok pojedynczego dokumentu. Ułatwiają zaimplementowanie wielu widoków, obiektu dokumentu przechowuje listę widokach, udostępnia funkcje elementów członkowskich do dodawania i usuwania widoków i dostarcza [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) funkcji członkowskiej do przekazywania wielu widoków o tym, kiedy dane dokumentu został zmieniony.  
  
 MFC obsługuje trzy wspólnych interfejsów użytkownika wymagające wielu widoków do tego samego dokumentu. Te modele są:  
  
-   Pokaż obiekty tej samej klasy każdego w osobnym oknie ramki dokumentu MDI.  
  
     Możesz chcieć obsługują tworzenie drugie okno ramowe w dokumencie. Użytkownik może wybrać polecenie nowe okno, aby otworzyć ramki drugi z widokiem tego samego dokumentu, a następnie użyć dwóch ramek do wyświetlania różnych części dokumentu jednocześnie. Platforma obsługuje nowe okno polecenia menu okna MDI — aplikacje duplikując okno ramowe początkowej i widoku dołączonym do dokumentu.  
  
-   Pokaż obiekty tej samej klasy, w tym samym oknie ramki dokumentu.  
  
     Okna podziału podzielone wiele oddzielnych widoków dokumentu miejsca widok okna pojedynczego dokumentu. Platformę tworzy wiele obiektów widoku z tej samej klasy widoku. Aby uzyskać więcej informacji, zobacz [okna podziału](#_core_splitter_windows).  
  
-   Obiekty widoku różnych klas w oknie jedną ramkę.  
  
     W tym modelu odmianą okna podziału wiele widoków udostępnianie jednej ramki okna. Widoki są tworzone na podstawie różnych klas każdego widoku, podając inny sposób, aby wyświetlić tego samego dokumentu. Na przykład jeden widok mogą być wyświetlane dokumentu edytora tekstów w normalnym trybie, podczas gdy inne widoku go w tryb konspektu. Formant rozdzielacza umożliwia użytkownik może dostosować względnych rozmiarów widoków.  
  
 Poniższa ilustracja podzielone na części, b i c, pokazuje trzy modele interfejsu użytkownika w kolejności przedstawionych powyżej.  
  
 ![Wiele&#45;wyświetlić interfejsy użytkownika](../mfc/media/vc37a71.gif "vc37a71")  
Interfejsy użytkownika wielu widoku  
  
 Platformę zawiera te modele przez zastosowanie polecenia nowe okno i zapewniając klasy [CSplitterWnd](../mfc/reference/csplitterwnd-class.md), zgodnie z opisem w [okna podziału](#_core_splitter_windows). Można zaimplementować innych modeli przy użyciu je jako punktu początkowego. Dla programów próbki, ilustrujące różne konfiguracje widoki, okien ramowych i rozdzielaczy, zobacz [MFC — przykłady](../visual-cpp-samples.md).  
  
 Aby uzyskać więcej informacji na temat `UpdateAllViews`, można znaleźć klasy [CView](../mfc/reference/cview-class.md) w *odwołania MFC* i [próbki bazgrołów](../visual-cpp-samples.md).  
  
##  <a name="_core_multiple_frame_windows"></a> Wiele okien ramowych  
 Polecenie nowe okno z menu okna MDI — aplikacje można utworzyć drugie okno ramowe na tym samym dokumencie. Aby uzyskać więcej informacji Zobacz pierwszy model na ilustracji, widok wielu interfejsów użytkownika.  
  
##  <a name="_core_splitter_windows"></a> Okna podziału  
 W oknie podziału okna jest lub można podzielić na dwa lub więcej przewijanego okienka. Podziału formantu (lub "podzielić pole") w ramki okna obok pasków przewijania umożliwia użytkownik może dostosować względną rozmiary okienka. Każde okienko jest widok na tym samym dokumencie. W "dynamiczny" rozdzielaczy widoki są tej samej klasy opisane w części b rysunek widoku wielu interfejsów użytkownika. W "statyczny" rozdzielaczy widoki mogą mieć różnych klas. Okna podziału obu rodzajów są obsługiwane przez klasę [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).  
  
 Dynamiczne okna podziału, z widokami z tej samej klasy Zezwalaj użytkownikowi na dzieli okno na okienka wiele w momencie, a następnie przewiń w różnych okienek, aby wyświetlić różne części dokumentu. Użytkownik może także cofnąć podziału okna, aby usunąć dodatkowe widoki. Okna podziału dodane do [próbki bazgrołów](../visual-cpp-samples.md) są przykładem. Ten temat zawiera opis technik tworzenia dynamiczne okna podziału. Dynamiczne okno podziału jest wyświetlany w części b rysunek widoku wielu interfejsów użytkownika.  
  
 Statyczne okna podziału, z widokami różnych klas rozpoczynać okna podzielony na wiele okienek, każde z nich innym celu. Na przykład do edytora mapy bitowej Visual C++ okna Obraz zawiera dwa okienka obok siebie. W okienku po lewej stronie wyświetlane life-sized obraz mapy bitowej. W okienku po prawej stronie wyświetlane powiększony lub powiększony obrazu z tej samej mapy bitowej. Okienka są oddzielone "pasek podziału", który użytkownik może przeciągnij, aby zmienić względną rozmiary okienka. Okno statyczny rozdzielacz jest wyświetlany w części c rysunek widoku wielu interfejsów użytkownika.  
  
 Aby uzyskać więcej informacji, zobacz klasy [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) w *odwołania MFC* i [MFC — przykłady](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura dokument/widok](../mfc/document-view-architecture.md)


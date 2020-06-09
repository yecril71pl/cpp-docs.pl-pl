---
title: Przeciąganie i upuszczanie elementów OLE
description: Przegląd Microsoft Foundation Classes (MFC) OLE — przeciąganie i upuszczanie, jak zaimplementować Źródło upuszczania, miejsce docelowe upuszczania oraz jak dostosować przeciąganie i upuszczanie.
ms.date: 02/09/2020
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
ms.openlocfilehash: 23680765377d325bdc1f8878daf4d4fc553a1304
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623186"
---
# <a name="ole-drag-and-drop"></a>Przeciąganie i upuszczanie elementów OLE

Funkcja przeciągania i upuszczania OLE jest szczególnie skrótem do kopiowania i wklejania danych. W przypadku używania schowka do kopiowania lub wklejania danych wymagane jest wykonanie kilku kroków. Wybierzesz dane, a następnie wybierz opcję **Wytnij** lub **Kopiuj** z menu **Edycja** . Następnie przejdziesz do docelowej aplikacji lub okna i umieścisz kursor w lokalizacji docelowej. Na koniec wybierz pozycję **Edytuj**  >  **Wklej** z menu.

Funkcja przeciągania i upuszczania OLE różni się od mechanizmu przeciągania i upuszczania w Menedżerze plików. Menedżer plików może obsłużyć tylko nazwy plików i został zaprojektowany specjalnie w celu przekazywania nazw plików do aplikacji. Przeciąganie i upuszczanie w OLE jest znacznie bardziej ogólne. Umożliwia przeciąganie i upuszczanie wszelkich danych, które można również umieścić w Schowku.

Przy użyciu przeciągania i upuszczania OLE należy usunąć dwa kroki z procesu. Wybierasz dane z okna źródłowego ("Drop source"), a następnie przeciągniesz je do lokalizacji docelowej ("upuść Target"). Można je usunąć, zwalniając przycisk myszy. Operacja eliminuje konieczność stosowania menu i jest szybsza niż sekwencja kopiowania/wklejania. Istnieje tylko jedno wymaganie: zarówno źródło, jak i miejsce docelowe upuszczania muszą być otwarte, a co najmniej częściowo widoczne na ekranie.

Za pomocą przeciągania i upuszczania OLE dane można łatwo przenieść z jednej lokalizacji do innej: w dokumencie, między różnymi dokumentami lub między aplikacjami. Może być zaimplementowana w aplikacji kontener lub serwer. Każda aplikacja może być źródłem Drop, elementem docelowym upuszczania lub jednocześnie. Jeśli aplikacja implementuje obsługę zarówno upuszczania, jak i upuszczania, można przeciągać i upuszczać między oknami podrzędnymi lub w jednym oknie. Ta funkcja znacznie ułatwia korzystanie z aplikacji.

W artykułach [obiekty danych i źródła danych (OLE)](data-objects-and-data-sources-ole.md) objaśniono sposób implementacji transferu danych w aplikacjach. Pomocne jest również zbadanie przykładów MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md).

## <a name="implement-a-drop-source"></a><a name="implement-a-drop-source"></a>Implementowanie źródła upuszczania

Aby aplikacja mogła dostarczać dane do operacji przeciągania i upuszczania, należy zaimplementować Źródło upuszczania. Podstawowa implementacja źródła upuszczania jest stosunkowo prosta. Pierwszym krokiem jest określenie, jakie zdarzenia rozpoczynają operację przeciągania. Zalecane wskazówki dotyczące interfejsu użytkownika definiują początek operacji przeciągania, tak jakby zdarzenie **WM_LBUTTONDOWN** występuje w punkcie wewnątrz niektórych wybranych danych. Przykłady MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md) są zgodne z tymi wskazówkami.

Jeśli aplikacja jest kontenerem, a wybrane dane są połączonym lub osadzonym obiektem typu `COleClientItem` , należy wywołać jego `DoDragDrop` funkcję członkowską. W przeciwnym razie Utwórz `COleDataSource` obiekt, zainicjuj go za pomocą zaznaczenia i Wywołaj `DoDragDrop` funkcję członkowską obiektu źródła danych. Jeśli aplikacja jest serwerem, użyj programu `COleServerItem::DoDragDrop` . Aby uzyskać informacje na temat dostosowywania standardowego zachowania przeciągania i upuszczania, zobacz sekcję [Dostosowywanie przeciągania i upuszczania](#customize-drag-and-drop).

Jeśli `DoDragDrop` zwraca **DROPEFFECT_MOVE**, natychmiast Usuń dane źródłowe z dokumentu źródłowego. Żadna inna wartość zwracana z nie `DoDragDrop` ma żadnego wpływu na źródło upuszczania.

Aby uzyskać więcej informacji, zobacz [obiekty danych OLE i źródła danych: Tworzenie i niszczenie](data-objects-and-data-sources-creation-and-destruction.md) oraz [obiekty danych OLE i źródła danych: manipulowanie](data-objects-and-data-sources-manipulation.md)\.

## <a name="implement-a-drop-target"></a><a name="implement-a-drop-target"></a>Implementowanie elementu docelowego upuszczania

Zaimplementowanie miejsca docelowego upuszczania niż źródło upuszczania zajmuje nieco więcej czasu, ale jest nadal stosunkowo proste.

### <a name="to-implement-an-ole-drop-target"></a>Aby zaimplementować obiekt docelowy upuszczania OLE

1. Jeśli jeszcze nie istnieje, Dodaj wywołanie do `AfxOleInit` `InitInstance` funkcji składowej aplikacji. To wywołanie jest wymagane do zainicjowania bibliotek OLE.

1. Dodaj zmienną członkowską do każdego widoku w aplikacji, która ma być miejscem docelowym upuszczania. Ta zmienna członkowska musi być typu `COleDropTarget` lub klasy pochodnej.

1. Z funkcji klasy widoku, która obsługuje komunikat **WM_CREATE** (zazwyczaj `OnCreate` ), wywołaj funkcję członkowską nowej zmiennej składowej `Register` . `Revoke`zostanie automatycznie wywołana dla Ciebie, gdy widok zostanie zniszczony.

1. Zastąp poniższe funkcje. Jeśli chcesz mieć takie samo zachowanie w aplikacji, Przesłoń te funkcje w klasie widoku. Jeśli chcesz zmodyfikować zachowanie w przypadku izolowanych przypadków lub chcesz włączyć opcję upuszczania w systemie innym niż `CView` Windows, Przesłoń te funkcje w `COleDropTarget` klasie pochodnej.

   | Zastąpienie | Aby zezwolić |
   | -------- | -------- |
   | `OnDragEnter` | Operacje usuwania są wykonywane w oknie. Wywołuje się, gdy kursor po raz pierwszy przejdzie do okna. |
   | `OnDragLeave` | Specjalne zachowanie, gdy operacja przeciągania opuszcza określone okno. |
   | `OnDragOver` | Operacje usuwania są wykonywane w oknie. Wywołuje się, gdy kursor jest przeciągany w oknie. |
   | `OnDrop` | Obsługa danych usuwanych do określonego okna. |
   | `OnScrollBy` | Specjalne zachowanie w przypadku, gdy w oknie docelowym jest wymagane przewijanie. |

Zobacz MAINVIEW. Plik CPP, który jest częścią przykładu OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) , aby zapoznać się z przykładem, jak te funkcje współpracują ze sobą.

Aby uzyskać więcej informacji, zobacz [obiekty danych OLE i źródła danych: Tworzenie i niszczenie](data-objects-and-data-sources-creation-and-destruction.md) oraz [obiekty danych OLE i źródła danych: manipulowanie](data-objects-and-data-sources-manipulation.md)\.

## <a name="customize-drag-and-drop"></a><a name="customize-drag-and-drop"></a>Dostosuj przeciąganie i upuszczanie

Domyślna implementacja funkcji przeciągania i upuszczania jest wystarczająca dla większości aplikacji. Jednak niektóre aplikacje mogą wymagać zmiany tego zachowania standardowego. W tej sekcji opisano kroki, które należy wykonać, aby zmienić te ustawienia domyślne. Za pomocą tej metody można tworzyć aplikacje, które nie obsługują dokumentów złożonych w źródłach.

Jeśli dostosowujesz standardowe zachowanie typu "przeciągnij i upuść", lub używasz aplikacji innej niż OLE, musisz utworzyć `COleDataSource` obiekt, który będzie zawierał dane. Gdy użytkownik uruchamia operację przeciągania i upuszczania, kod powinien wywołać `DoDragDrop` funkcję z tego obiektu zamiast z innych klas, które obsługują operacje przeciągania i upuszczania.

Opcjonalnie można utworzyć obiekt służący `COleDropSource` do sterowania upuszczaniem i przesłaniać część jego funkcji w zależności od typu zachowania, które chcesz zmienić. Ten obiekt typu "Drop source" jest następnie przekazaną do `COleDataSource::DoDragDrop` zmiany domyślnego zachowania tych funkcji. Te różne opcje umożliwiają znaczną elastyczność w zakresie obsługi operacji przeciągania i upuszczania w aplikacji. Aby uzyskać więcej informacji na temat źródeł danych, zobacz temat [obiekty danych artykułu i źródła danych (OLE)](data-objects-and-data-sources-ole.md).

Można przesłonić następujące funkcje, aby dostosować operacje przeciągania i upuszczania:

| Zastąpienie | Aby dostosować |
| -------- | ------------ |
| `OnBeginDrag` | Jak rozpoczyna się operacja przeciągania po wywołaniu `DoDragDrop` . |
| `GiveFeedback` | Wizualne Opinie, takie jak wygląd kursora, dla różnych wyników upuszczania. |
| `QueryContinueDrag` | Zakończenie operacji przeciągania i upuszczania. Ta funkcja umożliwia sprawdzenie Stanów klawiszy modyfikujących podczas operacji przeciągania. |

## <a name="see-also"></a>Zobacz też

[SERWERY](ole-in-mfc.md)\
[Obiekty danych OLE i źródła danych](data-objects-and-data-sources-ole.md)\
[Obiekty danych OLE i źródła danych: Tworzenie i niszczenie](data-objects-and-data-sources-creation-and-destruction.md)\
[Obiekty danych OLE i źródła danych: manipulowanie](data-objects-and-data-sources-manipulation.md)\
[COleClientItem::D oDragDrop](reference/coleclientitem-class.md#dodragdrop)\
[Klasa by uzyskać COleDataSource](reference/coledatasource-class.md)\
[By uzyskać COleDataSource::D oDragDrop](reference/coledatasource-class.md#dodragdrop)\
[Klasa COleDropSource](reference/coledropsource-class.md)\
[Klasa COleDropTarget](reference/coledroptarget-class.md)\
[CView:: OnDragLeave](reference/cview-class.md#ondragleave)

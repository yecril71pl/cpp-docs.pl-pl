---
title: 'Obiekty danych i źródła danych: tworzenie i likwidacja'
ms.date: 11/04/2016
helpviewer_keywords:
- destroying data objects [MFC]
- object creation [MFC], data source objects
- data sources [MFC], and data objects
- data source objects [MFC], creating
- destruction [MFC], data sources
- data source objects [MFC], destroying
- data objects [MFC], creating
- data objects [MFC], destroying
- data sources [MFC], role
- data sources [MFC], destroying
- destruction [MFC], data objects
- data sources [MFC], creating
ms.assetid: ac216d54-3ca5-4ce7-850d-cd1f6a90d4f1
ms.openlocfilehash: 58b68ca9597fd2a03cffb2bbab327dbc72d09599
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371215"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Obiekty danych i źródła danych: tworzenie i likwidacja

Jak wyjaśniono w artykule [Obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md)obiekty danych i źródła danych reprezentują obie strony transferu danych. W tym artykule wyjaśniono, kiedy utworzyć i zniszczyć te obiekty i źródła, aby prawidłowo wykonywać transfery danych, w tym:

- [Tworzenie obiektów danych](#_core_creating_data_objects)

- [Niszczenie obiektów danych](#_core_destroying_data_objects)

- [Tworzenie źródeł danych](#_core_creating_data_sources)

- [Niszczenie źródeł danych](#_core_destroying_data_sources)

## <a name="creating-data-objects"></a><a name="_core_creating_data_objects"></a>Tworzenie obiektów danych

Obiekty danych są używane przez aplikację docelową — klienta lub serwera. Obiekt danych w aplikacji docelowej jest jednym z końca połączenia między aplikacją źródłową a aplikacją docelową. Obiekt danych w aplikacji docelowej służy do uzyskiwania dostępu do danych w źródle danych i interakcji z nimi.

Istnieją dwie typowe sytuacje, w których potrzebny jest obiekt danych. Pierwszą sytuacją jest, gdy dane są upuszczane w aplikacji za pomocą przeciągania i upuszczania. Druga sytuacja jest wtedy, gdy wklej lub wklej specjalnie jest wybrany z menu Edycja.

W sytuacji przeciągania i upuszczania nie trzeba tworzyć obiektu danych. Wskaźnik do istniejącego obiektu danych zostanie `OnDrop` przekazany do funkcji. Ten obiekt danych jest tworzony przez platformę w ramach operacji przeciągania i upuszczania i będzie również niszczony przez niego. Nie zawsze jest to przypadek, gdy wklejanie odbywa się za pomocą innej metody. Aby uzyskać więcej informacji, zobacz [Niszczenie obiektów danych](#_core_destroying_data_objects).

Jeśli aplikacja wykonuje operację specjalną wklejania lub wklejania, należy utworzyć `COleDataObject` obiekt i wywołać jego `AttachClipboard` funkcję elementu członkowskiego. Powoduje to skojarzenie obiektu danych z danymi w Schowku. Następnie można użyć tego obiektu danych w funkcji wklejania.

## <a name="destroying-data-objects"></a><a name="_core_destroying_data_objects"></a>Niszczenie obiektów danych

Jeśli zastosujesz się do schematu opisanego w [temacie Tworzenie obiektów danych,](#_core_creating_data_objects)niszczenie obiektów danych jest trywialnym aspektem transferu danych. Obiekt danych, który został utworzony w funkcji wklejania zostaną zniszczone przez MFC po powrocie funkcji wklejania.

Jeśli zastosujesz się do innej metody obsługi operacji wklejania, upewnij się, że obiekt danych zostanie zniszczony po zakończeniu operacji wklejania. Dopóki obiekt danych nie zostanie zniszczony, żadna aplikacja nie będzie w stanie pomyślnie skopiować danych do Schowka.

## <a name="creating-data-sources"></a><a name="_core_creating_data_sources"></a>Tworzenie źródeł danych

Źródła danych są używane przez źródło transferu danych, które może być klientem lub po stronie serwera transferu danych. Źródło danych w aplikacji źródłowej jest jednym z końca połączenia między aplikacją źródłową a aplikacją docelową. Obiekt danych w aplikacji docelowej jest używany do interakcji z danymi w źródle danych.

Źródła danych są tworzone, gdy aplikacja musi skopiować dane do Schowka. Typowy scenariusz działa w ten sposób:

1. Użytkownik wybiera niektóre dane.

1. Użytkownik wybiera **polecenie Kopiuj** (lub **Wytnij)** z menu **Edycja** lub rozpoczyna operację przeciągania i upuszczania.

1. W zależności od projektu programu aplikacja tworzy `COleDataSource` obiekt lub obiekt z klasy `COleDataSource`pochodzącej od .

1. Wybrane dane są wstawiane do źródła danych przez `COleDataSource::CacheData` `COleDataSource::DelayRenderData` wywołanie jednej z funkcji w lub grupy.

1. Aplikacja wywołuje `SetClipboard` funkcję elementu członkowskiego `DoDragDrop` (lub funkcję elementu członkowskiego, jeśli jest to operacja przeciągania i upuszczania) należącą do obiektu utworzonego w kroku 3.

1. Jeśli jest to operacja `DoDragDrop` **Wytnij** lub **zwraca DROPEFFECT_MOVE,** dane wybrane w kroku 1 są usuwane z dokumentu.

Ten scenariusz jest implementowany przez próbki OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md). Spójrz na źródło dla każdej `CView`aplikacji klasy pochodnej `GetClipboardData` dla `OnGetClipboardData` wszystkich, ale i funkcje. Te dwie funkcje znajdują `COleClientItem` `COleServerItem`się w implementacjach klasy lub pochodnych. Te przykładowe programy stanowią dobry przykład na sposób zaimplementowania tych pojęć.

Inna sytuacja, w której można `COleDataSource` utworzyć obiekt występuje, jeśli modyfikujesz domyślne zachowanie operacji przeciągania i upuszczania. Aby uzyskać więcej informacji, zobacz [Ole Przeciągnij i upuść: Dostosowywanie przeciągania i upuszczania](../mfc/drag-and-drop-ole.md#customize-drag-and-drop) artykułu.

## <a name="destroying-data-sources"></a><a name="_core_destroying_data_sources"></a>Niszczenie źródeł danych

Źródła danych muszą zostać zniszczone przez aplikację, która jest za nie obecnie odpowiedzialna. W sytuacjach, w których źródło danych jest oddaniem ole, takie jak wywołanie [COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop), należy wywołać `pDataSrc->InternalRelease`. Przykład:

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

Jeśli nie zostały przekazane źródła danych do OLE, a następnie jesteś odpowiedzialny za zniszczenie go, jak w przypadku każdego typowego obiektu C++.

Aby uzyskać więcej informacji, zobacz [Przeciąganie i upuszczanie,](../mfc/drag-and-drop-ole.md) [Schowek](../mfc/clipboard.md)i [Manipulowanie obiektami danych i źródłami danych](../mfc/data-objects-and-data-sources-manipulation.md).

## <a name="see-also"></a>Zobacz też

[Obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[Klasa COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
[Klasa COleDataSource](../mfc/reference/coledatasource-class.md)

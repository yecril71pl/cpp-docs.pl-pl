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
ms.openlocfilehash: a46cc15a101618699b9e7fa988155517de673fdb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614971"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Obiekty danych i źródła danych: tworzenie i likwidacja

Zgodnie z opisem w artykule [obiekty danych i źródeł danych (OLE)](../mfc/data-objects-and-data-sources-ole.md), obiekty danych i źródeł danych reprezentują obie strony transferu danych. W tym artykule wyjaśniono, kiedy należy tworzyć i niszczyć te obiekty i źródeł, aby prawidłowo, wykonaj usługi transfery danych w tym:

- [Tworzenie obiektów danych](#_core_creating_data_objects)

- [Niszczenie obiektów danych](#_core_destroying_data_objects)

- [Tworzenie źródeł danych](#_core_creating_data_sources)

- [Niszczenie źródeł danych](#_core_destroying_data_sources)

##  <a name="_core_creating_data_objects"></a> Tworzenie obiektów danych

Obiekty danych są używane przez aplikację docelową — klienta lub serwera. Obiekt danych w aplikacji docelowej jest jednym końcu połączenie między usługą aplikacji źródłowej i docelowej. Obiekt danych w aplikacji docelowej służy do dostępu i interakcję z danymi w źródle danych.

Istnieją dwie typowe sytuacje, w których wymagane jest obiekt danych. Pierwszy sytuacja po upuszczeniu danych w aplikacji za pomocą przeciągania i upuszczania. Druga sytuacja jest po wybraniu z menu Edycja Wklej lub Wklej specjalne.

W sytuacji, przeciągnij i upuść nie trzeba utworzyć obiekt danych. Wskaźnik do istniejącego obiektu danych, które zostaną przekazane do usługi `OnDrop` funkcji. Ten obiekt danych jest tworzony przez strukturę w ramach operacji przeciągania i upuszczania oraz zostaną również usunięte przez nią. Nie zawsze jest to wymagane podczas wklejania odbywa się przy użyciu innej metody. Aby uzyskać więcej informacji, zobacz [niszczenie obiektów danych](#_core_destroying_data_objects).

Jeśli aplikacja działa, wklejanie lub Wklej specjalnej operacji, należy utworzyć `COleDataObject` obiektu, a następnie wywołać jej `AttachClipboard` funkcja elementu członkowskiego. Spowoduje to skojarzenie obiektu danych przy użyciu danych w Schowku. Następnie można ten obiekt danych w funkcji Wklej.

##  <a name="_core_destroying_data_objects"></a> Niszczenie obiektów danych

Jeśli stosujesz schematu, opisanego w [tworzenia obiektów danych](#_core_creating_data_objects), niszczenie obiektów danych jest prosta aspektem transferów danych. Obiekt danych, który został utworzony w funkcji Wklej jest niszczony, MFC, po powrocie funkcji Wklej.

Jeśli wykonasz innej metody obsługi operacji wklejania, upewnij się, że obiekt jest niszczony, po zakończeniu operacji wklejania. Do momentu zniszczenia obiektu danych nie było możliwe dla każdej aplikacji pomyślnie skopiować dane do Schowka.

##  <a name="_core_creating_data_sources"></a> Tworzenie źródeł danych

Źródła danych są używane przez źródło transfer danych, która może być klienta lub po stronie serwera, transferu danych. Źródło danych w aplikacji źródłowej jest jeden z końców połączenia między aplikacji źródłowej i docelowej. Obiekt danych w aplikacji docelowej służy do interakcji z danymi w źródle danych.

Źródła danych są tworzone, gdy aplikacja potrzebuje do kopiowania danych do Schowka. Typowy scenariusz uruchamia się następująco:

1. Gdy użytkownik wybierze niektórych danych.

1. Użytkownik wybierze **kopiowania** (lub **Wytnij**) z **Edytuj** menu lub rozpoczyna się operacja przeciągania i upuszczania.

1. W zależności od projektu program, aplikacja tworzy albo `COleDataSource` lub obiektu z klasą pochodną `COleDataSource`.

1. Wybrane dane są wstawiane do źródła danych, wywołując jedną z funkcji w `COleDataSource::CacheData` lub `COleDataSource::DelayRenderData` grup.

1. Wywołania aplikacji `SetClipboard` funkcji składowej (lub `DoDragDrop` funkcja elementu członkowskiego, jeśli jest to operacja przeciągania i upuszczania) należące do obiektu, który został utworzony w kroku 3.

1. Jeśli jest to **Wytnij** operacji lub `DoDragDrop` zwraca **DROPEFFECT_MOVE**, wybrane w kroku 1 dane są usuwane z dokumentu.

Ten scenariusz jest implementowany przez przykłady MFC OLE [OCLIENT](../visual-cpp-samples.md) i [HIERSVR](../visual-cpp-samples.md). Przyjrzyj się źródła dla każdej aplikacji `CView`-klasy dla wszystkie elementy oprócz `GetClipboardData` i `OnGetClipboardData` funkcji. Te dwie funkcje są albo `COleClientItem` lub `COleServerItem`-implementacji klasy pochodnej. Te przykładowe programy zapewniają dobrym przykładem sposobu wdrożenia tych pojęć.

Jeden innej sytuacji, w których warto utworzyć `COleDataSource` obiekt występuje w przypadku modyfikowania domyślne zachowanie operacji przeciągania i upuszczania. Aby uzyskać więcej informacji, zobacz [przeciąganie i upuszczanie: dostosowywanie](../mfc/drag-and-drop-customizing.md) artykułu.

##  <a name="_core_destroying_data_sources"></a> Niszczenie źródeł danych

Źródła danych musi zostać zniszczona przez aplikację, która jest obecnie odpowiedzialnych za. W sytuacjach, w którym przekazać źródła danych do OLE, takich jak wywoływanie [COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop), należy wywołać `pDataSrc->InternalRelease`. Na przykład:

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

Jeśli masz nie przekazywane źródła danych OLE, a następnie odpowiedzialność za zniszczenie, podobnie jak w przypadku dowolnego typowego obiektu języka C++.

Aby uzyskać więcej informacji, zobacz [przeciąganie i upuszczanie](../mfc/drag-and-drop-ole.md), [Schowka](../mfc/clipboard.md), i [manipulowanie obiekty danych i źródeł danych](../mfc/data-objects-and-data-sources-manipulation.md).

## <a name="see-also"></a>Zobacz też

[Obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[Klasa COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
[Klasa COleDataSource](../mfc/reference/coledatasource-class.md)

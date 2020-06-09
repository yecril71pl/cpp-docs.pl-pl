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
ms.openlocfilehash: 8d4edc93594bf453c61e03dca7e3117aefaa6c42
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620498"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Obiekty danych i źródła danych: tworzenie i likwidacja

Zgodnie z opisem w temacie [obiekty danych artykułu i źródła danych (OLE)](data-objects-and-data-sources-ole.md), obiekty danych i źródła danych reprezentują obie strony transferu danych. W tym artykule wyjaśniono, kiedy należy utworzyć i zniszczyć te obiekty i źródła w celu prawidłowego przeprowadzenia transferów danych, w tym:

- [Tworzenie obiektów danych](#_core_creating_data_objects)

- [Niszczenie obiektów danych](#_core_destroying_data_objects)

- [Tworzenie źródeł danych](#_core_creating_data_sources)

- [Niszczenie źródeł danych](#_core_destroying_data_sources)

## <a name="creating-data-objects"></a><a name="_core_creating_data_objects"></a>Tworzenie obiektów danych

Obiekty danych są używane przez aplikację docelową — klienta lub serwera. Obiekt danych w aplikacji docelowej jest jednym końcem połączenia między aplikacją źródłową a aplikacją docelową. Obiekt danych w aplikacji docelowej służy do uzyskiwania dostępu do danych w źródle danych i korzystania z nich.

Istnieją dwie typowe sytuacje, w których obiekt danych jest wymagany. Pierwsza sytuacja polega na tym, że dane są porzucane w aplikacji za pomocą przeciągania i upuszczania. Druga sytuacja polega na wybraniu opcji Wklej lub Wklej specjalnie z menu Edycja.

W przypadku przeciągania i upuszczania nie trzeba tworzyć obiektu danych. Wskaźnik do istniejącego obiektu danych zostanie przesłany do `OnDrop` funkcji. Ten obiekt danych jest tworzony przez platformę jako część operacji przeciągania i upuszczania, a także zostanie zniszczony przez nią. Nie zawsze jest to przypadek, gdy wklejanie jest wykonywane przez inną metodę. Aby uzyskać więcej informacji, zobacz [niszczenie obiektów danych](#_core_destroying_data_objects).

Jeśli aplikacja wykonuje operację wklejania lub wklejania, należy utworzyć `COleDataObject` obiekt i wywołać jego `AttachClipboard` funkcję członkowską. Spowoduje to skojarzenie obiektu danych z danymi w Schowku. Następnie można użyć tego obiektu danych w funkcji wklejania.

## <a name="destroying-data-objects"></a><a name="_core_destroying_data_objects"></a>Niszczenie obiektów danych

Jeśli zastosujesz schemat opisany w temacie [Tworzenie obiektów danych](#_core_creating_data_objects), niszczenie obiektów danych jest prostym aspektem transferów danych. Obiekt danych, który został utworzony w funkcji wklejania, zostanie zniszczony przez MFC, gdy funkcja wklejania zwróci wartość.

Jeśli korzystasz z innej metody obsługi operacji wklejania, upewnij się, że obiekt danych został zniszczony po zakończeniu operacji wklejania. Dopóki obiekt danych nie zostanie zniszczony, nie będzie możliwe, aby każda aplikacja pomyślnie skopiował dane do Schowka.

## <a name="creating-data-sources"></a><a name="_core_creating_data_sources"></a>Tworzenie źródeł danych

Źródła danych są używane przez źródło transferu danych, które mogą być klientem lub po stronie serwera transferu danych. Źródło danych w aplikacji źródłowej jest jednym końcem połączenia między aplikacją źródłową a aplikacją docelową. Obiekt danych w aplikacji docelowej jest używany do korzystania z danych w źródle danych.

Źródła danych są tworzone, gdy aplikacja wymaga kopiowania danych do Schowka. Typowy scenariusz działa następująco:

1. Użytkownik wybiera pewne dane.

1. Użytkownik wybiera polecenie **Kopiuj** (lub **Wytnij**) z menu **Edytuj** lub rozpoczyna operację przeciągania i upuszczania.

1. W zależności od projektu programu aplikacja tworzy `COleDataSource` obiekt lub obiekt z klasy pochodnej `COleDataSource` .

1. Wybrane dane są wstawiane do źródła danych przez wywołanie jednej z funkcji w `COleDataSource::CacheData` `COleDataSource::DelayRenderData` grupach lub.

1. Aplikacja wywołuje `SetClipboard` funkcję członkowską (lub `DoDragDrop` funkcję członkowską, jeśli jest to operacja przeciągania i upuszczania) należących do obiektu utworzonego w kroku 3.

1. Jeśli jest to operacja **wycinania** lub `DoDragDrop` zwraca **DROPEFFECT_MOVE**, dane wybrane w kroku 1 zostaną usunięte z dokumentu.

Ten scenariusz jest implementowany przez przykłady MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md). Przyjrzyj się źródłu dla każdej `CView` klasy pochodnej każdej aplikacji, dla wszystkich `GetClipboardData` funkcji i `OnGetClipboardData` . Te dwie funkcje znajdują się w `COleClientItem` `COleServerItem` implementacjach klas lub. Te przykładowe programy zapewniają dobry przykład implementacji tych koncepcji.

Jedną inną sytuacją, w której można utworzyć obiekt, `COleDataSource` występuje w przypadku modyfikowania domyślnego zachowania operacji przeciągania i upuszczania. Aby uzyskać więcej informacji, zobacz [Przeciąganie i upuszczanie OLE: Dostosowywanie artykułu przeciągnij i upuść](drag-and-drop-ole.md#customize-drag-and-drop) .

## <a name="destroying-data-sources"></a><a name="_core_destroying_data_sources"></a>Niszczenie źródeł danych

Źródła danych muszą zostać zniszczone przez aplikację, która jest aktualnie odpowiedzialna za nie. W sytuacjach, w których Źródło danych jest dostępne dla OLE, takie jak wywołanie [by uzyskać COleDataSource::D odragdrop](reference/coledatasource-class.md#dodragdrop), należy wywołać `pDataSrc->InternalRelease` . Przykład:

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

Jeśli źródło danych nie zostało przekazane do OLE, użytkownik jest odpowiedzialny za ich zniszczenie, podobnie jak w przypadku każdego typowego obiektu języka C++.

Aby uzyskać więcej informacji, zobacz [Przeciąganie i upuszczanie](drag-and-drop-ole.md), [schowek](clipboard.md)i [manipulowanie obiektami danych i źródłami danych](data-objects-and-data-sources-manipulation.md).

## <a name="see-also"></a>Zobacz też

[Obiekty danych i źródła danych (OLE)](data-objects-and-data-sources-ole.md)<br/>
[Klasa COleDataObject](reference/coledataobject-class.md)<br/>
[Klasa COleDataSource](reference/coledatasource-class.md)

---
title: 'Obiekty danych i źródła danych: tworzenie i likwidacja | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90143b919fde02a95df81d41845d8ecc671ced0d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931879"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Obiekty danych i źródła danych: tworzenie i likwidacja
Jak opisano w artykule [obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md), obiekty danych i źródeł danych reprezentują obie strony transferu danych. W tym artykule opisano, kiedy należy utworzyć i zniszcz te obiekty i źródła przeprowadzanie Twojej transferów danych, w tym:  
  
-   [Tworzenie obiektów danych](#_core_creating_data_objects)  
  
-   [Niszczenie obiektów danych](#_core_destroying_data_objects)  
  
-   [Tworzenie źródła danych](#_core_creating_data_sources)  
  
-   [Niszczenie źródeł danych](#_core_destroying_data_sources)  
  
##  <a name="_core_creating_data_objects"></a> Tworzenie obiektów danych  
 Obiekty danych są używane przez aplikację docelową — klienta lub serwera. Obiekt danych w aplikacji docelowej jest jeden element end połączenie między usługą aplikacji źródłowym i docelowym. Obiekt danych w aplikacji docelowej służy do dostęp i interakcję z danymi w źródle danych.  
  
 Istnieją dwie typowe sytuacje, gdy potrzebne jest obiekt danych. Pierwszy sytuacji jest po upuszczeniu danych w aplikacji przy użyciu operacji przeciągania i upuszczania. Drugi sytuacji jest po wklejeniu lub Wklej specjalne wybraniu z menu Edycja.  
  
 W przypadku przeciągania i upuszczania nie trzeba utworzyć obiektu danych. Wskaźnik do istniejącego obiektu danych zostanie przekazany do Twojej `OnDrop` funkcji. Ten obiekt danych jest tworzony przez platformę w ramach operacji przeciągania i upuszczania oraz zostaną również usunięte przez nią. To nie zawsze jest wielkość liter podczas wklejania odbywa się przy użyciu innej metody. Aby uzyskać więcej informacji, zobacz [niszczenie obiektów danych](#_core_destroying_data_objects).  
  
 Jeśli aplikacja jest wykonywane wklejanie lub specjalnych operacji wklejania, należy utworzyć `COleDataObject` obiekt i wywołanie jego `AttachClipboard` funkcję elementu członkowskiego. Obiekt danych skojarzenie z danymi w Schowku. Następnie można ten obiekt danych w funkcji Wklej.  
  
##  <a name="_core_destroying_data_objects"></a> Niszczenie obiektów danych  
 Jeśli wykonujesz schematu opisanego w [Tworzenie obiektów danych](#_core_creating_data_objects), niszczenie obiektów danych jest prosta aspektem transferów danych. Obiekt danych, który został utworzony w funkcji Wklej zostanie zniszczona przez MFC, po powrocie z funkcji Wklej.  
  
 Jeśli wykonujesz innej metody obsługi operacji wklejania, upewnij się, że obiekt zostanie zniszczony po zakończeniu operacji wklejania. Dopóki nie zostanie zniszczony obiekt danych, będzie niemożliwe dla dowolnej aplikacji pomyślnie skopiować dane do Schowka.  
  
##  <a name="_core_creating_data_sources"></a> Tworzenie źródła danych  
 Źródła danych są używane przez źródło transferu danych, który może być klienta lub po stronie serwera transferu danych. Źródło danych w aplikacji źródłowej jest jeden element end połączenie między usługą aplikacji źródłowym i docelowym. Obiekt danych w aplikacji docelowej służy do interakcji z danymi w źródle danych.  
  
 Źródeł danych są tworzone, gdy aplikacja musi skopiować dane do Schowka. Typowy scenariusz działa następująco:  
  
1.  Gdy użytkownik wybierze niektórych danych.  
  
2.  Użytkownik wybierze **kopiowania** (lub **Wytnij**) z **Edytuj** menu lub rozpoczyna się operacja przeciągania i upuszczania.  
  
3.  W zależności od projektu programu, aplikacja tworzy albo `COleDataSource` lub obiektu z klasą pochodną `COleDataSource`.  
  
4.  Wybrane dane zostaną wstawione do źródła danych, wywołując jedną z funkcji w `COleDataSource::CacheData` lub `COleDataSource::DelayRenderData` grup.  
  
5.  Wywołania aplikacji `SetClipboard` funkcji członkowskiej (lub `DoDragDrop` funkcji członkowskiej, jeśli jest to operacja przeciągania i upuszczania) należące do obiektu utworzonego w kroku 3.  
  
6.  Jeśli jest to **Wytnij** operacji lub `DoDragDrop` zwraca **DROPEFFECT_MOVE**, dane wybranej w kroku 1 zostaną usunięte z dokumentu.  
  
 Ten scenariusz jest implementowany przez przykłady MFC OLE [OCLIENT](../visual-cpp-samples.md) i [HIERSVR](../visual-cpp-samples.md). Przyjrzyj się źródła dla każdej aplikacji `CView`-klasy dla wszystkie elementy oprócz `GetClipboardData` i `OnGetClipboardData` funkcji. Te dwie funkcje są albo `COleClientItem` lub `COleServerItem`-implementacji klasy pochodnej. Te przykładowe programy zawierają dobrym przykładem sposobu wdrażania tych pojęć.  
  
 Jeden innej sytuacji, w którym można utworzyć `COleDataSource` obiekt występuje w przypadku modyfikowania domyślne zachowanie operacji przeciągania i upuszczania. Aby uzyskać więcej informacji, zobacz [przeciąganie i upuszczanie: dostosowywanie](../mfc/drag-and-drop-customizing.md) artykułu.  
  
##  <a name="_core_destroying_data_sources"></a> Niszczenie źródeł danych  
 Przez aplikację obecnie odpowiedzialnych za musi zostać zniszczona źródeł danych. W sytuacjach, w którym ręcznie źródła danych do OLE, takich jak wywoływanie [COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop), należy wywołać `pDataSrc->InternalRelease`. Na przykład:  
  
 [!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]  
  
 Jeśli nie ma przekazywany źródła danych OLE, następnie jest odpowiedzialny za niszczenie, podobnie jak w przypadku dowolnego typowego obiektu języka C++.  
  
 Aby uzyskać więcej informacji, zobacz [przeciągnij i upuść](../mfc/drag-and-drop-ole.md), [Schowka](../mfc/clipboard.md), i [manipulowanie obiekty danych i źródła danych](../mfc/data-objects-and-data-sources-manipulation.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md)   
 [Klasa COleDataObject](../mfc/reference/coledataobject-class.md)   
 [Klasa COleDataSource](../mfc/reference/coledatasource-class.md)

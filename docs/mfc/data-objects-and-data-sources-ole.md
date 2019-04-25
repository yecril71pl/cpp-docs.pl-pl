---
title: Obiekty danych i źródła danych (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
ms.openlocfilehash: 485fa5c62aafa4c116a76547238325d2979bfdc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241213"
---
# <a name="data-objects-and-data-sources-ole"></a>Obiekty danych i źródła danych (OLE)

Podczas przeprowadzania transferu danych za pomocą Schowka lub przeciągnij i upuść danych ma źródło i miejsce docelowe. Jedna aplikacja dostarcza dane do kopiowania i inna aplikacja akceptuje on wklejania. Każdej stronie transferu potrzebuje do wykonywania różnych operacji na tych samych danych w celu wykonania transferu zakończyło się sukcesem. Biblioteka Microsoft Foundation Class (MFC) zapewnia dwie klasy, które reprezentują na każdej stronie tego przeniesienia:

- Źródła danych (jako implementowany przez `COleDataSource` obiektów) reprezentują po stronie źródła transferu danych. Są one tworzone przez aplikację źródła, gdy dane, które ma zostać skopiowany do Schowka, lub gdy dane są dostarczane dla operacji przeciągania i upuszczania.

- Obiekty danych (jako implementowany przez `COleDataObject` obiektów) reprezentują po stronie docelowej transferu danych. Są one tworzone, gdy docelowa aplikacja ma danych porzucić tę sytuację, lub po otrzymaniu żądania do wykonywania operacji wklejania ze Schowka.

W poniższych artykułach opisano sposób użycia obiekty danych i źródeł danych w aplikacjach. Te informacje dotyczą zarówno kontenera, jak i serwera aplikacji, ponieważ oba może zostać wywołana podczas kopiowania i wklejania danych.

- [Obiekty danych i źródeł danych: Tworzenie i likwidacja](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Obiekty danych i źródeł danych: Manipulowanie](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="in-this-section"></a>W tej sekcji

[Przeciąganie i upuszczanie](../mfc/drag-and-drop-ole.md)

[Schowek](../mfc/clipboard.md)

## <a name="see-also"></a>Zobacz także

[OLE](../mfc/ole-in-mfc.md)<br/>
[Klasa COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
[Klasa COleDataSource](../mfc/reference/coledatasource-class.md)

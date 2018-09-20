---
title: Obiekty danych i źródeł danych (OLE) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f933a8eb75c25921c3025f8ca1bc03a2c72fc81b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443946"
---
# <a name="data-objects-and-data-sources-ole"></a>Obiekty danych i źródła danych (OLE)

Podczas przeprowadzania transferu danych za pomocą Schowka lub przeciągnij i upuść danych ma źródło i miejsce docelowe. Jedna aplikacja dostarcza dane do kopiowania i inna aplikacja akceptuje on wklejania. Każdej stronie transferu potrzebuje do wykonywania różnych operacji na tych samych danych w celu wykonania transferu zakończyło się sukcesem. Biblioteka Microsoft Foundation Class (MFC) zapewnia dwie klasy, które reprezentują na każdej stronie tego przeniesienia:

- Źródła danych (jako implementowany przez `COleDataSource` obiektów) reprezentują po stronie źródła transferu danych. Są one tworzone przez aplikację źródła, gdy dane, które ma zostać skopiowany do Schowka, lub gdy dane są dostarczane dla operacji przeciągania i upuszczania.

- Obiekty danych (jako implementowany przez `COleDataObject` obiektów) reprezentują po stronie docelowej transferu danych. Są one tworzone, gdy docelowa aplikacja ma danych porzucić tę sytuację, lub po otrzymaniu żądania do wykonywania operacji wklejania ze Schowka.

W poniższych artykułach opisano sposób użycia obiekty danych i źródeł danych w aplikacjach. Te informacje dotyczą zarówno kontenera, jak i serwera aplikacji, ponieważ oba może zostać wywołana podczas kopiowania i wklejania danych.

- [Obiekty danych i źródła danych: tworzenie i likwidacja](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Obiekty danych i źródła danych: operowanie](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="in-this-section"></a>W tej sekcji

[Przeciąganie i upuszczanie](../mfc/drag-and-drop-ole.md)

[Schowek](../mfc/clipboard.md)

## <a name="see-also"></a>Zobacz też

[OLE](../mfc/ole-in-mfc.md)<br/>
[Klasa COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
[Klasa COleDataSource](../mfc/reference/coledatasource-class.md)

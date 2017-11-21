---
title: "Obiekty danych i źródła danych (OLE) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb39b5089b7cd4849e5afd3eaac239c0c2ab3adf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="data-objects-and-data-sources-ole"></a>Obiekty danych i źródła danych (OLE)
Podczas przeprowadzania transferu danych za pomocą Schowka lub przeciągania i upuszczania, dane mają źródłowym i docelowym. Co aplikacja udostępnia dane do kopiowania i inna aplikacja akceptuje on wklejania. Każdej strony przeniesienia musi wykonywać różne operacje na tych samych danych do przeniesienia powiodło się. Biblioteka Microsoft Foundation Class (MFC) zapewnia dwie klasy reprezentujące każdej strony to przeniesienie:  
  
-   Źródła danych (zaimplementowanego przez `COleDataSource` obiektów) reprezentuje po stronie źródła transferu danych. Są one tworzone przez aplikację źródła, gdy danych ma zostać skopiowany do Schowka lub gdy podano danych dla operacji przeciągania i upuszczania.  
  
-   Obiekty danych (zaimplementowanego przez `COleDataObject` obiektów) reprezentuje po stronie docelowej transferu danych. Są one tworzone po porzucony w niej lub monit o wykonanie operacji wklejania ze Schowka danych aplikacji docelowej.  
  
 Następujące artykuły opisano sposób użycia obiekty danych i źródła danych w aplikacji. Te informacje dotyczą zarówno kontenera, jak i serwera aplikacji, ponieważ zarówno może zostać wywołana podczas kopiowania i wklejania danych.  
  
-   [Obiekty danych i źródła danych: tworzenie i likwidacja](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Obiekty danych i źródła danych: manipulowanie](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przeciągnij i upuść](../mfc/drag-and-drop-ole.md)  
  
 [Schowka](../mfc/clipboard.md)  
  
## <a name="see-also"></a>Zobacz też  
 [OLE](../mfc/ole-in-mfc.md)   
 [Klasa COleDataObject](../mfc/reference/coledataobject-class.md)   
 [COleDataSource — klasa](../mfc/reference/coledatasource-class.md)

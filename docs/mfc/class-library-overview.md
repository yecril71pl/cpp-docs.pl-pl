---
title: "Przegląd biblioteki klas | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.mfc
dev_langs: C++
helpviewer_keywords:
- grouping MFC classes
- MFC, class library
- classes [MFC], MFC
- class libraries, MFC
- class libraries
ms.assetid: 9b0e3152-ac39-4f52-91b4-f20aa3a674aa
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 014e1792a3431fee8dad673d17afdb84ef620936
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="class-library-overview"></a>Przegląd biblioteki klas
To omówienie kategoryzuje oraz opis klas w wersji 9.0 biblioteki klasy Foundation (MFC) firmy Microsoft. Struktura aplikacji stanowi klas MFC razem, — struktura aplikacji napisanych dla interfejsu API systemu Windows. Zadania programowania jest kod, który jest specyficzne dla aplikacji.  
  
 Biblioteki klas są przedstawione w tym miejscu w ramach następujących kategorii:  
  
-   [Klasa główna: CObject](../mfc/root-class-cobject.md)  
  
-   [Klasy związane z architekturą aplikacji MFC](../mfc/mfc-application-architecture-classes.md)  
  
    -   [Klasy obsługi wątków i aplikacji](../mfc/application-and-thread-support-classes.md)  
  
    -   [Klasy routingu poleceń](../mfc/command-routing-classes.md)  
  
    -   [Klasy dokumentów](../mfc/document-classes.md)  
  
    -   [Klasy widoków (architektura)](../mfc/view-classes-architecture.md)  
  
    -   [Klasy okien ramowych (architektura)](../mfc/frame-window-classes-architecture.md)  
  
    -   [Klasy szablonów dokumentów](../mfc/document-template-classes.md)  
  
-   [Okna, okno dialogowe i klasy formantów](../mfc/window-dialog-and-control-classes.md)  
  
    -   [Klasy okien ramowych (Windows)](../mfc/frame-window-classes-windows.md)  
  
    -   [Klasy widoków (Windows)](../mfc/view-classes-windows.md)  
  
    -   [Klasy okien dialogowych](../mfc/dialog-box-classes.md)  
  
    -   [Klasy formantów](../mfc/control-classes.md)  
  
    -   [Klasy pasków sterowania](../mfc/control-bar-classes.md)  
  
-   [Związane z rysowaniem i drukowaniem klas](../mfc/drawing-and-printing-classes.md)  
  
    -   [Klasy wyjściowe (kontekst urządzenia)](../mfc/output-device-context-classes.md)  
  
    -   [Klasy narzędzi do rysowania](../mfc/drawing-tool-classes.md)  
  
-   [Proste klasy typów danych](../mfc/simple-data-type-classes.md)  
  
-   [Tablic, List i klasy Map](../mfc/array-list-and-map-classes.md)  
  
    -   [Klasy szablonów dla tablic, list i map](../mfc/template-classes-for-arrays-lists-and-maps.md)  
  
    -   [Gotowe do użycia klasy tablic](../mfc/ready-to-use-array-classes.md)  
  
    -   [Gotowe do użycia klasy List](../mfc/ready-to-use-list-classes.md)  
  
    -   [Gotowe do użycia klasy Map](../mfc/ready-to-use-map-classes.md)  
  
-   [Klasy bazy danych i plików](../mfc/file-and-database-classes.md)  
  
    -   [Klasy we/wy pliku](../mfc/file-i-o-classes.md)  
  
    -   [DAO — klasy](../mfc/dao-classes.md)  
  
    -   [ODBC — klasy](../mfc/odbc-classes.md)  
  
    -   [Klasy OLE DB](../mfc/ole-db-classes.md)  
  
-   [Klasy internetowe i sieciowe](../mfc/internet-and-networking-classes.md)  
  
    -   [Klasy Windows Sockets](../mfc/windows-sockets-classes.md)  
  
    -   [Klasy internetowe Win32](../mfc/win32-internet-classes.md)  
  
-   [Klasy OLE](../mfc/ole-classes.md)  
  
    -   [Klasy kontenerów OLE](../mfc/ole-container-classes.md)  
  
    -   [Klasy serwerów OLE](../mfc/ole-server-classes.md)  
  
    -   [OLE przeciągania i upuszczania oraz transferów danych klasy](../mfc/ole-drag-and-drop-and-data-transfer-classes.md)  
  
    -   [Klasy wspólnych okien dialogowych OLE](../mfc/ole-common-dialog-classes.md)  
  
    -   [Klasy automatyzacji OLE](../mfc/ole-automation-classes.md)  
  
    -   [Klasy formantów OLE](../mfc/ole-control-classes.md)  
  
    -   [Klasy dokumentów aktywnych](../mfc/active-document-classes.md)  
  
    -   [Klasy związane z mechanizmem OLE](../mfc/ole-related-classes.md)  
  
-   [Klasy debugowania i wyjątków](../mfc/debugging-and-exception-classes.md)  
  
    -   [Klasy obsługi debugowania](../mfc/debugging-support-classes.md)  
  
    -   [Klasy wyjątków](../mfc/exception-classes.md)  
  
 Sekcja [ogólne zasady projektowania klas klasy](../mfc/general-class-design-philosophy.md) wyjaśniono, jak została zaprojektowana biblioteki MFC.  
  
 Omówienie struktury, zobacz [pisać aplikacje dla systemu Windows za pomocą klasy](../mfc/using-the-classes-to-write-applications-for-windows.md). Niektóre z wymienionych powyżej klas są klasy ogólnego przeznaczenia, które mogą być używane poza platformę i podaj przydatne obiektów abstrakcyjnych, takich jak kolekcje, wyjątki, plików i ciągów.  
  
 Aby wyświetlić dziedziczenia klasy, należy użyć [diagram hierarchii klasy](../mfc/hierarchy-chart.md).  
  
 Oprócz klas wymienionych w tym omówieniu biblioteki MFC zawiera szereg makra, funkcje globalne i zmienne globalne. Brak Przegląd oraz szczegółowy wykaz je w temacie [makr MFC i funkcje globalne](../mfc/reference/mfc-macros-and-globals.md), który wykonuje alfabetyczny spis do klas MFC.  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje dla pulpitu MFC](../mfc/mfc-desktop-applications.md)


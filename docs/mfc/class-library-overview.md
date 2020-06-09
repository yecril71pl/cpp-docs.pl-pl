---
title: Przegląd biblioteki klas
ms.date: 09/17/2019
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- grouping MFC classes
- MFC, class library
- classes [MFC], MFC
- class libraries, MFC
- class libraries
ms.assetid: 9b0e3152-ac39-4f52-91b4-f20aa3a674aa
ms.openlocfilehash: bf30f1b0aa83ef002337b76601f04c7103963441
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620744"
---
# <a name="class-library-overview"></a>Przegląd biblioteki klas

To omówienie obejmuje kategoryzacje i opisuje klasy w biblioteka MFC (MFC) w wersji 9,0. Klasy w MFC, a razem stanowią strukturę aplikacji — strukturę aplikacji zapisaną dla interfejsu API systemu Windows. Zadaniem programowania jest wypełnienie kodu, który jest specyficzny dla Twojej aplikacji.

Klasy biblioteki są prezentowane w następujących kategoriach:

- [Klasa główna: CObject](root-class-cobject.md)

- [Klasy związane z architekturą aplikacji MFC](mfc-application-architecture-classes.md)

  - [Klasy obsługi aplikacji i wątków](application-and-thread-support-classes.md)

  - [Klasy routingu poleceń](command-routing-classes.md)

  - [Klasy dokumentów](document-classes.md)

  - [Klasy widoków (architektura)](view-classes-architecture.md)

  - [Klasy okien ramowych (architektura)](frame-window-classes-architecture.md)

  - [Klasy szablonów dokumentów](document-template-classes.md)

- [Klasy okien, okien dialogowych i kontrolek](window-dialog-and-control-classes.md)

  - [Klasy okien ramowych (Windows)](frame-window-classes-windows.md)

  - [Klasy widoków (Windows)](view-classes-windows.md)

  - [Klasy okien dialogowych](dialog-box-classes.md)

  - [Klasy formantów](control-classes.md)

  - [Klasy pasków sterowania](control-bar-classes.md)

- [Klasy związane z rysowaniem i drukowaniem](drawing-and-printing-classes.md)

  - [Klasy wyjściowe (kontekst urządzenia)](output-device-context-classes.md)

  - [Klasy narzędzi do rysowania](drawing-tool-classes.md)

- [Proste klasy typów danych](simple-data-type-classes.md)

- [Klasy tablic, list i map](array-list-and-map-classes.md)

  - [Klasy szablonów dla tablic, list i map](template-classes-for-arrays-lists-and-maps.md)

  - [Gotowe do użycia klasy tablic](ready-to-use-array-classes.md)

  - [Gotowe do użycia klasy list](ready-to-use-list-classes.md)

  - [Gotowe do użycia klasy map](ready-to-use-map-classes.md)

- [Klasy plików i baz danych](file-and-database-classes.md)

  - [Klasy we/wy plików](file-i-o-classes.md)

  - [Klasy DAO](dao-classes.md)

  - [Klasy ODBC](odbc-classes.md)

  - [Klasy OLE DB](ole-db-classes.md)

- [Klasy internetowe i sieciowe](internet-and-networking-classes.md)

  - [Klasy Windows Sockets](windows-sockets-classes.md)

  - [Klasy internetowe Win32](win32-internet-classes.md)

- [Klasy OLE](ole-classes.md)

  - [Klasy kontenerów OLE](ole-container-classes.md)

  - [Klasy serwerów OLE](ole-server-classes.md)

  - [Klasy przeciągania i upuszczania oraz transferów danych OLE](ole-drag-and-drop-and-data-transfer-classes.md)

  - [Klasy wspólnych okien dialogowych OLE](ole-common-dialog-classes.md)

  - [Klasy automatyzacji OLE](ole-automation-classes.md)

  - [Klasy formantów OLE](ole-control-classes.md)

  - [Klasy dokumentów aktywnych](active-document-classes.md)

  - [Klasy związane z OLE](ole-related-classes.md)

- [Klasy debugowania i wyjątków](debugging-and-exception-classes.md)

  - [Klasy obsługi debugowania](debugging-support-classes.md)

  - [Klasy wyjątków](exception-classes.md)

W sekcji [ogólne zasady projektowania klasy](general-class-design-philosophy.md) wyjaśniono, jak biblioteka MFC została zaprojektowana.

Aby zapoznać się z omówieniem platformy, zobacz [Używanie klas do pisania aplikacji dla systemu Windows](using-the-classes-to-write-applications-for-windows.md). Niektóre wymienione powyżej klasy są klasami ogólnego przeznaczenia, które mogą być używane poza platformą i zapewniają przydatne streszczenia, takie jak kolekcje, wyjątki, pliki i ciągi.

Aby wyświetlić dziedziczenie klasy, użyj [wykresu hierarchii klas](hierarchy-chart.md).

Poza klasami wymienionymi w tym przeglądzie Biblioteka MFC zawiera wiele funkcji globalnych, zmiennych globalnych i makr. Istnieje przegląd i szczegółowa lista tych elementów w temacie [makra MFC i Globals](reference/mfc-macros-and-globals.md), która następuje po alfabetycznym odwołaniu do klas MFC.

## <a name="see-also"></a>Zobacz też

[Aplikacje klasyczne MFC](mfc-desktop-applications.md)

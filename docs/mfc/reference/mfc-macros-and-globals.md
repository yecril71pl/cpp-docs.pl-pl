---
title: Makr MFC i funkcje globalne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- MFC, global functions and variables
- MFC, macros
- global functions, MFC
- macros, MFC
- global functions [MFC]
- global variables, MFC
- Afx naming convention
- macros
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 189e3f272d679030c11fcd11ca4760f59944faeb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-macros-and-globals"></a>Makra i funkcje globalne MFC
Microsoft Foundation Class Library można podzielić na dwie główne części: (1 klasy MFC i (2) makra i funkcje globalne. Jeśli funkcja lub zmienna nie jest elementem członkowskim klasy, to globalnej funkcji lub zmienna.  
  
 Makra konwersji ciągu do udziału biblioteki MFC i Active Template Library (ATL). Aby uzyskać więcej informacji, zobacz [makra konwersji ciągu](../../atl/reference/string-conversion-macros.md) w dokumentacji ATL.  
  
 Makr MFC i funkcje globalne oferują funkcje w ramach następujących kategorii.  
  
## <a name="general-mfc"></a>Ogólne MFC  
  
-   [Typy danych](data-types-mfc.md)  
  
-   [Rzutowanie typów obiektów klas MFC](type-casting-of-mfc-class-objects.md)  
  
-   [Usługi modelu obiektów czasu wykonywania](run-time-object-model-services.md)  
  
-   [Usługi diagnostyczne](diagnostic-services.md)  
  
-   [Wyjątek podczas przetwarzania](exception-processing.md)  
  
-   [Formatowanie obiektu CString i wyświetlanie okna komunikatu](cstring-formatting-and-message-box-display.md)  
  
-   [Mapy wiadomości](message-map-macros-mfc.md)  

-   [Mapy interfejsu i delegata](delegate-and-interface-maps.md)

-   [Moduły i biblioteki DLL](extension-dll-macros.md)
  
-   [Informacje o aplikacji i zarządzanie](application-information-and-management.md)  
  
-   [Standardowa identyfikatorów poleceń i okien](standard-command-and-window-ids.md)  
  
-   [Pomocnicy klasy kolekcji](collection-class-helpers.md)  
  
-   [Funkcje szarych i symulowanych map bitowych](gray-and-dithered-bitmap-functions.md)  
  
-   [Standardowe procedury okna dialogowego danych programu exchange (DDX)](standard-dialog-data-exchange-routines.md)  
  
-   [Standardowe procedury okna dialogowego danych sprawdzania poprawności (DDV)](standard-dialog-data-validation-routines.md)  
  
-   [Komunikaty AFX](afx-messages.md)  
  
-   [Style kontrolki ToolBar](toolbar-control-styles.md)  
  
-   [Wyliczanie CMFCImagePaintArea::IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)  

  
## <a name="database"></a>Baza danych  
  
-   [Zarejestruj funkcje wymiany pól (RFX)](record-field-exchange-functions.md) i [funkcje zbiorcza wymiana pól rekordów (zbiorczej wymiany RFX)](record-field-exchange-functions.md) dla klas MFC ODBC  
  
-   [Funkcje (DFX) wymiany pól rekordów](record-field-exchange-functions.md) dla klas MFC DAO  
  
-   [Wymiana danych okna dialogowego (DDX) funkcje dla formularzy CRecordView i CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (klas MFC ODBC i DAO)  
  
-   [Wymiany danych okna dialogowego (DDX) funkcje dla formantów OLE](dialog-data-exchange-functions-for-ole-controls.md)  
  
-   [Makra i funkcje globalne ułatwiających bezpośrednie wywoływanie funkcji Otwórz połączenie bazy danych (ODBC) interfejsu API](database-macros-and-globals.md)  
  
-   [Inicjowanie aparatu bazy danych DAO i kończenie działania](dao-database-engine-initialization-and-termination.md)  
  
## <a name="internet"></a>Internet  
  
-   [Funkcje globalne do analizowania internetowych adresów URL](internet-url-parsing-globals.md)  
  
## <a name="dhtml--dhtml-event-maps"></a>DHTML / mapy zdarzeń DHTML  
  
-   [Wymiany danych okna dialogowego DHTML makra pomocnika (DDX)](ddx-dhtml-helper-macros.md)  
  
-   [Mapy zdarzeń DHTML](dhtml-event-maps.md)  
  
## <a name="ole"></a>OLE  
  
-   [Inicjalizacja OLE](ole-initialization.md)  
  
-   [Formant aplikacji](application-control.md)  
  
-   [Mapy wysyłania](dispatch-maps.md)  
  
 Ponadto MFC zawiera funkcji o nazwie [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) czy umożliwia każdy kontener OLE opracowanych za pomocą 4.0 MFC do w pełni obsługuje osadzonych formantów OLE.  
  
## <a name="ole-controls"></a>Formanty OLE  
  
-   [Stałe typów parametru Variant](variant-parameter-type-constants.md)  
  
-   [Dostęp do biblioteki typów](type-library-access.md)  
  
-   [Strony właściwości](property-pages-mfc.md)  
  
-   [Mapy zdarzeń](event-maps.md)  
  
-   [Mapy wychwytywania zdarzeń](event-sink-maps.md)  
  
-   [Mapy połączeń](connection-maps.md)  
  
-   [Rejestrowanie formantów OLE](registering-ole-controls.md)  
  
-   [Fabryki klas i Licencjonowanie](class-factories-and-licensing.md)  
  
-   [Stan trwały formantów OLE](persistence-of-ole-controls.md)  
  
 Pierwsza część w tej sekcji krótko opisano każdy z poprzednich kategorii i wymieniono funkcje globalne i makra w danej kategorii, wraz z krótkie opisy funkcji. Czynności opisane w tym przedstawiono opisy funkcje globalne, zmienne globalne i makra w bibliotece MFC.  
  
> [!NOTE]
>  Wiele funkcji globalnych rozpoczyna się od prefiksu "Afx", ale niektóre, na przykład funkcje programu exchange (DDX) danych w oknie dialogowym i wiele funkcji bazy danych nie wykonuj tę Konwencję. Wszystkie zmienne globalne rozpoczynać "afx" jako prefiksu. Makra nie rozpoczyna się żadnych określonego prefiksu, ale są napisane wielkimi literami.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../mfc/class-library-overview.md)




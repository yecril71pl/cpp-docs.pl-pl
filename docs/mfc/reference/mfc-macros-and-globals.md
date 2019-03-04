---
title: Makra i funkcje globalne MFC
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
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
ms.openlocfilehash: 27664d4e48c0c4e09439f9e970ded9f2a630d90d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268190"
---
# <a name="mfc-macros-and-globals"></a>Makra i funkcje globalne MFC

Biblioteki klas Microsoft Foundation można podzielić na dwie główne części: (1 klas MFC i (2) makra i funkcje globalne. Jeśli funkcja lub zmienna nie jest składową klasy, jest to, globalnej funkcji lub zmienna.

Biblioteka MFC i Active Template Library (ATL) używają makr konwersji ciągu. Aby uzyskać więcej informacji, zobacz [makra konwersji ciągów](../../atl/reference/string-conversion-macros.md) w dokumentacji ATL.

Makra i globalne MFC oferują funkcje w następujących kategoriach.

## <a name="general-mfc"></a>Ogólne MFC

- [Typy danych](data-types-mfc.md)

- [Rzutowanie typów obiektów klas MFC](type-casting-of-mfc-class-objects.md)

- [Usługi modelu obiektów czasu wykonywania](run-time-object-model-services.md)

- [Usługi diagnostyczne](diagnostic-services.md)

- [Przetwarzanie wyjątków](exception-processing.md)

- [Formatowanie obiektu CString i wyświetlanie okna komunikatu](cstring-formatting-and-message-box-display.md)

- [Mapy komunikatów](message-map-macros-mfc.md)

- [Delegata i mapy interfejsu](delegate-and-interface-maps.md)

- [Moduły i biblioteki DLL](extension-dll-macros.md)

- [Informacje o aplikacji i zarządzanie](application-information-and-management.md)

- [Standardowa identyfikatorów poleceń i okien](standard-command-and-window-ids.md)

- [Pomocnicy klasy kolekcji](collection-class-helpers.md)

- [Funkcje szarych i symulowanych map bitowych](gray-and-dithered-bitmap-functions.md)

- [Standardowe procedury okna dialogowego dane programu exchange (DDX)](standard-dialog-data-exchange-routines.md)

- [Standardowe procedury okna dialogowego danych sprawdzania poprawności (DDV)](standard-dialog-data-validation-routines.md)

- [Komunikaty AFX](afx-messages.md)

- [Style kontrolki ToolBar](toolbar-control-styles.md)

- [Wyliczanie CMFCImagePaintArea::IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>Baza danych

- [Zarejestruj funkcje wymiany pól (RFX)](record-field-exchange-functions.md) i [wymiana pól rekordów zbiorczego (zbiorcze RFX) funkcje](record-field-exchange-functions.md) dla klas MFC ODBC

- [Funkcje wymiany (DXF) pola rejestrowania](record-field-exchange-functions.md) dla klas MFC DAO

- [Wymiana danych okna dialogowego (DDX) funkcje dla formularzy CRecordView i CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (klas MFC ODBC i DAO)

- [Funkcje programu exchange (DDX) danych w oknie dialogowym dla formantów OLE](dialog-data-exchange-functions-for-ole-controls.md)

- [Makra i funkcje globalne do pomocy w bezpośrednie wywoływanie funkcji Open Database Connectivity (ODBC) interfejsu API](database-macros-and-globals.md)

- [Inicjowanie aparatu bazy danych DAO i zakończenie](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>Internet

- [Funkcje globalne do analizowania internetowych adresów URL](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>DHTML / mapy zdarzeń DHTML

- [Makra pomocnika (DDX) wymiany danych okna dialogowego DHTML](ddx-dhtml-helper-macros.md)

- [Mapy zdarzeń DHTML](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [Inicjalizacja OLE](ole-initialization.md)

- [Sterowanie aplikacjami](application-control.md)

- [Mapy wysyłania](dispatch-maps.md)

Ponadto biblioteka MFC zawiera funkcję o nazwie [afxenablecontrolcontainer —](ole-initialization.md#afxenablecontrolcontainer) czy umożliwia dowolnego kontenera OLE opracowanych za pomocą MFC 4.0 do zapewnienia pełnej obsługi osadzonych formantów OLE.

## <a name="ole-controls"></a>Formanty OLE

- [Stałe typów parametru Variant](variant-parameter-type-constants.md)

- [Dostęp do biblioteki typów](type-library-access.md)

- [Strony właściwości](property-pages-mfc.md)

- [Mapy zdarzeń](event-maps.md)

- [Mapy wychwytywania zdarzeń](event-sink-maps.md)

- [Mapy połączeń](connection-maps.md)

- [Rejestrowanie formantów OLE](registering-ole-controls.md)

- [Fabryki klas i Licencjonowanie](class-factories-and-licensing.md)

- [Stan trwały formantów OLE](persistence-of-ole-controls.md)

Pierwszej części tej sekcji krótko opisano każdy z poprzednich kategorii i wyświetla zmienne globalne i makra w danej kategorii, wraz z krótkie opisy funkcji. Zgodnie z dokumentem omówiono funkcje globalne, zmienne globalne i makra w bibliotece MFC.

> [!NOTE]
>  Wiele funkcji globalnych rozpoczynają się prefiksem "Afx", ale niektóre, na przykład funkcje programu exchange (DDX) danych w oknie dialogowym i wielu funkcji bazy danych nie stosują taką Konwencję. Wszystkie zmienne globalne zaczynać od "afx" jako prefiksu. Makra rozpoczyna się od dowolnego określonego prefiksu, ale są one napisane wielkimi literami.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../mfc/class-library-overview.md)

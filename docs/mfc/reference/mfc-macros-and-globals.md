---
title: Makra i funkcje globalne MFC
ms.date: 11/04/2016
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
ms.openlocfilehash: ed45fc7014bda18887be6dc8fbcdff8ba9a9c5f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373040"
---
# <a name="mfc-macros-and-globals"></a>Makra i funkcje globalne MFC

Biblioteka klas Microsoft Foundation można podzielić na dwie główne sekcje: (1) klasy MFC i (2) makra i globals. Jeśli funkcja lub zmienna nie jest członkiem klasy, jest to funkcja globalna lub zmienna.

Biblioteka MFC i biblioteka aktywnych szablonów (ATL) współużytkuje makra konwersji ciągów. Aby uzyskać więcej informacji, zobacz [Makra konwersji ciągów](../../atl/reference/string-conversion-macros.md) w dokumentacji ATL.

Makra MFC i globals oferują funkcje w następujących kategoriach.

## <a name="general-mfc"></a>Ogólne MFC

- [Typy danych](data-types-mfc.md)

- [Typ rzutowania obiektów klasy MFC](type-casting-of-mfc-class-objects.md)

- [Usługi modelu obiektów w czasie wykonywania](run-time-object-model-services.md)

- [Usługi diagnostyczne](diagnostic-services.md)

- [Przetwarzanie wyjątków](exception-processing.md)

- [Formatowanie CString i wyświetlanie okna komunikatu](cstring-formatting-and-message-box-display.md)

- [Mapy wiadomości](message-map-macros-mfc.md)

- [Delegowanie i mapy interfejsu](delegate-and-interface-maps.md)

- [Moduły i biblioteki DLL](extension-dll-macros.md)

- [Informacje o aplikacji i zarządzanie nimi](application-information-and-management.md)

- [Standardowe identyfikatory poleceń i okien](standard-command-and-window-ids.md)

- [Pomocnicy klasy zbierania](collection-class-helpers.md)

- [Szare i roztrząsane funkcje mapy bitowej](gray-and-dithered-bitmap-functions.md)

- [Standardowe procedury wymiany danych dialogowych (DDX)](standard-dialog-data-exchange-routines.md)

- [Procedury sprawdzania poprawności danych w oknie dialogowym (DDV)](standard-dialog-data-validation-routines.md)

- [Komunikaty AFX](afx-messages.md)

- [Style sterowania paskiem narzędzi](toolbar-control-styles.md)

- [CMFCImagePaintArea::IMAGE_EDIT_MODE — Wyliczenie](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>baza danych

- [Funkcje wymiany pól rekordów (RFX)](record-field-exchange-functions.md) i [zbiorcza wymiana pól rekordów (zbiorcza RFX)](record-field-exchange-functions.md) dla klas MFC ODBC

- [Funkcje wymiany pól rekordu (DFX)](record-field-exchange-functions.md) dla klas DAO MFC

- [Funkcje wymiany danych dialogowych (DDX) dla CRecordView i CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (klasy MFC ODBC i DAO)

- [Funkcje wymiany danych dialogowych (DDX) dla kontrolek OLE](dialog-data-exchange-functions-for-ole-controls.md)

- [Makra i globals do pomocy w wywoływaniu funkcji API Open Database Connectivity (ODBC) bezpośrednio](database-macros-and-globals.md)

- [Inicjowanie i zakończenie aparatu bazy danych DAO](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>Internet

- [Analizowanie adresów globalnych pod adresem URL w Internecie](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>Mapy zdarzeń DHTML / DHTML

- [Makra pomocnicze wymiany danych w oknie dialogowym DHTML (DDX)](ddx-dhtml-helper-macros.md)

- [Mapy zdarzeń DHTML](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [Inicjowanie OLE](ole-initialization.md)

- [Kontrola aplikacji](application-control.md)

- [Mapy wysyłki](dispatch-maps.md)

Ponadto MFC udostępnia funkcję o nazwie [AfxEnableControlContainer,](ole-initialization.md#afxenablecontrolcontainer) która umożliwia dowolny kontener OLE opracowany z MFC 4.0 w pełni obsługiwać wbudowane formanty OLE.

## <a name="ole-controls"></a>Elementy sterujące OLE

- [Stałe typu parametru wariantu](variant-parameter-type-constants.md)

- [Wpisz dostęp do biblioteki](type-library-access.md)

- [Strony właściwości](property-pages-mfc.md)

- [Mapy zdarzeń](event-maps.md)

- [Mapy zlewu zdarzeń](event-sink-maps.md)

- [Mapy połączeń](connection-maps.md)

- [Rejestrowanie kontrolek OLE](registering-ole-controls.md)

- [Fabryki klas i licencjonowanie](class-factories-and-licensing.md)

- [Trwałość kontroli OLE](persistence-of-ole-controls.md)

Pierwsza część tej sekcji pokrótce omawia każdą z poprzednich kategorii i zawiera listę globals i makra w kategorii, wraz z krótkimi opisami funkcji. Poniżej przedstawiono opisy funkcji globalnych, zmiennych globalnych i makr w bibliotece MFC.

> [!NOTE]
> Wiele funkcji globalnych rozpoczyna się od prefiksu "Afx", ale niektóre, na przykład, funkcje wymiany danych dialogowych (DDX) i wiele funkcji bazy danych, nie są zgodne z tą konwencją. Wszystkie zmienne globalne zaczynają się od "afx" jako prefiksu. Makra nie zaczynają się od żadnego konkretnego prefiksu, ale są pisane wielką literą.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../mfc/class-library-overview.md)

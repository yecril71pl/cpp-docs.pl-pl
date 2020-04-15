---
title: Pochodne klasy widoków dostępne w MFC
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 12b31074e4fcc2ed6a83e3669e1044f5b9caedab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373500"
---
# <a name="derived-view-classes-available-in-mfc"></a>Pochodne klasy widoków dostępne w MFC

W poniższej tabeli przedstawiono klasy widoku MFC i ich relacje ze sobą. Możliwości klasy widoku zależą od klasy widoku MFC, z której pochodzi.

### <a name="view-classes"></a>Zobacz klasy

|Klasa|Opis|
|-----------|-----------------|
|[Cview](../mfc/reference/cview-class.md)|Klasa podstawowa wszystkich widoków.|
|[Cctrlview](../mfc/reference/cctrlview-class.md)|Klasa `CTreeView`podstawowa `CListView` `CEditView`, `CRichEditView`, i . Te klasy umożliwiają korzystanie z architektury dokumentu/widoku ze wskazanymi typowymi formantami systemu Windows.|
|[Ceditview](../mfc/reference/ceditview-class.md)|Prosty widok oparty na formancie pola edycji systemu Windows. Umożliwia wprowadzanie i edytowanie tekstu i może być używany jako podstawa prostej aplikacji edytora tekstu. Zobacz też `CRichEditView`.|
|[Cricheditview](../mfc/reference/cricheditview-class.md)|Widok zawierający [obiekt CRichEditCtrl.](../mfc/reference/cricheditctrl-class.md) Ta klasa jest `CEditView`analogiczna `CEditView`do `CRichEditView` , ale w przeciwieństwie do , obsługuje sformatowany tekst.|
|[Clistview](../mfc/reference/clistview-class.md)|Widok zawierający [obiekt CListCtrl.](../mfc/reference/clistctrl-class.md)|
|[Ctreeview](../mfc/reference/ctreeview-class.md)|Widok zawierający [obiekt CTreeCtrl](../mfc/reference/ctreectrl-class.md) dla widoków przypominających okno Eksploratora rozwiązań w języku Visual C++.|
|[Cscrollview](../mfc/reference/cscrollview-class.md)|Klasa `CFormView`podstawowa `CRecordView`, `CDaoRecordView`i . Implementuje przewijanie zawartości widoku.|
|[Cformview](../mfc/reference/cformview-class.md)|Widok formularza, widok zawierający formanty. Aplikacja oparta na formularzach udostępnia jeden lub więcej takich interfejsów formularza.|
|[Chtmlview](../mfc/reference/chtmlview-class.md)|Widok przeglądarki sieci Web, za pomocą którego użytkownik aplikacji może przeglądać witryny w sieci World Wide Web, a także foldery w lokalnym systemie plików i w sieci. Widok przeglądarki sieci Web może również działać jako kontener dokumentu aktywnego.|
|[Crecordview](../mfc/reference/crecordview-class.md)|Widok formularza, który wyświetla rekordy bazy danych ODBC w formantach. Jeśli wybierzesz obsługę ODBC w projekcie, klasą bazową widoku jest `CRecordView`. Widok jest połączony `CRowset` z obiektem.|
|[Cdaorecordview](../mfc/reference/cdaorecordview-class.md)|Widok formularza, który wyświetla rekordy bazy danych DAO w formantach. Jeśli wybierzesz obsługę DAO w projekcie, klasą bazową widoku jest `CDaoRecordView`. Widok jest połączony `CDaoRecordset` z obiektem.|
|[Coledbrecordview](../mfc/reference/coledbrecordview-class.md)|Widok formularza, który wyświetla rekordy OLE DB w formantach. Jeśli wybierzesz obsługę OLE DB w projekcie, `COleDBRecordView`klasą podstawową widoku jest . Widok jest połączony `CRowset` z obiektem.|

> [!NOTE]
> Od wersji MFC 4.0, `CEditView` pochodzi `CCtrlView`od .

Aby użyć tych klas w aplikacji, należy wyprowadzić klasy widoku aplikacji z nich. Aby uzyskać powiązane informacje, zobacz [Przewijanie i skalowanie widoków](../mfc/scrolling-and-scaling-views.md). Aby uzyskać więcej informacji na temat klas bazy danych, zobacz [Omówienie: Programowanie baz danych](../data/data-access-programming-mfc-atl.md).

## <a name="see-also"></a>Zobacz też

[Używanie widoków](../mfc/using-views.md)

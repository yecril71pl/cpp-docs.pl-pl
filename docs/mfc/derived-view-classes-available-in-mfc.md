---
title: Pochodne klasy widoków dostępne w MFC
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: dc0f0b10ea291db32c576a7d36b7fc19728fa6ce
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616983"
---
# <a name="derived-view-classes-available-in-mfc"></a>Pochodne klasy widoków dostępne w MFC

W poniższej tabeli przedstawiono klasy widoków MFC i ich relacje ze sobą. Możliwości klasy widoku zależą od klasy widoku MFC, z której dziedziczy.

### <a name="view-classes"></a>Klasy widoków

|Klasa|Opis|
|-----------|-----------------|
|[CView](reference/cview-class.md)|Klasa bazowa wszystkich widoków.|
|[CCtrlView](reference/cctrlview-class.md)|Klasa bazowa `CTreeView` , `CListView` , `CEditView` , i `CRichEditView` . Te klasy umożliwiają używanie architektury dokumentu/widoku ze wskazanymi typowymi kontrolkami systemu Windows.|
|[Elementu CEditView](reference/ceditview-class.md)|Widok prosty oparty na kontrolce pola edycji systemu Windows. Umożliwia wprowadzanie i edytowanie tekstu oraz może służyć jako podstawa dla prostej aplikacji edytora tekstu. Zobacz też `CRichEditView`.|
|[CRichEditView](reference/cricheditview-class.md)|Widok zawierający obiekt [CRichEditCtrl](reference/cricheditctrl-class.md) . Ta klasa jest analogiczna do `CEditView` , ale w przeciwieństwie do `CEditView` , `CRichEditView` obsługuje sformatowany tekst.|
|[CListView](reference/clistview-class.md)|Widok zawierający obiekt [CListCtrl](reference/clistctrl-class.md) .|
|[CTreeView](reference/ctreeview-class.md)|Widok zawierający obiekt [CTreeCtrl](reference/ctreectrl-class.md) dla widoków, które przypominają okno Eksplorator rozwiązań w Visual C++.|
|[CScrollView](reference/cscrollview-class.md)|Klasa bazowa `CFormView` , `CRecordView` , i `CDaoRecordView` . Implementuje przewijanie zawartości widoku.|
|[CFormView](reference/cformview-class.md)|Widok formularza, widok zawierający kontrolki. Aplikacja oparta na formularzach udostępnia jeden lub więcej takich interfejsów.|
|[CHtmlView](reference/chtmlview-class.md)|Widok przeglądarki sieci Web, za pomocą którego użytkownik aplikacji może przeglądać witryny na World Wide Web, a także foldery w lokalnym systemie plików i w sieci. Widok przeglądarki sieci Web może również współdziałać z aktywnym kontenerem dokumentów.|
|[Formularzy CRecordView](reference/crecordview-class.md)|Widok formularza wyświetlający rekordy bazy danych ODBC w kontrolkach. W przypadku wybrania obsługi ODBC w projekcie, Klasa bazowa widoku to `CRecordView` . Widok jest połączony z `CRowset` obiektem.|
|[CDaoRecordView](reference/cdaorecordview-class.md)|Widok formularza wyświetlający rekordy bazy danych DAO w kontrolkach. Jeśli wybierzesz obsługę DAO w projekcie, Klasa bazowa widoku to `CDaoRecordView` . Widok jest połączony z `CDaoRecordset` obiektem.|
|[COleDBRecordView](reference/coledbrecordview-class.md)|Widok formularza, który wyświetla OLE DB rekordy w kontrolkach. W przypadku wybrania OLE DB obsługi w projekcie, Klasa bazowa widoku to `COleDBRecordView` . Widok jest połączony z `CRowset` obiektem.|

> [!NOTE]
> Począwszy od programu MFC w wersji 4,0, pochodzi `CEditView` od `CCtrlView` .

Aby użyć tych klas w aplikacji, należy utworzyć z nich klasy widoku aplikacji. Aby uzyskać powiązane informacje, zobacz [Widok przewijania i skalowania](scrolling-and-scaling-views.md). Aby uzyskać więcej informacji na temat klas baz danych, zobacz [Omówienie: Programowanie baz danych](../data/data-access-programming-mfc-atl.md).

## <a name="see-also"></a>Zobacz też

[Używanie widoków](using-views.md)

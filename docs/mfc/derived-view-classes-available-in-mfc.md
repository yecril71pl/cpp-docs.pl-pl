---
title: Pochodne klasy widoków dostępne w MFC
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 61b38f6147a8bde4f6eb42cd144f9f64dac8dbd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152907"
---
# <a name="derived-view-classes-available-in-mfc"></a>Pochodne klasy widoków dostępne w MFC

W poniższej tabeli przedstawiono klasy widoku MFC i ich relacji ze sobą. Funkcje klasy widoku są zależne od klasy widoku MFC, z którego pochodzi.

### <a name="view-classes"></a>Klasy widoków

|Class|Opis|
|-----------|-----------------|
|[CView](../mfc/reference/cview-class.md)|Klasa bazowa wszystkich widoków.|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|Klasa bazowa `CTreeView`, `CListView`, `CEditView`, i `CRichEditView`. Klasy te umożliwiają używanie architektury dokument/widok przy użyciu wskazanego wspólnych formantów Windows.|
|[Elementu CEditView](../mfc/reference/ceditview-class.md)|Widok prosty oparte na Windows edytować formantu pola. Umożliwia wprowadzanie i edycję tekstu i może służyć jako podstawa aplikacji edytora zwykłego tekstu. Zobacz też `CRichEditView`.|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|Widok zawierający [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) obiektu. Ta klasa jest odpowiednikiem `CEditView`, ale w przeciwieństwie do `CEditView`, `CRichEditView` uchwyty sformatowanego tekstu.|
|[CListView](../mfc/reference/clistview-class.md)|Widok zawierający [CListCtrl](../mfc/reference/clistctrl-class.md) obiektu.|
|[CTreeView](../mfc/reference/ctreeview-class.md)|Widok zawierający [CTreeCtrl](../mfc/reference/ctreectrl-class.md) obiektu dla widoków, które przypominają okna Eksploratora rozwiązań w programie Visual C++.|
|[CScrollView](../mfc/reference/cscrollview-class.md)|Klasa bazowa `CFormView`, `CRecordView`, i `CDaoRecordView`. Implementuje przewijanie zawartości tego widoku.|
|[CFormView](../mfc/reference/cformview-class.md)|Widok formularza widoku, który zawiera formanty. Aplikacją opartą na formularzach zawiera jeden lub więcej takich interfejsów formularza.|
|[CHtmlView](../mfc/reference/chtmlview-class.md)|Widoku przeglądarki sieci Web za pomocą którego aplikacja umożliwić użytkownikom przeglądanie witryn w sieci World Wide Web, a także folderów w lokalnym systemie plików, a w sieci. Widoku przeglądarki sieci Web mogą również działać jako kontener aktywnego dokumentu.|
|[CRecordView](../mfc/reference/crecordview-class.md)|Widok formularza wyświetlający rekordy bazy danych ODBC w kontrolkach. Jeśli wybierzesz opcję Obsługa ODBC w projekcie, klasa bazowa widoku jest `CRecordView`. Widok jest podłączony do `CRowset` obiektu.|
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|Widok formularza wyświetlający rekordy bazy danych DAO w kontrolkach. Jeśli wybierzesz opcję obsługi DAO w projekcie, klasa bazowa widoku jest `CDaoRecordView`. Widok jest podłączony do `CDaoRecordset` obiektu.|
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|Widok formularza, który wyświetla rekordów OLE DB w kontrolkach. Jeśli wybierzesz opcję Obsługa OLE DB w projekcie, klasa bazowa widoku jest `COleDBRecordView`. Widok jest podłączony do `CRowset` obiektu.|

> [!NOTE]
>  Począwszy od wersji 4.0, MFC `CEditView` jest tworzony na podstawie `CCtrlView`.

Aby użyć tych klas w aplikacji, dziedziczyć klasy widoku aplikacji je. Aby uzyskać powiązane informacje, zobacz [przewijanie i skalowanie widoków](../mfc/scrolling-and-scaling-views.md). Aby uzyskać więcej informacji na temat klas baz danych, zobacz [omówienie: Baza danych programowania](../data/data-access-programming-mfc-atl.md).

## <a name="see-also"></a>Zobacz także

[Używanie widoków](../mfc/using-views.md)

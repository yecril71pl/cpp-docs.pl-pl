---
title: "Pochodzi z klasy widoków dostępne w MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2426f3e547da6eaab6a4b38bb5199e87c93ef933
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="derived-view-classes-available-in-mfc"></a>Pochodne klasy widoków dostępne w MFC
W poniższej tabeli przedstawiono MFC widoku klasy i ich relacji między nimi. Funkcje klasy widoku są zależne od klasy widoku MFC, z którego pochodzi.  
  
### <a name="view-classes"></a>Klasy widoku  
  
|Class|Opis|  
|-----------|-----------------|  
|[Cview —](../mfc/reference/cview-class.md)|Klasa podstawowa wszystkich widoków.|  
|[CCtrlView](../mfc/reference/cctrlview-class.md)|Podstawowa klasa `CTreeView`, `CListView`, `CEditView`, i `CRichEditView`. Te klasy umożliwiają używanie architektury dokument/widok z wskazanych formanty standardowe systemu Windows.|  
|[CEditView](../mfc/reference/ceditview-class.md)|Prosty widok opartych na systemie Windows Edytuj kontrolkę pola. Umożliwia wprowadzanie i edycję tekstu i może służyć jako podstawa dla aplikacji edytor tekstowy. Zobacz też `CRichEditView`.|  
|[Cricheditview —](../mfc/reference/cricheditview-class.md)|Widok zawierający [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) obiektu. Ta klasa jest odpowiednikiem `CEditView`, ale w przeciwieństwie do `CEditView`, `CRichEditView` dojść sformatowanego tekstu.|  
|[Clistview —](../mfc/reference/clistview-class.md)|Widok zawierający [CListCtrl](../mfc/reference/clistctrl-class.md) obiektu.|  
|[CTreeView —](../mfc/reference/ctreeview-class.md)|Widok zawierający [CTreeCtrl](../mfc/reference/ctreectrl-class.md) obiektu dla widoków, które przypominają okna Eksploratora rozwiązań w programie Visual C++.|  
|[CScrollView](../mfc/reference/cscrollview-class.md)|Podstawowa klasa `CFormView`, `CRecordView`, i `CDaoRecordView`. Implementuje przewijanie zawartości widoku.|  
|[CFormView](../mfc/reference/cformview-class.md)|Widok formularza, widok, który zawiera formanty. Aplikacja formularzy zawiera jeden lub więcej takich interfejsów formularza.|  
|[CHtmlView](../mfc/reference/chtmlview-class.md)|Widok przeglądarki sieci Web, z którym użytkownik aplikacji można przeglądać witryn w sieci World Wide Web, a także folderów w lokalnym systemie plików, a w sieci. Widok przeglądarki sieci Web mogą również działać jako kontener dokumentów aktywnych.|  
|[CRecordView](../mfc/reference/crecordview-class.md)|Widok formularz, który wyświetla rekordów bazy danych ODBC w formantach. W przypadku wybrania Obsługa ODBC w projekcie widoku klasa podstawowa jest `CRecordView`. Widok jest połączona z `CRowset` obiektu.|  
|[Cdaorecordview —](../mfc/reference/cdaorecordview-class.md)|Widok formularz, który wyświetla rekordów bazy danych DAO w formantach. W przypadku wybrania DAO pomocy technicznej w projekcie widoku klasa podstawowa jest `CDaoRecordView`. Widok jest połączona z `CDaoRecordset` obiektu.|  
|[Coledbrecordview —](../mfc/reference/coledbrecordview-class.md)|Widok formularz, który wyświetla rekordów OLE DB w formantach. W przypadku wybrania Obsługa OLE DB w projekcie widoku klasa podstawowa jest `COleDBRecordView`. Widok jest połączona z `CRowset` obiektu.|  
  
> [!NOTE]
>  Począwszy od wersji 4.0, MFC `CEditView` jest pochodną `CCtrlView`.  
  
 Aby korzystać z tych klas w aplikacji, pochodną klasy widoku aplikacji je. Aby uzyskać odpowiednie informacje, zobacz [przewijanie i skalowanie widoków](../mfc/scrolling-and-scaling-views.md). Aby uzyskać więcej informacji o klasach bazy danych, zobacz [omówienie: programowania bazy danych](../data/data-access-programming-mfc-atl.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie widoków](../mfc/using-views.md)


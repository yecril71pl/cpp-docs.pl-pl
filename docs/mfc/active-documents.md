---
title: Dokumenty aktywne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52f3165f69d47f63fc52ae01bbbd1947e7755a43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="active-documents"></a>Dokumenty aktywne
Dokumenty aktywne rozszerzyć technologii złożonego dokumentu OLE. Rozszerzenia te są udostępniane w formie dodatkowe interfejsy, które zarządzają widoków, dzięki czemu obiekty mogą działać w kontenerach i jeszcze zachować kontrolę nad ich wyświetlania i funkcji drukowania. Ten proces pozwala na wyświetlanie dokumentów obcego ramki (na przykład Microsoft Office Binder lub programu Microsoft Internet Explorer) oraz ramek natywnych (na przykład portów widok tego produktu).  
  
 W tej sekcji opisano funkcjonalności [wymagania dotyczące dokumentów aktywnych](#requirements_for_active_documents). Aktywny dokument jest właścicielem zestawu danych i ma dostęp do magazynu, gdzie można zapisać i pobrać dane. Można go tworzyć i zarządzać co najmniej jeden widok na jego danych. Oprócz obsługi zwykle osadzanie i aktywacja w miejscu interfejsy OLE dokumentów, dokumentów aktywnych komunikuje się możliwość tworzenia widoków za pośrednictwem `IOleDocument`. Za pomocą tego interfejsu kontenera można zażądać Utwórz (i prawdopodobnie wyliczyć) widoki, które można wyświetlić w aktywnym dokumencie. Za pomocą tego interfejsu aktywny dokument zapewniają różne informacje, takie jak czy obsługuje wiele widoków lub prostokąty złożonych.  
  
 Poniżej przedstawiono **IOleDocument** interfejsu. Należy pamiętać, że **IEnumOleDocumentViews** interfejs jest standardowy moduł wyliczający OLE dla **IOleDocumentView \***  typów.  
  
```  
interface IOleDocument : IUnknown  
    {  
    HRESULT CreateView(  
        [in] IOleInPlaceSite *pIPSite,  
        [in] IStream *pstm,  
        [in] DWORD dwReserved,  
        [out] IOleDocumentView **ppView);  

    HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);  

    HRESULT EnumViews(  
        [out] IEnumOleDocumentViews **ppEnum,  
        [out] IOleDocumentView **ppView);  
    }  
```  
  
 Każdego aktywnego dokumentu musi mieć dostawcę ramki widoku z tego interfejsu. Jeśli dokument nie jest osadzony w kontenerze, sam serwer dokumentów aktywnych podać ramki widoku. Aktywny dokument osadzone w kontenerze dokumentów aktywnych kontenera zapewnia jednak ramki widoku.  
  
 Dokument aktywny, można utworzyć jeden lub więcej typów [widoków](#requirements_for_view_objects) swoich danych (na przykład normalne, konspektu, strony układu i tak dalej). Widoki działać tak jak filtry za pomocą których dane są widoczne. Nawet wtedy, gdy dokument ma tylko jeden typ widoku, może nadal chcesz obsługiwać wiele widoków jako sposób obsługi nowych funkcji okna (na przykład **nowe okno** elementu na **okna** menu pakietu Office aplikacje).  
  
##  <a name="requirements_for_active_documents"></a>Wymagania dotyczące dokumentów aktywnych  
 Aktywny dokument wyświetlany w kontenerze aktywny dokument musi:  
  
-   Użyj plików złożonych OLE jego mechanizmu magazynowania zaimplementowanie `IPersistStorage`.  
  
-   Obsługuje podstawowe funkcje osadzania OLE dokumentów, w tym **Utwórz z pliku**. Wymaga to interfejsy `IPersistFile`, `IOleObject`, i `IDataObject`.  
  
-   Obsługuje co najmniej jeden widok, z których każdy jest w stanie aktywacji w miejscu. Oznacza to, widoki musi obsługiwać interfejs `IOleDocumentView` oraz interfejsów `IOleInPlaceObject` i `IOleInPlaceActiveObject` (przy użyciu kontenera **IOleInPlaceSite** i **IOleInPlaceFrame** interfejsy).  
  
-   Obsługuje interfejsy standardowe dokumentów aktywnych `IOleDocument`, `IOleCommandTarget`, i `IPrint`.  
  
 Wiedzy o kiedy i jak używać interfejsów po stronie kontenera jest podany w tych wymagań.  
  
##  <a name="requirements_for_view_objects"></a>Wymagania dotyczące obiekty widoku  
 Aktywny dokument można utworzyć co najmniej jeden widok swoich danych. Funkcjonalnie tych widoków są podobne do portów na konkretnej metody do wyświetlania danych. Jeśli aktywny dokument obsługuje tylko jeden widok, aktywny dokument i że pojedynczego widoku można zaimplementować przy użyciu jednej klasy. **IOleDocument::CreateView** zwraca ten sam obiekt `IOleDocumentView` wskaźnika interfejsu.  
  
 Może być reprezentowana kontenera dokumentów aktywnych, musi obsługiwać składnika widoku **IOleInPlaceObject** i **IOleInPlaceActiveObject** oprócz `IOleDocumentView`:  
  
```  
interface IOleDocumentView : IUnknown  
    {  
    HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);  
    HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);  
    HRESULT GetDocument([out] IUnknown **ppunk);  
    [input_sync] HRESULT SetRect([in] LPRECT prcView);  
    HRESULT GetRect([in] LPRECT prcView);  
    [input_sync] HRESULT SetRectComplex(  
        [in] LPRECT prcView,  
        [in] LPRECT prcHScroll,  
        [in] LPRECT prcVScroll,  
        [in] LPRECT prcSizeBox);  
    HRESULT Show([in] BOOL fShow);  
    HRESULT UIActivate([in] BOOL fUIActivate);  
    HRESULT Open(void);  
    HRESULT CloseView([in] DWORD dwReserved);  
    HRESULT SaveViewState([in] IStream *pstm);  
    HRESULT ApplyViewState([in] IStream *pstm);  
    HRESULT Clone(  
        [in] IOleInPlaceSite *pIPSiteNew,  
        [out] IOleDocumentView **ppViewNew);  
    }  
```  
  
 Każdy widok ma lokacji skojarzonego widoku, który hermetyzuje ramki widoku oraz widoku portu (HWND i prostokątny obszar w danym przedziale). Lokacji ta funkcja udostępnia jednak standardowego **IOleInPlaceSite** interfejsu. Należy pamiętać, że można mieć więcej niż jeden port widok na jednym HWND.  
  
 Zazwyczaj każdy typ widoku ma inną reprezentacji wydruku. Dlatego widoków i powiązane Lokacje widok powinien implementować interfejsów drukowania Jeśli `IPrint` i `IContinueCallback`odpowiednio. Ramki widoku muszą uzgodnić z dostawcą widoku za pośrednictwem **iprint —** podczas drukowania rozpoczyna się, że nagłówków, stopek marginesy i powiązane elementy są drukowane poprawnie. Dostawca widoku powiadamia ramki za pośrednictwem zdarzenia związane z drukowaniem `IContinueCallback`. Aby uzyskać więcej informacji na korzystanie z tych interfejsów, temacie [drukowanie programowe](../mfc/programmatic-printing.md).  
  
 Należy pamiętać, że jeśli aktywny dokument obsługuje tylko jeden widok, następnie aktywny dokument i że pojedynczego widoku można zaimplementować przy użyciu jednej klasy konkretnej. **IOleDocument::CreateView** po prostu zwraca ten sam obiekt `IOleDocumentView` wskaźnika interfejsu. Innymi słowy nie jest konieczne, który istnieć dwa wystąpienia oddzielny obiekt gdy wymagane jest tylko jeden widok.  
  
 Wyświetl obiekt może być również docelowym polecenia. Zaimplementowanie `IOleCommandTarget` widok może odbierać polecenia, które pochodzą z kontenera interfejsu użytkownika (takich jak **nowy**, **Otwórz**, **Zapisz jako**,  **Drukuj** na **pliku** menu; i **kopiowania**, **Wklej**, **Cofnij** na **Edytuj** menu). Aby uzyskać więcej informacji, zobacz [Obsługa komunikatów i obiekty docelowe poleceń](../mfc/message-handling-and-command-targets.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)


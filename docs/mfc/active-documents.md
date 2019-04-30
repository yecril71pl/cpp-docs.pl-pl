---
title: Dokumenty aktywne
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
ms.openlocfilehash: 519dd51ab9b46adf862999104e97c6e478ccd86b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394952"
---
# <a name="active-documents"></a>Dokumenty aktywne

Dokumenty aktywne rozszerzenie technologii złożonego dokumentu OLE. Te rozszerzenia są udostępniane w formie dodatkowe interfejsy, które zarządzać widoków, tak aby obiekty mogą działać w kontenerach, a jeszcze zachowuje się kontrolę nad ich wyświetlania i funkcji drukowania. Ten proces umożliwia wyświetlanie dokumentów, zarówno w ramkach obcy (na przykład Microsoft Office Binder ani Microsoft Internet Explorer), jak i w ramek natywnych (takich jak porty widoku w produkcie).

W tej sekcji opisano funkcjonalności [wymagania dotyczące dokumenty aktywne](#requirements_for_active_documents). Aktywny dokument jest właścicielem zestawu danych i ma dostęp do magazynu, w którym dane można zapisać i pobrać. On można tworzyć i zarządzać jeden lub więcej widoków na jego danych. Oprócz obsługi, osadzanie zwykle i interfejsy aktywacji w miejscu dokumentów OLE, aktywny dokument komunikuje się możliwość tworzenia widoków za pośrednictwem `IOleDocument`. Za pomocą tego interfejsu kontenera można zażądać Utwórz (i ewentualnie wyliczyć) widoki, które można wyświetlić w aktywnym dokumencie. Za pośrednictwem tego interfejsu dokumencie oferuje również dodatkowych informacji na temat, takie jak czy obsługuje ona wiele widoków lub prostokąty złożonych.

Poniżej przedstawiono `IOleDocument` interfejsu. Należy pamiętać, że `IEnumOleDocumentViews` interfejs jest standardowy moduł wyliczający OLE dla `IOleDocumentView*` typów.

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

Każdy aktywny dokument musi mieć dostawcę widok ramek z tym interfejsem. Jeśli dokument nie jest zagnieżdżony w kontenerze, samego serwera aktywnego dokumentu należy podać ramki widoku. Osadzone aktywnego dokumentu w pojemniku aktywnego dokumentu kontenera zapewnia jednak ramki widoku.

Aktywny dokument można utworzyć jeden lub więcej typów [widoków](#requirements_for_view_objects) dane (na przykład, normalny, konspektu, strony układu i tak dalej). Widoki zachowywać się jak filtrów za pomocą których dane są widoczne. Nawet wtedy, gdy dokument ma tylko jeden rodzaj widoku, może nadal chcesz obsługiwać wiele widoków jako sposób obsługi nowych funkcji okna (na przykład **nowe okno** elementu na **okna** menu pakietu Office aplikacje).

##  <a name="requirements_for_active_documents"></a> Wymagania dotyczące dokumentów aktywnych

Aktywny dokument może być wyświetlany w pojemniku aktywnego dokumentu musi:

- Użyj plików złożonych OLE jako jego mechanizm magazynu przez zaimplementowanie `IPersistStorage`.

- Obsługa podstawowych funkcji osadzania OLE dokumenty, w tym **Utwórz z pliku**. Wymaga to interfejsy `IPersistFile`, `IOleObject`, i `IDataObject`.

- Obsługuje jeden lub więcej widoków, z których każdy jest w stanie aktywacji w miejscu. Oznacza to, że widoki musi obsługiwać interfejs `IOleDocumentView` oraz interfejsy `IOleInPlaceObject` i `IOleInPlaceActiveObject` (przy użyciu kontenera `IOleInPlaceSite` i `IOleInPlaceFrame` interfejsów).

- Obsługiwać interfejsy standardowa aktywnego dokumentu `IOleDocument`, `IOleCommandTarget`, i `IPrint`.

Wiedza nad tym, kiedy i jak używać interfejsów boku kontenera jest implikowane w tych wymagań.

##  <a name="requirements_for_view_objects"></a> Wymagania dotyczące obiektów widoku

Aktywny dokument można utworzyć jeden lub więcej widoków swoje dane. Funkcjonalnie te widoki są podobne porty na konkretnej metody do wyświetlania danych. Jeśli dokument aktywny obsługuje tylko jeden widok, aktywny dokument i ten pojedynczy widok można zaimplementować przy użyciu jednej klasy. `IOleDocument::CreateView` zwraca ten sam obiekt `IOleDocumentView` wskaźnika interfejsu.

Może być reprezentowana kontenera dokumentów aktywnych, musi obsługiwać składnika widoku `IOleInPlaceObject` i `IOleInPlaceActiveObject` oprócz `IOleDocumentView`:

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

Każdy widok zawiera lokacji skojarzonego widoku, który hermetyzuje ramki widoku i porcie widoku (HWND i prostokątny obszar, w tym oknie). Witryny ta funkcja udostępnia jednak standard `IOleInPlaceSite` interfejsu. Należy pamiętać, że można mieć więcej niż jeden port widok na jednym HWND.

Zazwyczaj każdy typ widoku ma inną reprezentację drukowanych. Dlatego widoków i odpowiadające im lokacje widoku powinny implementować interfejsy drukowania Jeśli `IPrint` i `IContinueCallback`, odpowiednio. Ramka widoku muszą uzgodnić z dostawcą widok za pośrednictwem `IPrint` drukowanie rozpoczęcia, więc, że nagłówki, stopki, marginesy i powiązanych elementów drukowane są poprawnie. Dostawca widoku powiadamia ramki związane z drukowaniem zdarzeń za pomocą `IContinueCallback`. Aby uzyskać więcej informacji dotyczących używania tych interfejsów, zobacz [programowe drukowanie](../mfc/programmatic-printing.md).

Należy pamiętać, że jeśli aktywny dokument obsługuje tylko jeden widok, następnie aktywny dokument i ten pojedynczy widok można zaimplementować przy użyciu jednej klasy konkretnej. `IOleDocument::CreateView` po prostu zwraca ten sam obiekt `IOleDocumentView` wskaźnika interfejsu. Krótko mówiąc nie jest konieczne, który istnieć dwa wystąpienia oddzielny obiekt gdy wymagana jest tylko jeden widok.

Obiekt widoku można także docelowym polecenia. Implementując `IOleCommandTarget` widok może odbierać polecenia, które pochodzą z kontenera interfejsu użytkownika (takie jak **New**, **Otwórz**, **Zapisz jako**,  **Drukuj** na **pliku** menu; i **kopiowania**, **Wklej**, **Cofnij** na **Edytuj** menu). Aby uzyskać więcej informacji, zobacz [obsługi komunikatów i obiekty docelowe poleceń](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Zobacz także

[Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)

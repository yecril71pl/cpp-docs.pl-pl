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
ms.openlocfilehash: cbea3e032932477006820c5a71fbbf3e40123bdf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322075"
---
# <a name="active-documents"></a>Dokumenty aktywne

Aktywne dokumenty rozszerzają technologię dokumentów złożonych OLE. Rozszerzenia te są dostarczane w postaci dodatkowych interfejsów, które zarządzają widokami, dzięki czemu obiekty mogą działać w kontenerach, a jednocześnie zachowują kontrolę nad ich funkcjami wyświetlania i drukowania. Ten proces umożliwia wyświetlanie dokumentów zarówno w ramkach obcych (takich jak Microsoft Office Binder lub Microsoft Internet Explorer) oraz w ramkach natywnych (takich jak porty widoku własnego produktu).

W tej sekcji opisano wymagania funkcjonalne [dla aktywnych dokumentów](#requirements_for_active_documents). Aktywny dokument jest właścicielem zestawu danych i ma dostęp do magazynu, w którym dane mogą być zapisywane i pobierane. Może tworzyć i zarządzać jednym lub kilkoma widokami na swoich danych. Oprócz obsługi zwykłych interfejsów osadzania i aktywacji w miejscu dokumentów OLE, aktywny dokument `IOleDocument`komunikuje swoją zdolność do tworzenia widoków za pośrednictwem programu . Za pośrednictwem tego interfejsu kontener może poprosić o utworzenie (i ewentualnie wyliczyć) widoki, które można wyświetlić aktywnego dokumentu. Za pośrednictwem tego interfejsu aktywny dokument może również dostarczyć różnych informacji o sobie, takich jak czy obsługuje wiele widoków lub złożonych prostokątów.

Poniżej znajduje `IOleDocument` się interfejs. Należy zauważyć, że `IEnumOleDocumentViews` interfejs jest standardowym `IOleDocumentView*` modułem wyliczania OLE dla typów.

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

Każdy aktywny dokument musi mieć dostawcę ramki widoku z tym interfejsem. Jeśli dokument nie jest osadzony w kontenerze, serwer aktywnych dokumentów sam musi dostarczyć ramkę widoku. Jednak gdy aktywny dokument jest osadzony w kontenerze aktywnego dokumentu, kontener udostępnia ramkę widoku.

Aktywny dokument może utworzyć jeden lub więcej typów [widoków](#requirements_for_view_objects) swoich danych (na przykład normalny, konspekt, układ strony itd.). Widoki działają jak filtry, dzięki którym dane są widoczne. Nawet jeśli dokument ma tylko jeden typ widoku, nadal można obsługiwać wiele widoków jako środek obsługi nowych funkcji okna (na przykład **nowy element okna** w menu **Okno** w aplikacjach pakietu Office).

## <a name="requirements-for-active-documents"></a><a name="requirements_for_active_documents"></a>Wymagania dotyczące aktywnych dokumentów

Aktywny dokument, który może być wyświetlany w kontenerze aktywnego dokumentu, musi:

- Użyj ole's Compound Files jako mechanizm `IPersistStorage`przechowywania poprzez wdrożenie .

- Obsługa podstawowych funkcji osadzania dokumentów OLE, w tym **tworzenie z pliku**. Wymaga to interfejsów `IPersistFile` `IOleObject`, `IDataObject`i .

- Obsługa jednego lub więcej widoków, z których każdy jest zdolny do aktywacji w miejscu. Oznacza to, że widoki `IOleDocumentView` muszą obsługiwać interfejs, jak również `IOleInPlaceObject` interfejsy i `IOleInPlaceActiveObject` (przy użyciu kontenera `IOleInPlaceSite` i `IOleInPlaceFrame` interfejsów).

- Obsługa standardowych interfejsów `IOleDocument`aktywnego `IOleCommandTarget`dokumentu `IPrint`, i .

Wiedza o tym, kiedy i jak używać interfejsów po stronie kontenera jest implikowana w tych wymaganiach.

## <a name="requirements-for-view-objects"></a><a name="requirements_for_view_objects"></a>Wymagania dotyczące wyświetlania obiektów

Aktywny dokument może utworzyć jeden lub więcej widoków swoich danych. Funkcjonalnie te widoki są jak porty na określonej metodzie wyświetlania danych. Jeśli aktywny dokument obsługuje tylko jeden widok, aktywny dokument i ten pojedynczy widok można zaimplementować przy użyciu jednej klasy. `IOleDocument::CreateView`zwraca wskaźnik `IOleDocumentView` interfejsu tego samego obiektu.

Aby być reprezentowanym w aktywnym kontenerze `IOleInPlaceObject` dokumentów, składnik widoku musi obsługiwać i `IOleInPlaceActiveObject` `IOleDocumentView`oprócz:

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

Każdy widok ma skojarzoną witrynę widoku, która hermetyzuje ramkę widoku i port widoku (HWND i prostokątny obszar w tym oknie). Witryna udostępnia tę funkcję, `IOleInPlaceSite` chociaż standardowy interfejs. Należy zauważyć, że istnieje możliwość mieć więcej niż jeden port widoku na jednym HWND.

Zazwyczaj każdy typ widoku ma inną drukowaną reprezentację. W związku z tym widoki i odpowiednie `IPrint` witryny widoku powinny implementować interfejsy drukowania, jeśli i `IContinueCallback`, odpowiednio. Ramka widoku musi negocjować `IPrint` z dostawcą widoku po rozpoczęciu drukowania, tak aby nagłówki, stopki, marginesy i powiązane elementy były drukowane poprawnie. Dostawca widoku powiadamia ramkę zdarzeń związanych `IContinueCallback`z drukowaniem za pośrednictwem programu . Aby uzyskać więcej informacji na temat korzystania z tych interfejsów, zobacz [Drukowanie programowe](../mfc/programmatic-printing.md).

Należy zauważyć, że jeśli aktywny dokument obsługuje tylko jeden widok, aktywny dokument i ten pojedynczy widok można zaimplementować przy użyciu jednej konkretnej klasy. `IOleDocument::CreateView`po prostu zwraca wskaźnik `IOleDocumentView` interfejsu tego samego obiektu. Krótko mówiąc, nie jest konieczne, aby istniały dwa oddzielne wystąpienia obiektu, gdy wymagany jest tylko jeden widok.

Obiekt widoku może być również obiektem docelowym polecenia. Implementując `IOleCommandTarget` widok może odbierać polecenia pochodzące z interfejsu użytkownika kontenera (takie jak **Nowy,** **Otwórz,** **Zapisz jako,** **Drukuj** w menu **Plik** oraz **Kopiuj,** **Wklej**, **Cofnij** w menu **Edycja).** Aby uzyskać więcej informacji, zobacz [Obsługa wiadomości i obiekty docelowe poleceń](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Zobacz też

[Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)

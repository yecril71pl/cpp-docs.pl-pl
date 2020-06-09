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
ms.openlocfilehash: bfe91dcb42b97ddfbb0bf0be36a54b45e6dc0809
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625158"
---
# <a name="active-documents"></a>Dokumenty aktywne

Aktywne dokumenty zwiększają technologię dokumentu złożonego OLE. Rozszerzenia te są dostępne w postaci dodatkowych interfejsów, które zarządzają widokami, dzięki czemu obiekty mogą działać w kontenerach, a następnie zachować kontrolę nad funkcjami wyświetlania i drukowania. Ten proces umożliwia wyświetlenie dokumentów w ramkach obcych (takich jak spinacz Microsoft Office lub program Microsoft Internet Explorer) i w ramkach natywnych (na przykład na własnych portach widoku).

W tej sekcji opisano [wymagania funkcjonalne dotyczące aktywnych dokumentów](#requirements_for_active_documents). Aktywny dokument jest właścicielem zestawu danych i ma dostęp do magazynu, w którym można zapisać i pobrać dane. Może tworzyć i zarządzać jednym lub wieloma widokami na swoich danych. Oprócz obsługi zwykłych, osadzania i w miejscu interfejsów aktywacji w dokumentach OLE, aktywny dokument komunikuje się z możliwością tworzenia widoków za pośrednictwem `IOleDocument` . Za pomocą tego interfejsu kontener może poprosił o utworzenie (i ewentualne Wyliczenie) widoków, które mogą być wyświetlane w aktywnym dokumencie. W tym interfejsie aktywny dokument może również udostępniać różne informacje o sobie, na przykład czy obsługuje wiele widoków czy złożone prostokąty.

Poniżej znajduje się `IOleDocument` interfejs. Należy pamiętać, że `IEnumOleDocumentViews` interfejs to standardowy moduł wyliczający OLE dla `IOleDocumentView*` typów.

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

Każdy aktywny dokument musi mieć dostawcy wyświetlania ramki z tym interfejsem. Jeśli dokument nie jest osadzony w kontenerze, sam serwer dokumentów musi udostępnić ramkę widoku. Jeśli jednak aktywny dokument jest osadzony w kontenerze dokumentów aktywnych, kontener zawiera ramkę widoku.

W aktywnym dokumencie można utworzyć jeden lub więcej typów [widoków](#requirements_for_view_objects) danych (na przykład normalne, konspekt, układ strony itd.). Widoki działają podobnie do filtrów, w których można zobaczyć dane. Nawet jeśli dokument zawiera tylko jeden typ widoku, można nadal obsługiwać wiele widoków jako sposób obsługi nowych funkcji okna (na przykład **nowy element okna** w menu **okno** w aplikacjach pakietu Office).

## <a name="requirements-for-active-documents"></a><a name="requirements_for_active_documents"></a>Wymagania dotyczące dokumentów aktywnych

Aktywny dokument, który może być wyświetlany w kontenerze aktywnego dokumentu, musi:

- Użyj plików złożonych OLE jako mechanizmu magazynu przez implementację `IPersistStorage` .

- Obsługa podstawowych funkcji osadzania dokumentów OLE, w tym **tworzenia plików z pliku**. Wymaga to interfejsów `IPersistFile` , `IOleObject` i `IDataObject` .

- Obsługa jednego lub kilku widoków, z których każdy jest w stanie aktywować w miejscu. Oznacza to, że widoki muszą obsługiwać interfejs, `IOleDocumentView` a także interfejsy `IOleInPlaceObject` i `IOleInPlaceActiveObject` (przy użyciu kontenerów `IOleInPlaceSite` i `IOleInPlaceFrame` interfejsów).

- Obsługa standardowych interfejsów dokumentów aktywnych `IOleDocument` , `IOleCommandTarget` i `IPrint` .

Informacje o tym, kiedy i jak używać interfejsów po stronie kontenera, są implikowane w tych wymaganiach.

## <a name="requirements-for-view-objects"></a><a name="requirements_for_view_objects"></a>Wymagania dotyczące obiektów widoków

Aktywny dokument może utworzyć jeden lub więcej widoków swoich danych. Funkcjonalnie te widoki są podobne do portów na konkretną metodę wyświetlania danych. Jeśli aktywny dokument obsługuje tylko jeden widok, aktywny dokument i ten pojedynczy widok można zaimplementować przy użyciu pojedynczej klasy. `IOleDocument::CreateView`Zwraca wskaźnik interfejsu tego samego obiektu `IOleDocumentView` .

Aby można było przedstawić w kontenerze dokumentów aktywnych, składnik widoku musi obsługiwać `IOleInPlaceObject` i `IOleInPlaceActiveObject` oprócz `IOleDocumentView` :

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

Każdy widok ma skojarzoną witrynę widoku, która hermetyzuje ramkę widoku i port widoku (HWND i prostokątny obszar w tym oknie). Lokacja ta udostępnia tę funkcję, chociaż standardowym `IOleInPlaceSite` interfejsem. Należy zauważyć, że istnieje więcej niż jeden port widoku na pojedynczym HWND.

Zazwyczaj każdy typ widoku ma inną reprezentację wydrukowaną. W związku z tym widoki i odpowiednie witryny widoku powinny implementować interfejsy drukowania, jeśli są `IPrint` `IContinueCallback` odpowiednio i. Po rozpoczęciu drukowania ramka widoku musi być negocjowana z dostawcą widoku, `IPrint` Aby nagłówki, stopki, marginesy i powiązane elementy były prawidłowo drukowane. Dostawca widoku powiadamia ramkę o zdarzeniach związanych z drukowaniem za pomocą programu `IContinueCallback` . Aby uzyskać więcej informacji na temat korzystania z tych interfejsów, zobacz [Drukowanie programistyczne](programmatic-printing.md).

Należy pamiętać, że jeśli aktywny dokument obsługuje tylko jeden widok, wówczas aktywny dokument i ten pojedynczy widok można zaimplementować przy użyciu jednej konkretnej klasy. `IOleDocument::CreateView`po prostu zwraca wskaźnik interfejsu tego samego obiektu `IOleDocumentView` . W krótkim czasie nie jest konieczne, aby istniały dwa oddzielne wystąpienia obiektów, gdy wymagany jest tylko jeden widok.

Obiekt widoku może być również elementem docelowym polecenia. Zaimplementowanie `IOleCommandTarget` widoku może odbierać polecenia, które pochodzą z interfejsu użytkownika kontenera (na przykład **New**, Open, **Save as**, **Print** w menu **plik** , a **następnie** **Kopiuj**, **Wklej**, **Cofnij** w menu **Edycja** ). Aby uzyskać więcej informacji, zobacz [Obsługa komunikatów i obiekty docelowe poleceń](message-handling-and-command-targets.md).

## <a name="see-also"></a>Zobacz też

[Zawieranie dokumentów aktywnych](active-document-containment.md)

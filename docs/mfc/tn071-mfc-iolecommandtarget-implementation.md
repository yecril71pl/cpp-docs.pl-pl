---
title: 'TN071: Implementacja MFC IOleCommandTarget'
ms.date: 06/28/2018
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: 7077211396c68750d47b91c7b2bb113370990f62
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511101"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: Implementacja MFC IOleCommandTarget

> [!NOTE]
> Następująca Uwaga techniczna nie została zaktualizowana, ponieważ została najpierw uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zalecamy wyszukiwanie tematu zainteresowania w indeksie dokumentacji online.

`IOleCommandTarget` Interfejs umożliwia obiektom i ich kontenerom Wysyłanie poleceń do siebie nawzajem. Na przykład paski narzędzi obiektu mogą zawierać przyciski poleceń takich jak `Print`, `Print Preview`, `Save`, `New`i `Zoom`. Jeśli taki obiekt został osadzony w kontenerze, który `IOleCommandTarget`obsługuje, obiekt może włączyć jego przyciski i przekazywać polecenia do kontenera w celu przetworzenia, gdy użytkownik je kliknął. Jeśli kontener chciał na wydrukowanie samego obiektu osadzonego, może on wykonać to żądanie przez wysłanie polecenia za pomocą `IOleCommandTarget` interfejsu osadzonego obiektu.

`IOleCommandTarget`jest interfejsem podobnym do automatyzacji, który jest używany przez klienta do wywoływania metod na serwerze. Jednak użycie `IOleCommandTarget` oszczędza obciążenie związane z wykonywaniem wywołań za pośrednictwem interfejsów automatyzacji, `IDispatch`ponieważ programiści nie muszą korzystać z `Invoke` zazwyczaj kosztownej metody.

W MFC `IOleCommandTarget` interfejs jest używany przez serwery dokumentów aktywnych do zezwalania kontenerów dokumentów do wysyłania poleceń na serwer. Klasa `CDocObjectServerItem`aktywnego dokumentu,, używa map interfejsu MFC (zobacz [TN038: Implementacja](../mfc/tn038-mfc-ole-iunknown-implementation.md)MFC/OLE IUnknown, `IOleCommandTarget` aby zaimplementować interfejs.

`IOleCommandTarget`jest również zaimplementowany w `COleFrameHook` klasie. `COleFrameHook`jest niezaudokumentowaną klasą MFC, która implementuje funkcje okna ramki w kontenerach edytowania w miejscu. `COleFrameHook`używa również map interfejsu MFC do zaimplementowania `IOleCommandTarget` interfejsu. `COleFrameHook`Implementacja `IOleCommandTarget` poleceń OLE przesyłania dalej do `COleDocObjectItem`pochodnych kontenerów dokumentów aktywnych. Dzięki temu wszystkie kontenery aktywnego dokumentu MFC mogą odbierać komunikaty z zawartych w nich aktywnych serwerów dokumentów.

## <a name="mfc-ole-command-maps"></a>Mapy poleceń OLE MFC

Deweloperzy MFC mogą korzystać z `IOleCommandTarget` zalet przy użyciu map poleceń OLE MFC. Mapy poleceń OLE są podobne do map komunikatów, ponieważ mogą służyć do mapowania poleceń OLE do funkcji składowych klasy, która zawiera mapę poleceń. Aby wykonać to działanie, umieść makra na mapie poleceń, aby określić grupę poleceń OLE polecenia, które chcesz obsłużyć, polecenie OLE i identyfikator polecenia komunikatu [WM_COMMAND](/windows/win32/menurc/wm-command) , który zostanie wysłany po odebraniu polecenia OLE. MFC udostępnia również wiele wstępnie zdefiniowanych makr dla standardowych poleceń OLE. Aby zapoznać się z listą standardowych poleceń OLE, które zostały pierwotnie zaprojektowane do użytku z aplikacjami Microsoft Office, zobacz Wyliczenie OLECMDID zdefiniowane w docobj. h.

Gdy polecenie OLE jest odbierane przez aplikację MFC, która zawiera mapę poleceń OLE, MFC próbuje znaleźć identyfikator polecenia i grupę poleceń dla żądanego polecenia na mapie poleceń OLE aplikacji. W przypadku znalezienia dopasowania komunikat WM_COMMAND jest wysyłany do aplikacji zawierającej mapę poleceń z IDENTYFIKATORem żądanego polecenia. (Zobacz Opis `ON_OLECMD` poniżej). W ten sposób polecenia OLE wysyłane do aplikacji są włączane do komunikatów WM_COMMAND przez MFC. Komunikaty WM_COMMAND są następnie kierowane przez mapy komunikatów aplikacji przy użyciu standardowej architektury [ROUTINGU](../mfc/command-routing.md) MFC.

W przeciwieństwie do map komunikatów mapy poleceń OLE MFC nie są obsługiwane przez ClassWizard. Deweloperzy MFC muszą ręcznie dodać obsługę map poleceń OLE i poleceń OLE. Mapy poleceń OLE można dodać do serwerów dokumentów Active Document MFC w dowolnej klasie, która znajduje się w łańcuchu routingu komunikatów WM_COMMAND w chwili, gdy aktywny dokument jest aktywny w kontenerze. Te klasy obejmują klasy aplikacji pochodne od [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md)i [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). W kontenerach dokumentów aktywnych mapy poleceń OLE można dodawać tylko do klasy pochodnej [metody COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md). Ponadto w kontenerach dokumentów aktywnych komunikaty WM_COMMAND są wysyłane tylko do mapy komunikatów w `COleDocObjectItem`klasie pochodnej.

## <a name="ole-command-map-macros"></a>Makra mapy poleceń OLE

Aby dodać funkcję mapowania poleceń do klasy, użyj następujących makr:

```cpp
DECLARE_OLECMD_MAP ()
```

To makro znajduje się w deklaracji klasy (zwykle w pliku nagłówkowym) klasy, która zawiera mapę poleceń.

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*theClass*<br/>
Nazwa klasy, która zawiera mapę poleceń.

*baseClass*<br/>
Nazwa klasy podstawowej klasy, która zawiera mapę poleceń.

To makro oznacza początek mapy poleceń. Użyj tego makra w pliku implementacji dla klasy, która zawiera mapę poleceń.

```
END_OLECMD_MAP()
```

To makro oznacza koniec mapy poleceń. Użyj tego makra w pliku implementacji dla klasy, która zawiera mapę poleceń. Makro musi być zawsze zgodne z makrem BEGIN_OLECMD_MAP.

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
Wskaźnik na identyfikator GUID grupy poleceń polecenia OLE. Ten parametr ma **wartość null** dla standardowej grupy poleceń OLE.

*olecmdid*<br/>
Identyfikator polecenia OLE polecenia do wywołania.

*id*<br/>
Identyfikator komunikatu WM_COMMAND do wysłania do aplikacji zawierającej mapę poleceń, gdy zostanie wywołane to polecenie OLE.

Za pomocą makra ON_OLECMD na mapie poleceń Dodaj wpisy dla poleceń OLE, które chcesz obsłużyć. Po odebraniu poleceń OLE zostaną one przekonwertowane do określonego komunikatu WM_COMMAND i kierowane przez mapę komunikatów aplikacji przy użyciu standardowej architektury routingu polecenia MFC.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dodać funkcję obsługi poleceń OLE do serwera aktywnego dokumentu MFC, aby obsłużyć polecenie OLE [OLECMDID_PRINT](/windows/win32/api/docobj/ne-docobj-olecmdid) . W tym przykładzie przyjęto założenie, że użyto AppWizard do wygenerowania aplikacji MFC, która jest aktywnym serwerem dokumentów.

1. `CView`W pliku nagłówkowym klasy pochodnej Dodaj makro DECLARE_OLECMD_MAP do deklaracji klasy.

    > [!NOTE]
    > Użyj klasy `CView`pochodnej, ponieważ jest ona jedną z klas na aktywnym serwerze dokumentów, która znajduje się w łańcuchu routingu komunikatów WM_COMMAND.

    ```cpp
    class CMyServerView : public CView
    {
    protected: // create from serialization only
        CMyServerView();
        DECLARE_DYNCREATE(CMyServerView)
        DECLARE_OLECMD_MAP()
        // . . .
    };
    ```

2. W pliku `CView`implementacji klasy pochodnej Dodaj makra BEGIN_OLECMD_MAP i END_OLECMD_MAP:

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. Aby obsłużyć standardowe polecenie OLE do drukowania, Dodaj makro [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) do mapy poleceń, określając identyfikator polecenia OLE dla standardowego polecenia Print i **ID_FILE_PRINT** dla identyfikatora WM_COMMAND. **ID_FILE_PRINT** jest STANDARDowym identyfikatorem polecenia drukowania używanym przez generowane przez APPWIZARD aplikacje MFC:

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Należy zauważyć, że jedno ze standardowych makr poleceń OLE, zdefiniowane w afxdocob. h, może być używane zamiast makra ON_OLECMD, ponieważ **OLECMDID_PRINT** jest STANDARDowym identyfikatorem polecenia OLE. Makro ON_OLECMD_PRINT wykona takie samo zadanie jak makro ON_OLECMD pokazane powyżej.

Gdy aplikacja kontenera wysyła ten serwer polecenia **OLECMDID_PRINT** za pomocą `IOleCommandTarget` interfejsu serwera, procedura obsługi poleceń drukowania MFC zostanie wywołana na serwerze, co spowoduje, że serwer drukuje aplikację. Kod kontenera dokumentu aktywnego do wywołania polecenia Print, które zostało dodane w powyższych krokach będzie wyglądać następująco:

```cpp
void CContainerCntrItem::DoOleCmd()
{
    IOleCommandTarget *pCmd = NULL;
    HRESULT hr = E_FAIL;
    OLECMD ocm={OLECMDID_PRINT, 0};

    hr = m_lpObject->QueryInterface(
        IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if (FAILED(hr))
        return;

    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if (SUCCEEDED(hr) && (ocm.cmdf& OLECMDF_ENABLED))
    {
        //Command is available and enabled so call it
        COleVariant vIn;
        COleVariant vOut;
        hr = pCmd->Exec(NULL, OLECMDID_PRINT,
            OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);
        ASSERT(SUCCEEDED(hr));
    }
    pCmd->Release();
}
```

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

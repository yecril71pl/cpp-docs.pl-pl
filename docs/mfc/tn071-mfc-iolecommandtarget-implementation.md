---
title: 'TN071: Implementacja interfejsu MFC IOleCommandTarget'
ms.date: 06/28/2018
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: dca1183a17fe8f3022f517d1ad0c3932ea272417
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168001"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: Implementacja interfejsu MFC IOleCommandTarget

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

`IOleCommandTarget` Interfejs umożliwia obiektów i kontenerów, ich do wysyłania poleceń do siebie nawzajem. Na przykład obiekt pasków narzędzi może zawierać przyciski dla poleceń takich jak `Print`, `Print Preview`, `Save`, `New`, i `Zoom`. Jeśli taki obiekt zostały osadzone w kontenerze, który obsługuje `IOleCommandTarget`, umożliwiające jej przyciski i przekazywać poleceń do kontenera do przetwarzania, gdy użytkownik kliknął ich obiektu. Jeśli kontener chce osadzonego obiektu, aby wydrukował sam siebie, można przesłać to żądanie, wysyłając polecenie za pośrednictwem `IOleCommandTarget` interfejsu osadzonego obiektu.

`IOleCommandTarget` jest interfejsem podobne do automatyzacji, w tym, że jest używany przez klienta do wywołania metody na serwerze. Jednak przy użyciu `IOleCommandTarget` zapisuje narzut na wykonywanie wywołań za pośrednictwem interfejsów automatyzacji, ponieważ programiści nie ma potrzeby używania zazwyczaj kosztowne `Invoke` metody `IDispatch`.

W MFC `IOleCommandTarget` interfejs jest używany przez serwery dokumentów aktywnych w celu umożliwienia kontenery dokumentów aktywnych wysyłanie poleceń do serwera. Klasa serwera aktywnego dokumentu, `CDocObjectServerItem`, przy użyciu map interfejsu MFC (zobacz [TN038: Implementacja interfejsu IUnknown MFC/OLE](../mfc/tn038-mfc-ole-iunknown-implementation.md)) do zaimplementowania `IOleCommandTarget` interfejsu.

`IOleCommandTarget` jest również implementowana w `COleFrameHook` klasy. `COleFrameHook` jest nieudokumentowane klasy MFC, który implementuje funkcje ramki okna kontenerów edycji w miejscu. `COleFrameHook` mapy interfejsów biblioteki MFC używa również zaimplementować `IOleCommandTarget` interfejsu. `COleFrameHook`w implementacji `IOleCommandTarget` przekazuje polecenia OLE, aby `COleDocObjectItem`-pochodnych kontenery dokumentów aktywnych. Dzięki temu wszystkie MFC aktywny kontener dokumentu odbierać komunikaty z serwery dokumentów aktywnych zawarte.

## <a name="mfc-ole-command-maps"></a>Mapy poleceń OLE MFC

MFC, deweloperzy mogą korzystać z `IOleCommandTarget` przy użyciu MFC OLE polecenia mapy. Mapy poleceń OLE są takie jak mapy wiadomości, ponieważ może służyć do mapowania polecenia OLE do składowych klasy, która zawiera mapę polecenia. Aby działało, umieść makra w mapie polecenie, aby określić grupę polecenia OLE, polecenia, które ma obsługiwać, polecenia OLE i identyfikator polecenia [WM_COMMAND](/windows/desktop/menurc/wm-command) komunikat, który zostanie wysłany, po odebraniu polecenia OLE. MFC udostępnia szereg wstępnie zdefiniowanych makr dla standardowych poleceń OLE. Lista OLE standardowych poleceń, które zostały pierwotnie zaprojektowane dla za pomocą aplikacji Microsoft Office, zobacz wyliczenie OLECMDID, która jest zdefiniowana w docobj.h.

Po odebraniu przez aplikację MFC, która zawiera mapę polecenia OLE polecenia OLE MFC próbuje znaleźć identyfikator polecenia i grupy poleceń dla żądanego polecenia w mapie polecenia OLE w aplikacji. Jeśli zostanie znalezione dopasowanie, komunikatów WM_COMMAND jest wywoływane z aplikacją zawierającą mapy polecenia o identyfikatorze żądane polecenie. (Zobacz opis `ON_OLECMD` poniżej.) W ten sposób OLE polecenia wysyłane do aplikacji są przekształcane w wm_command — komunikaty przez MFC. Wm_command — komunikaty są następnie wysyłane za pośrednictwem aplikacji mapy komunikatów przy użyciu standardu MFC [routing poleceń](../mfc/command-routing.md) architektury.

W przeciwieństwie do mapy komunikatów mapy poleceń MFC OLE nie są obsługiwane przez ClassWizard. Deweloperzy MFC należy dodać ręcznie Obsługa mapy polecenia OLE i wpisy mapy polecenia OLE. Polecenia OLE, które mapy mogą być dodawane do biblioteki MFC aktywnych serwerów dokumentu w każdej klasy, która jest w łańcuchu routing komunikatów WM_COMMAND w chwili aktywny dokument jest aktywny w miejscu w kontenerze. Tych klas obejmują klasy pochodne klasy aplikacji [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md), i [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). Kontenery dokumentów aktywnych mapy poleceń OLE może być dodana tylko do [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)-klasy pochodnej. Ponadto w kontenerach dokumentów aktywnych wm_command — komunikaty zostanie tylko skierowane do mapy wiadomości w `COleDocObjectItem`-klasy pochodnej.

## <a name="ole-command-map-macros"></a>Makra mapy polecenia OLE

Aby dodać funkcje mapy polecenia do klasy, użyj następujących makr:

```cpp
DECLARE_OLECMD_MAP ()
```

To makro jest przesyłany w deklaracji klasy (zwykle znajduje się w pliku nagłówka), klasy, która zawiera mapę polecenia.

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*theClass*<br/>
Nazwa klasy, która zawiera mapę polecenia.

*baseClass*<br/>
Nazwa klasy podstawowej klasy, która zawiera mapę polecenia.

To makro oznacza początek mapy polecenia. Użyj tego makra w pliku implementacji dla klasy, która zawiera mapę polecenia.

```
END_OLECMD_MAP()
```

To makro oznacza koniec mapy polecenia. Użyj tego makra w pliku implementacji dla klasy, która zawiera mapę polecenia. To makro, zawsze należy wykonać makro BEGIN_OLECMD_MAP.

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
Wskaźnik na identyfikator GUID grupy poleceń polecenia OLE. Ten parametr jest **NULL** grupy standardowe polecenia OLE.

*olecmdid*<br/>
Identyfikator polecenia OLE polecenie do wywołania.

*id*<br/>
Identyfikator komunikatu WM_COMMAND do wysłania do aplikacji zawierającej mapy polecenia podczas wywoływania tego polecenia OLE.

Użyj ON_OLECMD — makro w mapie polecenie, aby dodać wpisy dla polecenia OLE, którą chcesz obsługiwać. Po odebraniu polecenia OLE, będzie można przekonwertować na określony komunikat WM_COMMAND i przesyłane za pośrednictwem aplikacji mapy komunikatów przy użyciu architektury standardowego routingu poleceń MFC.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dodać funkcję obsługi polecenia OLE do serwer MFC aktywnego dokumentu do obsługi [OLECMDID_PRINT](/windows/desktop/api/docobj/ne-docobj-olecmdid) polecenia OLE. W tym przykładzie przyjęto założenie, używany przez kreatora AppWizard do generowania aplikacji MFC, który jest serwerem aktywnym dokumencie.

1. W swojej `CView`-pochodne klasy nagłówka pliku, Dodaj makro DECLARE_OLECMD_MAP do deklaracji klasy.

    > [!NOTE]
    > Użyj `CView`-klasy pochodnej, ponieważ jest to jeden z klas w serwera aktywnego dokumentu, który znajduje się w łańcuchu routing komunikatów WM_COMMAND.

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

2. W pliku implementacji dla `CView`-klasy, Dodaj BEGIN_OLECMD_MAP i END_OLECMD_MAP makra:

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. Aby obsłużyć standardowe polecenia drukowania OLE, należy dodać [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) makra do mapy polecenie, podając identyfikator polecenia OLE standardowe polecenia drukowania i **ID_FILE_PRINT** dla identyfikatora WM_COMMAND. **ID_FILE_PRINT** to standard identyfikator polecenia drukowania używane przez aplikacje wygenerowane przez kreatora biblioteki MFC:

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Należy pamiętać, że jeden standardowy makra poleceń OLE zdefiniowane w afxdocob.h, może zostać wykorzystana zamiast ON_OLECMD — makro ponieważ **OLECMDID_PRINT** jest standardowy identyfikator polecenia OLE. ON_OLECMD_PRINT — makro spowoduje wykonanie tych samych zadań ON_OLECMD — makro przedstawionych powyżej.

Gdy aplikacja kontenera wysyła ten serwer **OLECMDID_PRINT** polecenia przez ten serwer `IOleCommandTarget` interfejsu, MFC, drukowanie procedury obsługi polecenia zostanie wywołana na serwerze, powodując serwera wydrukować aplikacji. Kontener dokumentów aktywnych kodu w celu wywołania polecenia drukowania, dodane w powyższych krokach będzie wyglądać mniej więcej tak:

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

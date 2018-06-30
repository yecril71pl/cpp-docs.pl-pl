---
title: 'Tn071 implementacja interfejsu: MFC iolecommandtarget — implementacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IOleCommandTarget
dev_langs:
- C++
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ebd796690407fe0e65bc790c52477c7e4d149250
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122624"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: implementacja interfejsu MFC IOleCommandTarget

> [!NOTE]
> Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.

`IOleCommandTarget` Interfejs umożliwia obiektów i kontenerów ich wysłania polecenia ze sobą. Na przykład obiekt paski narzędzi mogą zawierać przyciski poleceń takich jak `Print`, `Print Preview`, `Save`, `New`, i `Zoom`. Jeśli taki obiekt zostały osadzone w kontenerze, który obsługuje `IOleCommandTarget`, umożliwiającą jej przyciski i przesłać poleceń do przetwarzania, gdy użytkownik kliknął ich kontenera obiektu. Jeśli kontener osadzonego obiektu do samej siebie drukowania, można utworzyć tego żądania, wysyłając polecenie za pośrednictwem `IOleCommandTarget` interfejsu osadzonego obiektu.

`IOleCommandTarget` Interfejs automatyzacji przypominającej się, że jest używany przez klienta do wywołania metody na serwerze. Jednak przy użyciu `IOleCommandTarget` zapisuje koszty nawiązywanie połączeń za pośrednictwem interfejsów automatyzacji, ponieważ programiści nie trzeba stosować zwykle kosztowne `Invoke` metody `IDispatch`.

W MFC `IOleCommandTarget` interfejs jest używany przez serwery dokumentów aktywnych umożliwia kontenery dokumentów aktywnych wysłania poleceń na serwerze. Klasa serwera aktywnego dokumentu, `CDocObjectServerItem`, wykorzystuje mapy interfejsu MFC (zobacz [TN038: implementacja MFC/OLE IUnknown](../mfc/tn038-mfc-ole-iunknown-implementation.md)) do zaimplementowania `IOleCommandTarget` interfejsu.

`IOleCommandTarget` jest również implementowana w `COleFrameHook` klasy. `COleFrameHook` jest nieudokumentowanej klasy MFC, która implementuje funkcje okno ramowe kontenerów edycji w miejscu. `COleFrameHook` używa również mapy interfejsu MFC do zaimplementowania `IOleCommandTarget` interfejsu. `COleFrameHook`w implementacji `IOleCommandTarget` przekazuje polecenia OLE `COleDocObjectItem`-pochodnych kontenery dokumentów aktywnych. Dzięki temu wszystkie MFC Active kontener dokumentu do odbierania wiadomości z serwery dokumentów aktywnych zawartych w niej.

## <a name="mfc-ole-command-maps"></a>Mapy poleceń OLE MFC

MFC programiści mogą wykorzystać `IOleCommandTarget` przy użyciu MFC OLE poleceń mapy. Mapy poleceń OLE są takie jak mapy wiadomości, ponieważ można ich używać do mapowania poleceń OLE do funkcji Członkowskich klasy, która zawiera mapy polecenia. Aby działało, umieść makra w mapy polecenia, aby określić grupę polecenia OLE polecenia mają być obsługiwane, polecenia OLE i identyfikator polecenia [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) komunikat, który będą wysyłane po odebraniu polecenia OLE. MFC udostępnia szereg wstępnie zdefiniowane makra dla standardowych poleceń OLE. Listę standardowych OLE poleceń, które pierwotnie zostały zaprojektowane dla korzystać z aplikacji Microsoft Office, zobacz wyliczenie OLECMDID, który jest zdefiniowany w docobj.h.

Po odebraniu polecenia OLE MFC aplikacji, które zawiera mapy polecenia OLE MFC próbuje znaleźć Identyfikatora polecenia i grupy poleceń dla żądanego polecenia w mapie polecenia OLE aplikacji. W przypadku odnalezienia pasującego komunikatów WM_COMMAND jest wysyłane do zawierającego mapy polecenia o identyfikatorze żądanej aplikacji. (Zobacz opis `ON_OLECMD` poniżej.) W ten sposób OLE polecenia wysyłane do aplikacji są przekształcane w WM_COMMAND — komunikaty przez MFC. WM_COMMAND — komunikaty są następnie wysyłane za pośrednictwem mapy komunikatów aplikacji przy użyciu standardowego MFC [routing poleceń](../mfc/command-routing.md) architektury.

W przeciwieństwie do mapy komunikatów mapy poleceń MFC OLE nie są obsługiwane przez ClassWizard. Deweloperzy MFC należy dodać ręcznie obsługi mapy polecenia oraz wpisy mapy polecenia OLE. Polecenie OLE map mogą być dodawane do MFC aktywnych serwerów dokumentu w dowolnej klasy, który znajduje się w łańcuchu routing komunikatów WM_COMMAND w czasie aktywny dokument jest aktywny w miejscu w kontenerze. Te klasy mają aplikacji klasy pochodzące od [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md), i [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). Kontenery dokumentów aktywnych mapy poleceń OLE można być dodana tylko do [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)-klasy. Ponadto w kontenerach dokumentów aktywnych komunikatów WM_COMMAND zostanie tylko skierowane do mapy wiadomości w `COleDocObjectItem`-klasy.

## <a name="ole-command-map-macros"></a>Makra mapy polecenia OLE

Aby dodać funkcję mapy polecenia do klasy, należy użyć następujące makra:

```cpp
DECLARE_OLECMD_MAP ()
```

To makro przejdzie w deklaracji klasy (zwykle w pliku nagłówka) klasę, która zawiera mapy polecenia.

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*theClass*  
 Nazwa klasy zawierającej mapy polecenia.

*baseclass —*  
 Nazwa klasy podstawowej klasy, która zawiera mapy polecenia.

To makro oznacza początek mapy polecenia. Użyj tego makra w pliku implementacji klasy, która zawiera mapy polecenia.

```
END_OLECMD_MAP()
```

To makro oznacza koniec mapy polecenia. Użyj tego makra w pliku implementacji klasy, która zawiera mapy polecenia. To makro musi zawsze występować po makro BEGIN_OLECMD_MAP.

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*  
 Wskaźnik do identyfikator GUID grupy poleceń polecenia OLE. Ten parametr jest **NULL** grupy standardowe polecenia OLE.

*olecmdid*  
 Identyfikator polecenia OLE polecenie do wywołania.

*id*  
 Identyfikator komunikatu WM_COMMAND przesyłany do aplikacji zawierającego mapy polecenia po wywołaniu tego polecenia OLE.

Użyj on_olecmd — makro w mapie polecenie, aby dodać wpisy dla polecenia OLE, które mają być obsługiwane. Po odebraniu polecenia OLE, będzie można przekonwertować na określony komunikat WM_COMMAND i przekazywane mapę komunikatów w aplikacji przy użyciu architektury standardowy routing poleceń MFC.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dodać funkcję obsługi polecenia OLE do MFC aktywnego serwera dokumentu do obsługi [OLECMDID_PRINT](http://msdn.microsoft.com/library/windows/desktop/ms691264) polecenia OLE. W tym przykładzie przyjęto założenie, używane kreatorami AppWizard do generowania aplikacji MFC, który jest serwerem aktywnym dokumencie.

1. W Twojej `CView`-pochodnej klasy nagłówka pliku, Dodaj makro DECLARE_OLECMD_MAP do deklaracji klasy.

    > [!NOTE]
    > Użyj `CView`-klasie pochodnej, ponieważ jest to jeden z klas w serwer dokumentów aktywnych, który znajduje się w łańcuchu routing komunikatów WM_COMMAND.

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

3. Aby obsłużyć standardowe polecenia print OLE, należy dodać [on_olecmd —](reference/message-map-macros-mfc.md#on_olecmd) makra mapy polecenia, podając identyfikator polecenia OLE standardowe polecenia wydruku i **id_file_print —** dla identyfikatora WM_COMMAND. **Id_file_print —** jest standardem identyfikator polecenia drukowania używane przez aplikacje generowane z kreatorami AppWizard MFC:

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Pamiętaj, że jeden standardowy makra poleceń OLE zdefiniowane w afxdocob.h, może być stosowane zamiast on_olecmd — makro ponieważ **OLECMDID_PRINT** jest identyfikatorem standardowe polecenia OLE On_olecmd_print — makro będzie wykonywać tych samych zadań on_olecmd — makro przedstawionych powyżej.

Gdy aplikacji kontenera wysyła ten serwer **OLECMDID_PRINT** polecenia za pomocą serwera `IOleCommandTarget` interfejsu, MFC Drukowanie programu obsługi poleceń zostanie wywołany, na serwerze, powoduje serwera do drukowania aplikacji. Kontener dokumentów aktywnych kodu do wywołania polecenia print dodane w powyższych krokach będzie wyglądać mniej więcej tak:

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

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)  
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)  

---
title: 'Tn071 implementacja interfejsu: MFC iolecommandtarget — implementacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 21745762fb6f6eb1eb324013db12207c4b3b81d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: implementacja interfejsu MFC IOleCommandTarget
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 `IOleCommandTarget` Interfejs umożliwia obiektów i kontenerów ich wysłania polecenia ze sobą. Na przykład obiekt paski narzędzi mogą zawierać przyciski poleceń takich jak **drukowania**, **Podgląd wydruku**, **zapisać**, `New`, i **powiększenia**. Jeśli taki obiekt zostały osadzone w kontenerze, który obsługuje `IOleCommandTarget`, umożliwiającą jej przyciski i przesłać poleceń do przetwarzania, gdy użytkownik kliknął ich kontenera obiektu. Jeśli kontener osadzonego obiektu do samej siebie drukowania, można utworzyć tego żądania, wysyłając polecenie za pośrednictwem `IOleCommandTarget` interfejsu osadzonego obiektu.  
  
 `IOleCommandTarget` Interfejs automatyzacji przypominającej się, że jest używany przez klienta do wywołania metody na serwerze. Jednak przy użyciu `IOleCommandTarget` zapisuje koszty nawiązywanie połączeń za pośrednictwem interfejsów automatyzacji, ponieważ programiści nie trzeba stosować zwykle kosztowne `Invoke` metody `IDispatch`.  
  
 W MFC `IOleCommandTarget` interfejs jest używany przez serwery dokumentów aktywnych umożliwia kontenery dokumentów aktywnych wysłania poleceń na serwerze. Klasa serwera aktywnego dokumentu, `CDocObjectServerItem`, wykorzystuje mapy interfejsu MFC (zobacz [TN038: implementacja MFC/OLE IUnknown](../mfc/tn038-mfc-ole-iunknown-implementation.md)) do zaimplementowania `IOleCommandTarget` interfejsu.  
  
 `IOleCommandTarget` jest również implementowana w **COleFrameHook** klasy. **COleFrameHook** nieudokumentowanej klasy MFC, która implementuje funkcje okno ramowe w miejscu edytuje kontenerów. **COleFrameHook** również używa mapy interfejsu MFC do implementacji `IOleCommandTarget` interfejsu. **COleFrameHook**w implementacji `IOleCommandTarget` przekazuje polecenia OLE `COleDocObjectItem`-pochodnych kontenery dokumentów aktywnych. Dzięki temu wszystkie MFC Active kontener dokumentu do odbierania wiadomości z serwery dokumentów aktywnych zawartych w niej.  
  
## <a name="mfc-ole-command-maps"></a>Mapy poleceń OLE MFC  
 MFC programiści mogą wykorzystać `IOleCommandTarget` przy użyciu MFC OLE poleceń mapy. Mapy poleceń OLE są takie jak mapy wiadomości, ponieważ można ich używać do mapowania poleceń OLE do funkcji Członkowskich klasy, która zawiera mapy polecenia. Aby działało, umieść makra w mapy polecenia, aby określić grupę polecenia OLE polecenia mają być obsługiwane, polecenia OLE i identyfikator polecenia [WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) komunikat, który będą wysyłane po odebraniu polecenia OLE. MFC udostępnia szereg wstępnie zdefiniowane makra dla standardowych poleceń OLE. Listę standardowych OLE poleceń, które pierwotnie zostały zaprojektowane dla korzystać z aplikacji Microsoft Office, zobacz wyliczenie OLECMDID, który jest zdefiniowany w docobj.h.  
  
 Po odebraniu polecenia OLE MFC aplikacji, które zawiera mapy polecenia OLE MFC próbuje znaleźć Identyfikatora polecenia i grupy poleceń dla żądanego polecenia w mapie polecenia OLE aplikacji. W przypadku odnalezienia pasującego **WM_COMMAND** komunikat jest wysyłany do aplikacji zawierającego mapy polecenia o identyfikatorze żądane polecenie. (Zobacz opis `ON_OLECMD` poniżej.) W ten sposób OLE polecenia wysyłane do aplikacji są przekształcane w **WM_COMMAND** wiadomości przez MFC. **WM_COMMAND** komunikaty są następnie wysyłane za pośrednictwem mapy komunikatów aplikacji przy użyciu standardowego MFC [routing poleceń](../mfc/command-routing.md) architektury.  
  
 W przeciwieństwie do mapy komunikatów mapy poleceń MFC OLE nie są obsługiwane przez ClassWizard. Deweloperzy MFC należy dodać ręcznie obsługi mapy polecenia oraz wpisy mapy polecenia OLE. OLE mapy poleceń mogą być dodawane do biblioteki MFC aktywnych serwerów dokumentu w dowolnej klasy, który znajduje się w **WM_COMMAND** łańcucha rozsyłania wiadomości w czasie aktywny dokument jest aktywny w miejscu w kontenerze. Te klasy mają aplikacji klasy pochodzące od [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md), i [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). Kontenery dokumentów aktywnych mapy poleceń OLE można być dodana tylko do [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)-klasy. Ponadto w kontenerach dokumentów aktywnych **WM_COMMAND** wiadomości tylko zostanie wysłany do mapy wiadomości w `COleDocObjectItem`-klasy.  
  
## <a name="ole-command-map-macros"></a>Makra mapy polecenia OLE  
 Aby dodać funkcję mapy polecenia do klasy, należy użyć następujące makra:  
  
```  
 
DECLARE_OLECMD_MAP ()  
 
```  
  
 To makro przejdzie w deklaracji klasy (zwykle w pliku nagłówka) klasę, która zawiera mapy polecenia.  
  
```  
 
BEGIN_OLECMD_MAP(
theClass  ,   baseClass)  
 
```  
  
 `theClass`  
 Nazwa klasy zawierającej mapy polecenia.  
  
 `baseClass`  
 Nazwa klasy podstawowej klasy, która zawiera mapy polecenia.  
  
 To makro oznacza początek mapy polecenia. Użyj tego makra w pliku implementacji klasy, która zawiera mapy polecenia.  
  
```  
 
END_OLECMD_MAP()  
 
```  
  
 To makro oznacza koniec mapy polecenia. Użyj tego makra w pliku implementacji klasy, która zawiera mapy polecenia. Zawsze należy wykonać to makro **BEGIN_OLECMD_MAP** makra.  
  
```  
 
ON_OLECMD(
pguid  ,   
olecmdid  ,
    id)  
 
```  
  
 `pguid`  
 Wskaźnik do identyfikator GUID grupy poleceń polecenia OLE. Ten parametr jest **NULL** grupy standardowe polecenia OLE.  
  
 *olecmdid*  
 Identyfikator polecenia OLE polecenie do wywołania.  
  
 `id`  
 Identyfikator **WM_COMMAND** do wysłania do aplikacji zawierającego mapy polecenia po wywołaniu tego polecenia OLE.  
  
 Użyj `ON_OLECMD` makra w mapie polecenie do dodania wpisów dla OLE polecenia mają być obsługiwane. Po odebraniu polecenia OLE, będzie można przekonwertować na określony **WM_COMMAND** wiadomości i kierowany przez mapę komunikatów w aplikacji przy użyciu architektury standardowy routing poleceń MFC.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak dodać funkcję obsługi polecenia OLE do MFC aktywnego serwera dokumentu do obsługi [OLECMDID_PRINT](http://msdn.microsoft.com/library/windows/desktop/ms691264) polecenia OLE. W tym przykładzie przyjęto założenie, używane kreatorami AppWizard do generowania aplikacji MFC, który jest serwerem aktywnym dokumencie.  
  
1.  W Twojej `CView`-nagłówka klasy pochodnej plików, dodawanie `DECLARE_OLECMD_MAP` makro deklaracji klasy.  
  
    > [!NOTE]
    >  Użyj `CView`-klasie pochodnej, ponieważ jest to jeden z klas w serwer dokumentów aktywnych, który znajduje się w **WM_COMMAND** łańcucha rozsyłania wiadomości.  
  
 ```  
    class CMyServerView : public CView  
 {  
    protected: // create from serialization only  
    CMyServerView();
DECLARE_DYNCREATE(CMyServerView)  
    DECLARE_OLECMD_MAP() 
 . . .  
 };  
 ```  
  
2.  W pliku implementacji dla `CView`-klasy, Dodaj `BEGIN_OLECMD_MAP` i `END_OLECMD_MAP` makra:  
  
 ```  
    BEGIN_OLECMD_MAP(CMyServerView, CView)  
 
    END_OLECMD_MAP() 
 ```  
  
3.  Aby obsłużyć standardowe polecenia print OLE, należy dodać [on_olecmd —](reference/message-map-macros-mfc.md#on_olecmd) makra mapy polecenia, podając identyfikator polecenia OLE standardowe polecenia wydruku i **id_file_print —** dla **WM_COMMAND**  Identyfikatora. **Id_file_print —** jest standardem identyfikator polecenia drukowania używane przez aplikacje generowane z kreatorami AppWizard MFC:  
  
 ```  
    BEGIN_OLECMD_MAP(CMyServerView,
    CView)  
    ON_OLECMD(NULL,
    OLECMDID_PRINT,
    ID_FILE_PRINT) 
    END_OLECMD_MAP() 
 ```  
  
 Należy pamiętać, że jeden standardowy makra poleceń OLE zdefiniowane w afxdocob.h, można użyć zamiast `ON_OLECMD` makro ponieważ **OLECMDID_PRINT** jest identyfikatorem standardowe polecenia OLE `ON_OLECMD_PRINT` Makra będzie wykonywać tych samych zadań `ON_OLECMD` makro przedstawionych powyżej.  
  
 Gdy aplikacji kontenera wysyła ten serwer **OLECMDID_PRINT** polecenia za pomocą serwera `IOleCommandTarget` interfejsu, MFC Drukowanie programu obsługi poleceń zostanie wywołany, na serwerze, powoduje serwera do drukowania aplikacji. Kontener dokumentów aktywnych kodu do wywołania polecenia print dodane w powyższych krokach będzie wyglądać mniej więcej tak:  
  
```  
void CContainerCntrItem::DoOleCmd()  
{  
    IOleCommandTarget *pCmd = NULL;  
    HRESULT hr = E_FAIL;  
    OLECMD ocm={OLECMDID_PRINT, 0};  
 
    hr = m_lpObject->QueryInterface(IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if(FAILED(hr)) 
    return; 
 
    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if(SUCCEEDED(hr)&& (ocm.cmdf& OLECMDF_ENABLED))  
 { *//Command is available and enabled so call it  
    COleVariant vIn;  
    COleVariant vOut;  
    hr = pCmd->Exec(NULL, OLECMDID_PRINT,  
    OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);

    ASSERT(SUCCEEDED(hr));

 }  
    pCmd->Release();

} 
```  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)


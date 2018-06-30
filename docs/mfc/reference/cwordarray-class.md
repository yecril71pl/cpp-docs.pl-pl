---
title: Klasa CWordArray | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWordArray
- AFXCOLL/CWordArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
dev_langs:
- C++
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 2ba2c194-2c6c-40ff-9db4-e9dbe57e1f57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 562f0eff1470a4754d3eaac15a94d08fefb95951
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123022"
---
# <a name="cwordarray-class"></a>Klasa CWordArray
Obsługuje tablic słowa 16-bitowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CWordArray : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
 Funkcje Członkowskie `CWordArray` są podobne do funkcji Członkowskich klasy [CObArray](../../mfc/reference/cobarray-class.md). Ze względu na to podobieństwa, można użyć `CObArray` odwołania dokumentacji charakterystykę funkcja elementu członkowskiego. Po wyświetleniu [CObject](../../mfc/reference/cobject-class.md) wskaźnika jako parametr funkcji lub wartości zwracanej, Zastąp wyrazu.  
  
 `CObject* CObArray::GetAt( int <nIndex> ) const;`  
  
 na przykład umożliwia to  
  
 `WORD CWordArray::GetAt( int <nIndex> ) const;`  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Tworzy pustą tablicę.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Dodaje element do końca tablicy; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Dołącza innej tablicy do tablicy; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Kopiuje innej tablicy do tablicy; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Zwraca tymczasowego odwołanie do wskaźnika elementu w tablicy.|  
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Zwalnia wszystkie nieużywanej pamięci powyżej bieżącego górną granicę.|  
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Zwraca wartość pod danym indeksem.|  
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Pobiera liczbę elementów w tej macierzy.|  
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartości NULL.|  
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Pobiera liczbę elementów w tej macierzy.|  
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Zwraca największy nieprawidłowy indeks.|  
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Wstawia elementu (lub wszystkie elementy w innej tablicy) od określonego indeksu.|  
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Określa, czy tablica jest pusta.|  
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Usuwa wszystkie elementy z tej tablicy.|  
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Usuwa element pod określonym indeksem.|  
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Ustawia wartość dla danego indeksu; Tablica nie może wzrosnąć.|  
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Ustawia wartość dla danego indeksu; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Ustawia liczbę elementów, które mają zostać zawarte w tej macierzy.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CObArray::operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|  
  
## <a name="remarks"></a>Uwagi  
 `CWordArray` zawiera [implement_serial —](run-time-object-model-services.md#implement_serial) makro do obsługi serializacji i zrzucanie swoich elementów. Jeśli tablica słów jest przechowywany archiwum z operatorem przeciążone wstawiania lub z [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) funkcji członkowskiej, każdy element jest, więc serializacji.  
  
> [!NOTE]
>  Przed rozpoczęciem korzystania z tablicy, użyj `SetSize` jego rozmiar i przydzielić pamięci dla niego. Jeśli nie używasz `SetSize`, dodawanie elementów do macierzy powoduje jego przydzielić często i skopiować. Częste zmiany alokacji i kopiowanie są mało wydajne i można fragmentu pamięci.  
  
 Jeśli potrzebujesz zrzutu poszczególnych elementów w tablicy, należy ustawić głębokość kontekstu zrzutu do co najmniej 1.  
  
 Aby uzyskać więcej informacji na temat używania `CWordArray`, zapoznaj się z artykułem [kolekcji](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CWordArray`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcoll.h  
  
##  <a name="icommandsource_interface"></a>  Interfejs ICommandSource  
 Zarządza polecenia przesyłane z obiektem źródłowym polecenia do kontrolki użytkownika.  
  
```  
interface class ICommandSource  
```  
  
### <a name="remarks"></a>Uwagi  
 Kiedy host kontrolkę użytkownika w widoku MFC [klasy CWinFormsView](../../mfc/reference/cwinformsview-class.md) polecenia tras i aktualizacji polecenia interfejsu użytkownika wiadomości do kontrolki użytkownika, aby umożliwić jego poleceń MFC (na przykład elementów menu ramki i przycisków paska narzędzi). Implementując, mieć kontrolę użytkownika odwołanie do `ICommandSource` obiektu.  
  
 Zobacz [porady: dodawanie do formantu formularzy systemu Windows Routing poleceń](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `ICommandTarget`.  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler  
 Dodaje programem obsługi do obiektu źródłowego polecenia.  
  
```  
void AddCommandHandler(
    unsigned int cmdID,  
    CommandHandler^ cmdHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdID*  
 Identyfikator polecenia.  
  
 *cmdHandler*  
 Dojście do metody obsługi poleceń.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda dodaje program obsługi poleceń *cmdHandler* do obiektu źródłowego polecenia i mapowania programu obsługi do *cmdID*.  
  
 Zobacz [porady: dodawanie do formantu formularzy systemu Windows Routing poleceń](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `AddCommandHandler`.  
  
##  <a name="addcommandrangehandler"></a>  ICommandSource::AddCommandRangeHandler  
 Dodaje grupę programy obsługi poleceń do obiektu źródłowego polecenia.  
  
```  
void AddCommandRangeHandler(
    unsigned int cmdIDMin,  
    unsigned int cmdIDMax,  
    CommandHandler^ cmdHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdIDMin*  
 Indeks początkowy zakres Identyfikatora polecenia.  
  
 *cmdIDMax*  
 Indeks końcowy zakres Identyfikatora polecenia.  
  
 *cmdHandler*  
 Dojście do metody obsługi wiadomości zamapowany poleceń.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda mapuje ciągły zakres identyfikatorów poleceń do obsługi wiadomości i dodaje go do obiektu źródłowego polecenia. Służy to do obsługi grupy przycisków powiązane z jedną z metod.  
  
##  <a name="addcommandrangeuihandler"></a>  ICommandSource::AddCommandRangeUIHandler  
 Dodaje grupę programów obsługi wiadomości polecenia interfejsu użytkownika do obiektu źródłowego polecenia.  
  
```  
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,   
    unsigned int cmdIDMax,   
    CommandUIHandler^ cmdUIHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdIDMin*  
 Indeks początkowy zakres Identyfikatora polecenia.  
  
 *cmdIDMax*  
 Indeks końcowy zakres Identyfikatora polecenia.  
  
 *cmdHandler*  
 Dojście do metody obsługi wiadomości zamapowany poleceń.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda mapuje ciągły zakres identyfikatorów poleceń do obsługi komunikatów polecenia interfejsu pojedynczego użytkownika i dodaje go do obiektu źródłowego polecenia. Służy to do obsługi grupy przycisków powiązane z jedną z metod.  
  
##  <a name="addcommanduihandler"></a>  ICommandSource::AddCommandUIHandler  
 Dodaje program obsługi komunikatów polecenia interfejsu użytkownika do obiektu źródłowego polecenia.  
  
```  
void AddCommandUIHandler(
    unsigned int cmdID,   
    CommandUIHandler^ cmdUIHandler);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdID*  
 Identyfikator polecenia.  
  
 *cmdUIHandler*  
 Dojście do metody obsługi wiadomości polecenia interfejsu użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda dodaje obsługi wiadomości polecenia interfejsu użytkownika *cmdHandler* do obiektu źródłowego polecenia i mapowania programu obsługi do *cmdID*.  
  
##  <a name="postcommand"></a>  ICommandSource::PostCommand  
 Zapisuje komunikat bez oczekiwania na przetworzenie.  
  
```  
void PostCommand(unsigned int command);
```  
  
### <a name="parameters"></a>Parametry  
 *Polecenie*  
 Identyfikator polecenia komunikatu zaksięgowania.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda asynchronicznie zapisuje komunikat zamapowane na identyfikator określony przez *polecenia*. Wywołuje [CWnd::PostMessage](../../mfc/reference/cwnd-class.md#postmessage) do umieszczenia wiadomości w kolejki komunikatów i zwraca okna bez oczekiwania na odpowiednie okno, aby przetworzyć komunikatu.  
  
##  <a name="removecommandhandler"></a>  ICommandSource::RemoveCommandHandler  
 Usuwa programem obsługi z obiektem źródłowym polecenia.  
  
```  
void RemoveCommandHandler(unsigned int cmdID);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdID*  
 Identyfikator polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa mapowane na program obsługi poleceń *cmdID* z polecenia obiektu źródłowego.  
  
##  <a name="removecommandrangehandler"></a>  ICommandSource::RemoveCommandRangeHandler  
 Usuwa grupę programy obsługi poleceń z obiektem źródłowym polecenia.  
  
```  
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,  
    unsigned int cmdIDMax);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdIDMin*  
 Indeks początkowy zakres Identyfikatora polecenia.  
  
 *cmdIDMax*  
 Indeks końcowy zakres Identyfikatora polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa grupę programów obsługi wiadomości, zamapowane na określone identyfikatory polecenia przez *cmdIDMin* i *cmdIDMax*, od źródła obiektu polecenia.  
  
##  <a name="removecommandrangeuihandler"></a>  ICommandSource::RemoveCommandRangeUIHandler  
 Usuwa grupę programów obsługi wiadomości polecenia interfejsu użytkownika z obiektem źródłowym polecenia.  
  
```  
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,  
    unsigned int cmdIDMax);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdIDMin*  
 Indeks początkowy zakres Identyfikatora polecenia.  
  
 *cmdIDMax*  
 Indeks końcowy zakres Identyfikatora polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa grupę użytkownika interfejsu polecenie Programy obsługi wiadomości, zamapowane na określone identyfikatory polecenia przez *cmdIDMin* i *cmdIDMax*, od źródła obiektu polecenia.  
  
##  <a name="removecommanduihandler"></a>  ICommandSource::RemoveCommandUIHandler  
 Usuwa program obsługi komunikatów polecenia interfejsu użytkownika z obiektem źródłowym polecenia.  
  
```  
void RemoveCommandUIHandler(unsigned int cmdID);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdID*  
 Identyfikator polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa mapowane do obsługi wiadomości użytkownika interfejsu polecenia *cmdID* z polecenia obiektu źródłowego.  
  
##  <a name="sendcommand"></a>  ICommandSource::SendCommand  
 Wysyła komunikat i czeka na jego przetworzenie przed zwróceniem.  
  
```  
void SendCommand(unsigned int command);
```  
  
### <a name="parameters"></a>Parametry  
 *Polecenie*  
 Identyfikator polecenia komunikatu do wysłania.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda synchronicznie wysyła wiadomość zamapowane na identyfikator określony przez *polecenia*. Wywołuje [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) można umieścić wiadomości w okna kolejki komunikatów i czeka, aż do tej procedury okna przed zwróceniem przetworzył wiadomość.  
  
##  <a name="icommandtarget_interface"></a>  Interfejs obiektu ICommandTarget  
 Udostępnia kontrolkę użytkownika przy użyciu interfejsu do odbierania poleceń z obiektem źródłowym polecenia.  
  
```  
interface class ICommandTarget  
```  
  
### <a name="remarks"></a>Uwagi  
 Kiedy host kontrolkę użytkownika w widoku MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) polecenia tras i aktualizacji polecenia interfejsu użytkownika wiadomości do kontrolki użytkownika, aby umożliwić jego poleceń MFC (na przykład elementów menu ramki i przycisków paska narzędzi). Zaimplementowanie `ICommandTarget`, nadaj odwołania do obiektu kontrolki użytkownika.  
  
 Zobacz [porady: dodawanie do formantu formularzy systemu Windows Routing poleceń](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `ICommandTarget`.  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="initialize"></a>  ICommandTarget::Initialize  
 Inicjuje obiekt docelowy polecenia.  
  
```  
void Initialize(ICommandSource^ cmdSource);
```  
  
### <a name="parameters"></a>Parametry  
 *cmdSource*  
 Dojście do obiektu źródłowego polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Kiedy host kontrolkę użytkownika w widoku MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) polecenia tras i aktualizacji polecenia interfejsu użytkownika wiadomości do kontrolki użytkownika pozwala na jego poleceń MFC.  
  
 Ta metoda inicjuje obiekt docelowy polecenia i kojarzy ją z obiektem źródłowym określone polecenie *cmdSource*. Powinna być wywoływana w implementacji klasy formantu użytkownika. Podczas inicjowania, należy zarejestrować programy obsługi poleceń z obiektem źródłowym polecenia, wywołując [ICommandSource::AddCommandHandler](../../mfc/reference/icommandsource-interface.md) w `Initialize` implementacji. Zobacz [porady: Dodawanie polecenia routingu do formantu formularzy systemu Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `Initialize` w tym celu.  
  
##  <a name="icommandui_interface"></a>  Interfejs ICommandUI  
 Zarządza polecenia interfejsu użytkownika.  
  
```  
interface class ICommandUI  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten interfejs udostępnia metody i właściwości, które zarządzają polecenia interfejsu użytkownika. `ICommandUI` przypomina [ccmdui — klasa](../../mfc/reference/ccmdui-class.md), ale `ICommandUI` jest używana dla aplikacji MFC, które współdziałają z składniki platformy .NET.  
  
 `ICommandUI` jest używany w ramach `ON_UPDATE_COMMAND_UI` obsługi - klasy pochodnej. Gdy użytkownik aplikacji aktywuje (wybiera lub kliknięć) menu, każdy element menu jest wyświetlany jako włączona lub wyłączona. Elementem docelowym każdego polecenia menu udostępnia te informacje zaimplementowanie `ON_UPDATE_COMMAND_UI` obsługi. Dla każdego z obiektów interfejsu użytkownika poleceń w aplikacji umożliwiają utworzenie wpisu mapy wiadomości i prototypu funkcji obsługi każdego okna właściwości.  
  
 Aby uzyskać więcej informacji na temat sposobu `ICommandUI` interfejs jest używany w routing poleceń, zobacz [porady: Dodawanie polecenia routingu do formantu formularzy systemu Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 Aby uzyskać więcej informacji dotyczących sposobu zarządzania polecenia interfejsu użytkownika w MFC, zobacz [ccmdui — klasa](../../mfc/reference/ccmdui-class.md).  
  
##  <a name="check"></a>  ICommandUI::Check  
 Ustawia element interfejsu użytkownika dla tego polecenia w stanie odpowiedniego wyboru.  
  
```  
property UICheckState Check;  
```  
  
### <a name="remarks"></a>Uwagi  
 Dana właściwość ustawia element interfejsu użytkownika dla tego polecenia do stanu odpowiedniego wyboru. Ustaw `Check` na następujące wartości:  
  
|Termin|Definicja|  
|----------|----------------|  
|0|Usuń zaznaczenie pola wyboru|  
|1|Sprawdź|  
|2|Ustaw nieokreślony|  
  
##  <a name="continuerouting"></a>  ICommandUI::ContinueRouting  
 Określa, że mechanizm routingu polecenia kontynuować routingu do bieżącej wiadomości w łańcuchu programów obsługi.  
  
```  
void ContinueRouting();
```  
  
### <a name="remarks"></a>Uwagi  
 To jest funkcja Zaawansowane elementu członkowskiego, które mają być używane w połączeniu z [on_command_ex —](message-map-macros-mfc.md#on_command_ex) obsługi, która zwraca wartość FALSE. Aby uzyskać więcej informacji, zobacz Uwaga techniczna [TN006: mapy komunikatów](../../mfc/tn006-message-maps.md).  
  
##  <a name="enabled"></a>  ICommandUI::Enabled  
 Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia.  
  
```  
property bool Enabled;  
```  
  
### <a name="remarks"></a>Uwagi  
 Tej właściwości Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia. Ustaw `Enabled` wartość true, aby włączyć element, FALSE, aby ją wyłączyć.  
  
##  <a name="id"></a>  ICommandUI::ID  
 Pobiera identyfikator obiektu interfejsu użytkownika reprezentowanego przez `ICommandUI` obiektu.  
  
```  
property unsigned int ID;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta właściwość pobiera identyfikator (dojścia) element menu przycisku paska narzędzi lub innych obiektów interfejsu użytkownika reprezentowanego przez `ICommandUI` obiektu.  
  
##  <a name="index"></a>  ICommandUI::Index  
 Pobiera indeks obiektu interfejsu użytkownika reprezentowanego przez `ICommandUI` obiektu.  
  
```  
property unsigned int Index;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta właściwość pobiera indeks element menu przycisku paska narzędzi (dojścia) lub innego obiektu interfejsu użytkownika reprezentowanego przez `ICommandUI` obiektu.  
  
##  <a name="radio"></a>  ICommandUI::Radio  
 Ustawia element interfejsu użytkownika dla tego polecenia w stanie odpowiedniego wyboru.  
  
```  
property bool Radio;  
```  
  
### <a name="remarks"></a>Uwagi  
 Dana właściwość ustawia element interfejsu użytkownika dla tego polecenia do stanu odpowiedniego wyboru. Ustaw `Radio` wartość true, aby włączyć elementu; w przeciwnym razie wartość FALSE.  
  
##  <a name="text"></a>  ICommandUI::Text  
 Ustawia tekst elementu interfejsu użytkownika dla tego polecenia.  
  
```  
property String^ Text;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta właściwość określa tekst elementu interfejsu użytkownika dla tego polecenia. Ustaw `Text` do uchwytu ciągu tekstowego.  
  
##  <a name="iview_interface"></a>  Interfejs IView  
 Implementuje kilka metod który [CWinFormsView](../../mfc/reference/cwinformsview-class.md) używa do wysyłania powiadomień widoku do zarządzanego formantu.  
  
```  
interface class IView  
```  
  
### <a name="remarks"></a>Uwagi  
 `IView` implementuje kilka metod który `CWinFormsView` używa do przekazywania wspólnej powiadomienia widoku do hostowanej zarządzanego formantu. Są to [OnInitialUpdate](../../mfc/reference/iview-interface.md), [OnUpdate](../../mfc/reference/iview-interface.md) i [OnActivateView](../../mfc/reference/iview-interface.md).  
  
 `IView` przypomina [CView](../../mfc/reference/cview-class.md), ale jest używana tylko z zarządzanych widoków i kontrolek.  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="onactivateview"></a>  IView::OnActivateView  
 Wywoływane przez MFC, gdy widok jest aktywowane lub dezaktywowane.  
  
```  
void OnActivateView(bool activate);
```  
  
### <a name="parameters"></a>Parametry  
 *Aktywuj*  
 Wskazuje, czy widok jest aktywowane lub dezaktywowane.  
  
##  <a name="oninitialupdate"></a>  IView::OnInitialUpdate  
 Wywoływane przez platformę po widoku najpierw jest dołączony do dokumentu, ale przed wyświetleniu widoku.  
  
```  
void OnInitialUpdate();
```  
  
##  <a name="onupdate"></a>  IView::OnUpdate  
 Metoda wywoływana przez MFC, po jego dokument został zmodyfikowany.  
  
```  
void OnUpdate();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja umożliwia widoku, aby zaktualizować jej wyświetlania w celu odzwierciedlenia zmian.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC ZBIERANIE](../../visual-cpp-samples.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)




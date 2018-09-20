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
ms.openlocfilehash: cddcf337c68908d58749623e0739f3cb5979fa91
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387955"
---
# <a name="cwordarray-class"></a>Klasa CWordArray

Obsługuje macierze 16-bitowych słów.

## <a name="syntax"></a>Składnia

```
class CWordArray : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje elementów członkowskich `CWordArray` są podobne do funkcji elementów członkowskich klasy [CObArray](../../mfc/reference/cobarray-class.md). Ze względu na to podobieństwa można użyć `CObArray` dokumentacji kątem specyfiki funkcja elementu członkowskiego. Po wyświetleniu [CObject](../../mfc/reference/cobject-class.md) wskaźnik jako parametr funkcji lub wartości zwracanej, Zastąp słowo.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

na przykład przekłada się na

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Tworzy pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Dodaje element do końca tablicy; zwiększa rozmiar tablicy, jeśli to konieczne.|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Dołącza innej tablicy do tablicy; zwiększa rozmiar tablicy, jeśli to konieczne.|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Kopiuje innej tablicy do tablicy; zwiększa rozmiar tablicy, jeśli to konieczne.|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Zwalnia wszystkie nieużywanej pamięci powyżej bieżącego górną granicę.|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Zwraca wartość pod danym indeksem.|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartości NULL.|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Zwraca największy nieprawidłowy indeks.|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) z określonym indeksem.|
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Określa, czy tablica jest pusta.|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Usuwa element pod określonym indeksem.|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Ustawia wartość dla podanego indeksu; Tablica nie może wzrosnąć.|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Ustawia wartość dla podanego indeksu; zwiększa rozmiar tablicy, jeśli to konieczne.|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray::operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|

## <a name="remarks"></a>Uwagi

`CWordArray` dołącza [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makra do obsługi serializacji i zrzucanie z jego elementów. Jeśli tablica słów są przechowywane do archiwum, za pomocą operatora przeciążona wstawiania lub za pomocą [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) funkcji członkowskiej, każdy element jest, pozycji serializacji.

> [!NOTE]
>  Przed rozpoczęciem korzystania z tablicy, należy użyć `SetSize` jej rozmiaru i przydzielanie pamięci dla niego. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje, że często ponownie przydzielane i skopiować. Częste ponowne przydzielenie kopiowania są nieefektywne i może fragmentu pamięci.

Zrzut poszczególnych elementów w tablicy, należy należy ustawić głębokość kontekstu zrzutu do 1 lub większą.

Aby uzyskać więcej informacji na temat korzystania z `CWordArray`, zapoznaj się z artykułem [kolekcje](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

##  <a name="icommandsource_interface"></a>  Klasa Icommandsource

Zarządza polecenia wysyłane z obiektu źródła polecenia do kontrolki użytkownika.

```
interface class ICommandSource
```

### <a name="remarks"></a>Uwagi

Hostowanie kontrolki użytkownika w widoku MFC [klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md) polecenia tras i aktualizacja poleceń interfejsu użytkownika wiadomości do formantu użytkownika, aby zezwalała na obsługę jego poleceń MFC (na przykład ramek elementów menu i przycisków paska narzędzi). Wdrażając, nadaj kontrolki użytkownika odwołanie do `ICommandSource` obiektu.

Zobacz [porady: Dodawanie routingu poleceń do formantu programu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `ICommandTarget`.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

Dodaje procedurę obsługi poleceń do obiektu źródła polecenia.

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.

*cmdHandler*<br/>
Dojście do metody obsługi polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje procedurę obsługi poleceń *cmdHandler* do obiektu źródła polecenia i mapuje program obsługi *cmdID*.

Zobacz [porady: Dodawanie routingu poleceń do formantu programu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `AddCommandHandler`.

##  <a name="addcommandrangehandler"></a>  ICommandSource::AddCommandRangeHandler

Dodaje grupę programy obsługi poleceń do obiektu źródła polecenia.

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Indeks początkowy zakresu Identyfikatora polecenia.

*cmdIDMax*<br/>
Końcowy indeks zakres Identyfikatora polecenia.

*cmdHandler*<br/>
Dojście do metody obsługi wiadomości, do której polecenia są zamapowane.

### <a name="remarks"></a>Uwagi

Ta metoda mapuje ciągły zakres identyfikatorów poleceń do obsługi komunikatów w jednym i dodaje go do obiektu źródła polecenia. Służy to do obsługi grupy przycisków powiązane z jedną z metod.

##  <a name="addcommandrangeuihandler"></a>  ICommandSource::AddCommandRangeUIHandler

Dodaje grupę obsługi komunikatów poleceń interfejsu użytkownika do obiektu źródła polecenia.

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Indeks początkowy zakresu Identyfikatora polecenia.

*cmdIDMax*<br/>
Końcowy indeks zakres Identyfikatora polecenia.

*cmdHandler*<br/>
Dojście do metody obsługi wiadomości, do której polecenia są zamapowane.

### <a name="remarks"></a>Uwagi

Ta metoda mapuje ciągły zakres identyfikatorów poleceń do obsługi komunikatów poleceń interfejsu pojedynczego użytkownika i dodaje go do obiektu źródła polecenia. Służy to do obsługi grupy przycisków powiązane z jedną z metod.

##  <a name="addcommanduihandler"></a>  ICommandSource::AddCommandUIHandler

Dodaje program obsługi komunikatów poleceń interfejsu użytkownika do obiektu źródła polecenia.

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.

*cmdUIHandler*<br/>
Dojście do metody obsługi wiadomości polecenia interfejsu użytkownika.

### <a name="remarks"></a>Uwagi

Metoda ta umożliwia dodanie obsługi komunikatów poleceń interfejsu użytkownika *cmdHandler* do obiektu źródła polecenia i mapuje program obsługi *cmdID*.

##  <a name="postcommand"></a>  ICommandSource::PostCommand

Publikuje komunikat bez oczekiwania na przetworzenie.

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*Polecenie*<br/>
Identyfikator polecenia wiadomość do opublikowania.

### <a name="remarks"></a>Uwagi

Ta metoda asynchronicznie wysyła komunikat mapowane na określony przez identyfikator *polecenia*. Wywołuje [CWnd::PostMessage](../../mfc/reference/cwnd-class.md#postmessage) do umieszczenia wiadomości w kolejki komunikatów i zwraca okna bez oczekiwania na odpowiednie okno przetworzyć komunikatu.

##  <a name="removecommandhandler"></a>  ICommandSource::RemoveCommandHandler

Usuwa procedurę obsługi poleceń z obiektu źródła polecenia.

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa zamapowany program obsługi poleceń *cmdID* z obiektu źródła polecenia.

##  <a name="removecommandrangehandler"></a>  ICommandSource::RemoveCommandRangeHandler

Usuwa grupę programy obsługi poleceń z obiektu źródła polecenia.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Indeks początkowy zakresu Identyfikatora polecenia.

*cmdIDMax*<br/>
Końcowy indeks zakres Identyfikatora polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa grupę programy obsługi komunikatów, mapowane na określonych identyfikatorów poleceń przez *cmdIDMin* i *cmdIDMax*, z obiektu źródła polecenia.

##  <a name="removecommandrangeuihandler"></a>  ICommandSource::RemoveCommandRangeUIHandler

Usuwa grupę obsługi komunikatów poleceń interfejsu użytkownika z obiektu źródła polecenia.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Indeks początkowy zakresu Identyfikatora polecenia.

*cmdIDMax*<br/>
Końcowy indeks zakres Identyfikatora polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa grupę użytkownika interfejsu polecenia programy obsługi komunikatów, mapowane na określonych identyfikatorów poleceń przez *cmdIDMin* i *cmdIDMax*, z obiektu źródła polecenia.

##  <a name="removecommanduihandler"></a>  ICommandSource::RemoveCommandUIHandler

Usuwa obsługi komunikatów poleceń interfejsu użytkownika z obiektu źródła polecenia.

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa obsługi komunikatów poleceń interfejsu użytkownika mapowane na *cmdID* z obiektu źródła polecenia.

##  <a name="sendcommand"></a>  ICommandSource::SendCommand

Wysyła komunikat i czeka na jego przetworzenie przed zwróceniem.

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*Polecenie*<br/>
Identyfikator polecenia komunikatu do wysłania.

### <a name="remarks"></a>Uwagi

Ta metoda synchronicznie wysyła komunikat mapowane na określony przez identyfikator *polecenia*. Wywołuje [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) można umieścić komunikatu w okna kolejki komunikatów i czeka, aż tej procedury okna przetworzeniu komunikatu przed zwróceniem.

##  <a name="icommandtarget_interface"></a>  Klasa Icommandtarget

Udostępnia kontrolkę użytkownika z interfejsem w celu odbierania poleceń od obiektu źródła polecenia.

```
interface class ICommandTarget
```

### <a name="remarks"></a>Uwagi

Hostowanie kontrolki użytkownika w widoku MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) polecenia tras i aktualizacja poleceń interfejsu użytkownika wiadomości do formantu użytkownika, aby zezwalała na obsługę jego poleceń MFC (na przykład ramek elementów menu i przycisków paska narzędzi). Implementując `ICommandTarget`, podać odwołanie do obiektu kontrolki użytkownika.

Zobacz [porady: Dodawanie routingu poleceń do formantu programu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `ICommandTarget`.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="initialize"></a>  ICommandTarget::Initialize

Inicjuje obiekt docelowy polecenia.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parametry

*cmdSource*<br/>
Dojście do obiektu źródła polecenia.

### <a name="remarks"></a>Uwagi

Hostowanie kontrolki użytkownika w widoku MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) polecenia tras i aktualizacja poleceń interfejsu użytkownika wiadomości do formantu użytkownika, aby zezwalała na obsługę jego poleceń MFC.

Ta metoda inicjuje obiekt docelowy polecenia i kojarzy ją z obiektu źródłowego określonego polecenia *cmdSource*. Powinien zostać wywołany w implementacji klasy formantu użytkownika. Podczas inicjowania, należy zarejestrować programy obsługi poleceń za pomocą obiektu źródła polecenia przez wywołanie metody [ICommandSource::AddCommandHandler](../../mfc/reference/icommandsource-interface.md) w `Initialize` implementacji. Zobacz [porady: Dodawanie routingu poleceń do formantu programu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `Initialize` w tym celu.

##  <a name="icommandui_interface"></a>  Klasa Icommandui

Zarządza poleceń interfejsu użytkownika.

```
interface class ICommandUI
```

### <a name="remarks"></a>Uwagi

Ten interfejs zapewnia metody i właściwości, które zarządzają poleceń interfejsu użytkownika. `ICommandUI` jest podobny do [klasa CCmdUI](../../mfc/reference/ccmdui-class.md), chyba że `ICommandUI` jest używana dla aplikacji MFC, które współpracować ze składnikami platformy .NET.

`ICommandUI` jest używany w ramach `ON_UPDATE_COMMAND_UI` obsługi klasy pochodnej. Gdy użytkownik aplikacji aktywuje (zaznacza lub kliknięcia) menu, każdy element menu jest wyświetlany jako włączone lub wyłączone. Celem każdego polecenia menu zawiera informacje, implementując `ON_UPDATE_COMMAND_UI` programu obsługi. Dla każdego z obiektów interfejsu użytkownika poleceń w aplikacji okno właściwości do utworzenia wpisu mapy wiadomości i prototypu funkcji dla każdej procedury obsługi.

Aby uzyskać więcej informacji na temat sposobu `ICommandUI` interfejs jest używany w routingu poleceń, zobacz [porady: Dodawanie routingu poleceń do formantu programu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Aby uzyskać więcej informacji na temat sposobu zarządzania poleceń interfejsu użytkownika w MFC, zobacz [klasa CCmdUI](../../mfc/reference/ccmdui-class.md).

##  <a name="check"></a>  ICommandUI::Check

Ustawia stan zaznaczenia odpowiednich element interfejsu użytkownika dla tego polecenia.

```
property UICheckState Check;
```

### <a name="remarks"></a>Uwagi

Ta właściwość ustawia element interfejsu użytkownika dla tego polecenia stanie odpowiedniej kontroli. Ustaw `Check` następujące wartości:

|Termin|Definicja|
|----------|----------------|
|0|Usuń zaznaczenie pola wyboru|
|1|Sprawdź|
|2|Ustaw nieokreślony|

##  <a name="continuerouting"></a>  ICommandUI::ContinueRouting

Informuje mechanizm routingu polecenia nadal routingu do bieżącej wiadomości w łańcuchu programów obsługi.

```
void ContinueRouting();
```

### <a name="remarks"></a>Uwagi

To jest funkcja członków na poziomie zaawansowanym, który ma zostać użyty w połączeniu z [ON_COMMAND_EX](message-map-macros-mfc.md#on_command_ex) program obsługi, który zwraca wartość FALSE. Aby uzyskać więcej informacji, zobacz Uwaga techniczna [TN006: mapy komunikatów](../../mfc/tn006-message-maps.md).

##  <a name="enabled"></a>  ICommandUI::Enabled

Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia.

```
property bool Enabled;
```

### <a name="remarks"></a>Uwagi

Tej właściwości Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia. Ustaw `Enabled` na wartość TRUE, FALSE umożliwiające elementu, aby je wyłączyć.

##  <a name="id"></a>  ICommandUI::ID

Pobiera identyfikator obiektu interfejsu użytkownika, które są reprezentowane przez `ICommandUI` obiektu.

```
property unsigned int ID;
```

### <a name="remarks"></a>Uwagi

Tej właściwości pobiera identyfikator (uchwyt) elementu menu, przycisk paska narzędzi lub innych obiektów interfejsu użytkownika są reprezentowane przez `ICommandUI` obiektu.

##  <a name="index"></a>  ICommandUI::Index

Pobiera indeks obiektu interfejsu użytkownika, które są reprezentowane przez `ICommandUI` obiektu.

```
property unsigned int Index;
```

### <a name="remarks"></a>Uwagi

Tej właściwości pobiera indeks elementu menu, przycisk paska narzędzi (uchwyt) lub inny obiekt interfejsu użytkownika są reprezentowane przez `ICommandUI` obiektu.

##  <a name="radio"></a>  ICommandUI::Radio

Ustawia stan zaznaczenia odpowiednich element interfejsu użytkownika dla tego polecenia.

```
property bool Radio;
```

### <a name="remarks"></a>Uwagi

Ta właściwość ustawia element interfejsu użytkownika dla tego polecenia stanie odpowiedniej kontroli. Ustaw `Radio` na wartość TRUE, aby włączyć element; w przeciwnym razie wartość FALSE.

##  <a name="text"></a>  ICommandUI::Text

Ustawia tekst elementu interfejsu użytkownika dla tego polecenia.

```
property String^ Text;
```

### <a name="remarks"></a>Uwagi

Ta właściwość określa tekst elementu interfejsu użytkownika dla tego polecenia. Ustaw `Text` do uchwytu ciągu tekstowego.

##  <a name="iview_interface"></a>  Interfejs IView

Implementuje kilka metod, które [CWinFormsView](../../mfc/reference/cwinformsview-class.md) używa do wysyłania powiadomień w widoku do zarządzanego formantu.

```
interface class IView
```

### <a name="remarks"></a>Uwagi

`IView` implementuje kilka metod, które `CWinFormsView` używa do przekazywania wspólnych powiadomień widoku do hostowanej zarządzanego formantu. Są to [OnInitialUpdate](../../mfc/reference/iview-interface.md), [OnUpdate](../../mfc/reference/iview-interface.md) i [OnActivateView](../../mfc/reference/iview-interface.md).

`IView` jest podobny do [CView](../../mfc/reference/cview-class.md), ale jest używany tylko z zarządzanych widoków i kontrolek.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="onactivateview"></a>  IView::OnActivateView

Metoda wywoływana przez MFC, gdy widok jest aktywowane lub dezaktywowane.

```
void OnActivateView(bool activate);
```

### <a name="parameters"></a>Parametry

*Aktywuj*<br/>
Wskazuje, czy widok jest aktywowane lub dezaktywowane.

##  <a name="oninitialupdate"></a>  IView::OnInitialUpdate

Wywoływane przez platformę po widoku najpierw jest dołączony do dokumentu, ale przed wyświetleniu widoku.

```
void OnInitialUpdate();
```

##  <a name="onupdate"></a>  IView::OnUpdate

Metoda wywoływana przez MFC po zmodyfikowaniu tego widoku dokumentu.

```
void OnUpdate();
```

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia widok, aby zaktualizować jego ekranu, aby odzwierciedlić zmiany.

## <a name="see-also"></a>Zobacz też

[Próbki MFC ZBIERANIE](../../visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)




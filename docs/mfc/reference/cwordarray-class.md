---
title: Klasa CWordArray
ms.date: 09/07/2019
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
ms.openlocfilehash: c136bbb14e0d7cffc604813731b6f87ba18063cf
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907914"
---
# <a name="cwordarray-class"></a>Klasa CWordArray

Obsługuje tablice słów 16-bitowych.

## <a name="syntax"></a>Składnia

```
class CWordArray : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje `CWordArray` składowe są podobne do funkcji składowych klasy [CObArray](../../mfc/reference/cobarray-class.md). W związku z tym podobieństwem można użyć `CObArray` dokumentacji referencyjnej dla specyficznych dla funkcji składowych. Wszędzie tam, gdzie widzisz wskaźnik [CObject](../../mfc/reference/cobject-class.md) jako parametr funkcji lub wartość zwracaną, Zastąp słowo.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

na przykład tłumaczy na

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Konstruuje pustą tablicę.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray:: Add](../../mfc/reference/cobarray-class.md#add)|Dodaje element na końcu tablicy; w razie potrzeby powiększa tablicę.|
|[CObArray:: Append](../../mfc/reference/cobarray-class.md#append)|Dołącza kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CObArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Kopiuje kolejną tablicę do tablicy; w razie potrzeby powiększa tablicę.|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Zwraca tymczasowe odwołanie do wskaźnika elementu w tablicy.|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Zwalnia wszystkie nieużywane pamięci powyżej bieżącej górnej granicy.|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Zwraca wartość w danym indeksie.|
|[CObArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Pobiera liczbę elementów w tej tablicy.|
|[CObArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Umożliwia dostęp do elementów w tablicy. Może mieć wartość NULL.|
|[CObArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|Pobiera liczbę elementów w tej tablicy.|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Zwraca największy prawidłowy indeks.|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Wstawia element (lub wszystkie elementy w innej tablicy) o określonym indeksie.|
|[CObArray:: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Określa, czy tablica jest pusta.|
|[CObArray::](../../mfc/reference/cobarray-class.md#removeall)|Usuwa wszystkie elementy z tej tablicy.|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Usuwa element z określonym indeksem.|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Ustawia wartość dla danego indeksu; Tablica nie może być większa.|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Ustawia wartość dla danego indeksu; w razie potrzeby powiększa tablicę.|
|[CObArray:: setSize](../../mfc/reference/cobarray-class.md#setsize)|Ustawia liczbę elementów, które mają być zawarte w tej tablicy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObArray:: operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|

## <a name="remarks"></a>Uwagi

`CWordArray`obejmuje makro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) , które obsługuje serializację i zatopienie elementów. Jeśli tablica wyrazów jest przechowywana w archiwum, ze przeciążonym operatorem wstawiania lub z [CObject:: serializować](../../mfc/reference/cobject-class.md#serialize) elementu członkowskiego, każdy element jest z kolei serializowany.

> [!NOTE]
>  Przed użyciem tablicy należy użyć `SetSize` , aby określić jej rozmiar i przydzielić pamięć. Jeśli nie używasz `SetSize`, dodawanie elementów do tablicy powoduje, że jest on często ponownie alokowany i kopiowany. Częste ponowne przydzielanie i kopiowanie są niewydajne i mogą fragmentację pamięci.

Jeśli potrzebujesz zrzutu poszczególnych elementów w tablicy, musisz ustawić głębokość kontekstu zrzutu na 1 lub większą.

Aby uzyskać więcej informacji na `CWordArray`temat korzystania z programu, zobacz [kolekcje](../../mfc/collections.md)artykułów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll. h

##  <a name="icommandsource_interface"></a>ICommandSource, interfejs

Zarządza poleceniami wysyłanymi z obiektu źródłowego polecenia do kontrolki użytkownika.

```
interface class ICommandSource
```

### <a name="remarks"></a>Uwagi

W przypadku hostowania kontrolki użytkownika w widoku MFC [Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md) kieruje polecenia i aktualizuje komunikaty interfejsu użytkownika do kontrolki użytkownika, aby umożliwić obsługę poleceń MFC (na przykład elementów menu ramek i przycisków paska narzędzi). Implementując, nadajesz użytkownikowi kontrolę odwołania do `ICommandSource` obiektu.

Zobacz [How to: Aby zapoznać się z przykładem użycia](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) `ICommandTarget`programu, należy dodać polecenie Routing do kontrolki Windows Forms.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="addcommandhandler"></a>ICommandSource:: AddCommandHandler

Dodaje procedurę obsługi polecenia do obiektu źródłowego polecenia.

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.

*cmdHandler*<br/>
Dojście do metody obsługi poleceń.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje procedurę obsługi poleceń *cmdHandler* do obiektu źródłowego polecenia i mapuje procedurę obsługi na *cmdID*.

Zobacz [How to: Aby zapoznać się z przykładem użycia](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) `AddCommandHandler`programu, należy dodać polecenie Routing do kontrolki Windows Forms.

##  <a name="addcommandrangehandler"></a>ICommandSource:: AddCommandRangeHandler

Dodaje grupę obsługi poleceń do obiektu źródłowego polecenia.

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Początkowy indeks zakresu identyfikatora polecenia.

*cmdIDMax*<br/>
Końcowy indeks zakresu identyfikatora polecenia.

*cmdHandler*<br/>
Dojście do metody obsługi komunikatów, do której są mapowane polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda mapuje ciągły zakres identyfikatorów poleceń do obsługi jednego komunikatu i dodaje go do obiektu źródłowego polecenia. Służy do obsługi grupy powiązanych przycisków przy użyciu jednej metody.

##  <a name="addcommandrangeuihandler"></a>ICommandSource:: AddCommandRangeUIHandler

Dodaje grupę obsługi komunikatów poleceń interfejsu użytkownika do obiektu źródłowego polecenia.

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Początkowy indeks zakresu identyfikatora polecenia.

*cmdIDMax*<br/>
Końcowy indeks zakresu identyfikatora polecenia.

*cmdHandler*<br/>
Dojście do metody obsługi komunikatów, do której są mapowane polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda mapuje ciągły zakres identyfikatorów poleceń do procedury obsługi komunikatów jednego interfejsu użytkownika i dodaje ją do obiektu źródłowego polecenia. Służy do obsługi grupy powiązanych przycisków przy użyciu jednej metody.

##  <a name="addcommanduihandler"></a>ICommandSource:: AddCommandUIHandler

Dodaje procedurę obsługi komunikatów interfejsu użytkownika do obiektu źródłowego polecenia.

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.

*cmdUIHandler*<br/>
Dojście do metody obsługi komunikatów polecenia interfejsu użytkownika.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje procedurę obsługi komunikatów interfejsu użytkownika *cmdHandler* do obiektu źródłowego polecenia i mapuje procedurę obsługi na *cmdID*.

##  <a name="postcommand"></a>ICommandSource::P ostCommand

Publikuje komunikat bez oczekiwania na jego przetworzenie.

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*dotyczące*<br/>
Identyfikator polecenia wiadomości do opublikowania.

### <a name="remarks"></a>Uwagi

Ta metoda asynchronicznie zapisuje komunikat mapowany do identyfikatora określonego przez *polecenie*. Wywołuje [CWnd::P ostmessage](../../mfc/reference/cwnd-class.md#postmessage) , aby umieścić komunikat w kolejce komunikatów okna, a następnie zwraca bez oczekiwania na odpowiednie okno do przetworzenia komunikatu.

##  <a name="removecommandhandler"></a>ICommandSource:: RemoveCommandHandler

Usuwa procedurę obsługi poleceń z obiektu źródłowego polecenia.

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa procedurę obsługi poleceń zamapowana do *cmdID* z obiektu źródłowego polecenia.

##  <a name="removecommandrangehandler"></a>ICommandSource:: RemoveCommandRangeHandler

Usuwa grupę programów obsługi poleceń z obiektu źródłowego polecenia.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Początkowy indeks zakresu identyfikatora polecenia.

*cmdIDMax*<br/>
Końcowy indeks zakresu identyfikatora polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa grupę programów obsługi komunikatów, mapowanych na identyfikatory poleceń określonych przez *cmdIDMin* i *cmdIDMax*, z obiektu źródłowego polecenia.

##  <a name="removecommandrangeuihandler"></a>ICommandSource:: RemoveCommandRangeUIHandler

Usuwa grupę procedur obsługi komunikatów poleceń interfejsu użytkownika z obiektu źródłowego polecenia.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Początkowy indeks zakresu identyfikatora polecenia.

*cmdIDMax*<br/>
Końcowy indeks zakresu identyfikatora polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa grupę obsługi komunikatów poleceń interfejsu użytkownika, zamapowane na identyfikatory poleceń określone przez *cmdIDMin* i *cmdIDMax*, z obiektu źródłowego polecenia.

##  <a name="removecommanduihandler"></a>ICommandSource:: RemoveCommandUIHandler

Usuwa procedurę obsługi komunikatów interfejsu użytkownika z obiektu źródłowego polecenia.

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa procedurę obsługi komunikatów interfejsu użytkownika zamapowana do *cmdID* z obiektu źródłowego polecenia.

##  <a name="sendcommand"></a>ICommandSource:: SendCommand

Wysyła komunikat i czeka na jego przetwarzanie przed zwróceniem.

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*dotyczące*<br/>
Identyfikator polecenia wiadomości do wysłania.

### <a name="remarks"></a>Uwagi

Ta metoda synchronicznie wysyła komunikat mapowany do identyfikatora określonego przez *polecenie*. Wywołuje [CWnd:: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) , aby umieścić komunikat w kolejce komunikatów okna i czekać, aż ta procedura okna przetworzy komunikat przed zwróceniem.

##  <a name="icommandtarget_interface"></a>ICommandTarget, interfejs

Udostępnia kontrolkę użytkownika z interfejsem do odbierania poleceń z obiektu źródłowego polecenia.

```
interface class ICommandTarget
```

### <a name="remarks"></a>Uwagi

W przypadku hostowania kontrolki użytkownika w widoku MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) kieruje polecenia i zaktualizuje komunikaty interfejsu użytkownika do kontrolki użytkownika, aby umożliwić obsługę poleceń MFC (na przykład elementów menu ramek i przycisków paska narzędzi). Implementując `ICommandTarget`, nadajesz użytkownikowi kontrolę odwołania do obiektu.

Zobacz [How to: Aby zapoznać się z przykładem użycia](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) `ICommandTarget`programu, należy dodać polecenie Routing do kontrolki Windows Forms.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="initialize"></a>ICommandTarget:: Initialize

Inicjuje obiekt docelowy polecenia.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Parametry

*cmdSource*<br/>
Uchwyt do obiektu źródłowego polecenia.

### <a name="remarks"></a>Uwagi

W przypadku hostowania kontrolki użytkownika w widoku MFC [CWinFormsView](../../mfc/reference/cwinformsview-class.md) kieruje polecenia i zaktualizuje komunikaty interfejsu użytkownika do kontrolki użytkownika, aby umożliwić obsługę poleceń MFC.

Ta metoda inicjuje obiekt docelowy polecenia i kojarzy go z określonym obiektem źródłowym polecenia *cmdSource*. Powinien być wywoływany w implementacji klasy kontrolki użytkownika. Podczas inicjalizacji należy zarejestrować programy obsługi poleceń z obiektem źródłowym polecenia przez wywołanie [ICommandSource:: AddCommandHandler](../../mfc/reference/icommandsource-interface.md) w `Initialize` implementacji. Zobacz [How to: Dodaj polecenie Routing do kontrolki](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) Windows Forms, aby zapoznać się z przykładem sposobu użycia `Initialize` w tym celu.

##  <a name="icommandui_interface"></a>ICommandUI, interfejs

Zarządza poleceniami interfejsu użytkownika.

```
interface class ICommandUI
```

### <a name="remarks"></a>Uwagi

Ten interfejs zapewnia metody i właściwości, które zarządzają poleceniami interfejsu użytkownika. `ICommandUI`jest podobna do [klasy CCmdUI](../../mfc/reference/ccmdui-class.md), z tą `ICommandUI` różnicą, że jest używana dla aplikacji MFC, które współdziałają ze składnikami platformy .NET.

`ICommandUI`jest używany w ramach `ON_UPDATE_COMMAND_UI` procedury obsługi w klasie pochodnej. Gdy użytkownik uaktywnia (wybiera lub klika) menu, każdy element menu jest wyświetlany jako włączony lub wyłączony. Obiekt docelowy każdego polecenia menu dostarcza te informacje poprzez implementację `ON_UPDATE_COMMAND_UI` programu obsługi. Dla każdego z poleceń obiektów interfejsu użytkownika w aplikacji użyj [kreatora klas](mfc-class-wizard.md) lub okna **właściwości** (w **Widok klasy**) do utworzenia wpisu mapy komunikatów i prototypu funkcji dla każdej procedury obsługi.

Aby uzyskać więcej informacji na temat `ICommandUI` sposobu użycia interfejsu w routingu poleceń, zobacz [How to: Dodaj routing poleceń do kontrolki](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)Windows Forms.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Aby uzyskać więcej informacji na temat sposobu zarządzania poleceniami interfejsu użytkownika w MFC, zobacz [CCmdUI Class](../../mfc/reference/ccmdui-class.md).

##  <a name="check"></a>ICommandUI:: Check

Ustawia element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu sprawdzania.

```
property UICheckState Check;
```

### <a name="remarks"></a>Uwagi

Ta właściwość ustawia element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu sprawdzania. Ustaw `Check` następujące wartości:

|Termin|Definicja|
|----------|----------------|
|0|Usuń zaznaczenie|
|1|Sprawdź|
|2|Ustaw nieokreślony|

##  <a name="continuerouting"></a>ICommandUI::ContinueRouting

Informuje mechanizm routingu poleceń, aby kontynuować kierowanie bieżącego komunikatu do łańcucha programów obsługi.

```
void ContinueRouting();
```

### <a name="remarks"></a>Uwagi

Jest to zaawansowana funkcja członkowska, która powinna być używana w połączeniu z obsługą [ON_COMMAND_EX](message-map-macros-mfc.md#on_command_ex) , która zwraca wartość false. Aby uzyskać więcej informacji, zobacz uwagi [techniczne TN006: Mapy](../../mfc/tn006-message-maps.md)komunikatów.

##  <a name="enabled"></a>ICommandUI:: Enabled

Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia.

```
property bool Enabled;
```

### <a name="remarks"></a>Uwagi

Ta właściwość włącza lub wyłącza element interfejsu użytkownika dla tego polecenia. Ustaw `Enabled` wartość true, aby włączyć element, false, aby go wyłączyć.

##  <a name="id"></a>ICommandUI:: ID

Pobiera identyfikator obiektu interfejsu użytkownika reprezentowanego przez `ICommandUI` obiekt.

```
property unsigned int ID;
```

### <a name="remarks"></a>Uwagi

Ta właściwość pobiera identyfikator (uchwyt) elementu menu, przycisku paska narzędzi lub innego obiektu interfejsu użytkownika reprezentowanego przez `ICommandUI` obiekt.

##  <a name="index"></a>ICommandUI:: index

Pobiera indeks obiektu interfejsu użytkownika reprezentowanego przez `ICommandUI` obiekt.

```
property unsigned int Index;
```

### <a name="remarks"></a>Uwagi

Ta właściwość Pobiera indeks (uchwyt) elementu menu, przycisku paska narzędzi lub innego obiektu interfejsu użytkownika reprezentowanego przez `ICommandUI` obiekt.

##  <a name="radio"></a>ICommandUI:: Radio

Ustawia element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu sprawdzania.

```
property bool Radio;
```

### <a name="remarks"></a>Uwagi

Ta właściwość ustawia element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu sprawdzania. Ustaw `Radio` wartość true, aby włączyć element; w przeciwnym razie wartość false.

##  <a name="text"></a>ICommandUI:: text

Ustawia tekst elementu interfejsu użytkownika dla tego polecenia.

```
property String^ Text;
```

### <a name="remarks"></a>Uwagi

Ta właściwość ustawia tekst elementu interfejsu użytkownika dla tego polecenia. Ustaw `Text` na uchwyt ciągu tekstowego.

##  <a name="iview_interface"></a>Interfejs IView

Implementuje kilka metod, których [CWinFormsView](../../mfc/reference/cwinformsview-class.md) używa do wysyłania powiadomień o widoku do zarządzanej kontrolki.

```
interface class IView
```

### <a name="remarks"></a>Uwagi

`IView`implementuje kilka metod, `CWinFormsView` które używają do przesyłania dalej wspólnych powiadomień o widoku do hostowanej kontroli zarządzanej. Są to [OnInitialUpdate](../../mfc/reference/iview-interface.md), [OnUpdate](../../mfc/reference/iview-interface.md) i [OnActivateView](../../mfc/reference/iview-interface.md).

`IView`jest podobny do [CView](../../mfc/reference/cview-class.md), ale jest używany tylko z zarządzanymi widokami i kontrolkami.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="onactivateview"></a>Widok IView:: OnActivateView

Wywoływane przez MFC, gdy widok jest aktywowany lub dezaktywowany.

```
void OnActivateView(bool activate);
```

### <a name="parameters"></a>Parametry

*zdezaktywować*<br/>
Wskazuje, czy widok jest aktywowany, czy dezaktywowany.

##  <a name="oninitialupdate"></a>Widok IView:: OnInitialUpdate

Wywoływane przez platformę po pierwszym dołączeniu widoku do dokumentu, ale zanim widok jest początkowo wyświetlany.

```
void OnInitialUpdate();
```

##  <a name="onupdate"></a>Widok IView:: OnUpdate

Wywoływane przez MFC po zmodyfikowaniu dokumentu widoku.

```
void OnUpdate();
```

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia zaktualizowanie wyświetlania widoku w celu odzwierciedlenia zmian.

## <a name="see-also"></a>Zobacz także

[ZBIERANIE próbek MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)

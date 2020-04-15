---
title: Klasa ICommandSource
ms.date: 03/27/2019
f1_keywords:
- ICommandSource
- AFXWINFORMS/ICommandSource
- AFXWINFORMS/ICommandSource::AddCommandHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::AddCommandUIHandler
- AFXWINFORMS/ICommandSource::PostCommand
- AFXWINFORMS/ICommandSource::RemoveCommandHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::RemoveCommandUIHandler
- AFXWINFORMS/ICommandSource::SendCommand
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
ms.openlocfilehash: 6a03c46c972f7746f39a3c5c65ca9b5509983d59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356981"
---
# <a name="icommandsource-interface"></a>Klasa ICommandSource

Zarządza poleceniami wysyłanymi z obiektu źródła polecenia do formantu użytkownika.

## <a name="syntax"></a>Składnia

```cpp
interface class ICommandSource
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ICommandSource::AddCommandHandler](#addcommandhandler)|Dodaje program obsługi poleceń do obiektu źródłowego polecenia.|
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|Dodaje grupę programów obsługi poleceń do obiektu źródłowego polecenia.|
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|Dodaje grupę programów obsługi komunikatów polecenia interfejsu użytkownika do obiektu źródłowego polecenia.|
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|Dodaje program obsługi komunikatów polecenia interfejsu użytkownika do obiektu źródłowego polecenia.|
|[ICommandSource::PostCommand](#postcommand)|Wysyła wiadomość bez oczekiwania na jej przetworzenie.|
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|Usuwa program obsługi poleceń z obiektu źródłowego polecenia.|
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Usuwa grupę programów obsługi poleceń z obiektu źródłowego polecenia.|
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Usuwa grupę programów obsługi komunikatów polecenia interfejsu użytkownika z obiektu źródłowego polecenia.|
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|Usuwa program obsługi komunikatów polecenia interfejsu użytkownika z obiektu źródłowego polecenia.|
|[ICommandSource::SendCommand](#sendcommand)|Wysyła wiadomość i czeka na jej przetworzenie przed zwróceniem.|

### <a name="remarks"></a>Uwagi

Podczas hostowania formantu użytkownika w widoku MFC, [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md) trasy poleceń i zaktualizować polecenia komunikaty interfejsu użytkownika do formantu użytkownika, aby umożliwić mu obsługę poleceń MFC (na przykład elementy menu ramki i przyciski paska narzędzi). Implementując [interfejs ICommandTarget](../../mfc/reference/icommandtarget-interface.md), nadać kontroli użytkownika `ICommandSource` odwołanie do obiektu.

Zobacz [Jak: Dodawanie routingu poleceń do formantu formularzy systemu Windows,](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) aby uzyskać przykład użycia `ICommandTarget`programu .

Aby uzyskać więcej informacji na temat korzystania z formularzy systemu Windows, zobacz [Korzystanie z formantu użytkownika formularza systemu Windows w programie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="icommandsourceaddcommandhandler"></a><a name="addcommandhandler"></a>ICommandSource::AddCommandHandler

Dodaje program obsługi poleceń do obiektu źródłowego polecenia.

```cpp
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*identyfikator cmdID*<br/>
Identyfikator polecenia.
*cmdHandler (uchwyt cmd)*<br/>
Dojście do metody obsługi poleceń.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje cmdHandler obsługi polecenia do obiektu źródła polecenia i mapuje program obsługi do cmdID.
Zobacz [Jak: Dodawanie routingu poleceń do formantu formularzy systemu Windows,](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) aby uzyskać przykład użycia dodatku AddCommandHandler.

## <a name="icommandsourceaddcommandrangehandler"></a><a name="addcommandrangehandler"></a>ICommandSource::AddCommandRangeHandler

Dodaje grupę programów obsługi poleceń do obiektu źródłowego polecenia.

```cpp
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Indeks początkowy zakresu identyfikatora polecenia.
*cmdIDMax*<br/>
Końcowy indeks zakresu identyfikatora polecenia.
*cmdHandler (uchwyt cmd)*<br/>
Dojście do metody obsługi wiadomości, do której są mapowane polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda mapuje ciągły zakres identyfikatorów poleceń do pojedynczego programu obsługi wiadomości i dodaje go do obiektu źródła polecenia. Służy do obsługi grupy powiązanych przycisków za pomocą jednej metody.

## <a name="icommandsourceaddcommandrangeuihandler"></a><a name="addcommandrangeuihandler"></a>ICommandSource::AddCommandRangeUIHandler

Dodaje grupę programów obsługi komunikatów polecenia interfejsu użytkownika do obiektu źródłowego polecenia.

```cpp
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Indeks początkowy zakresu identyfikatora polecenia.
*cmdIDMax*<br/>
Końcowy indeks zakresu identyfikatora polecenia.
*cmdHandler (uchwyt cmd)*<br/>
Dojście do metody obsługi wiadomości, do której są mapowane polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda mapuje ciągły zakres identyfikatorów poleceń do obsługi komunikatów poleceń pojedynczego interfejsu użytkownika i dodaje go do obiektu źródła polecenia. Służy do obsługi grupy powiązanych przycisków za pomocą jednej metody.

## <a name="icommandsourceaddcommanduihandler"></a><a name="addcommanduihandler"></a>ICommandSource::AddCommandUIHandler

Dodaje program obsługi komunikatów polecenia interfejsu użytkownika do obiektu źródłowego polecenia.

```cpp
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Parametry

*identyfikator cmdID*<br/>
Identyfikator polecenia.
*cmdUIHandler*<br/>
Dojście do metody obsługi komunikatów polecenia interfejsu użytkownika.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje program obsługi polecenia interfejsu użytkownika cmdHandler do obiektu źródła polecenia i mapuje program obsługi do cmdID.

## <a name="icommandsourcepostcommand"></a><a name="postcommand"></a>ICommandSource::PostCommand

Wysyła wiadomość bez oczekiwania na jej przetworzenie.

```cpp
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*Polecenia*<br/>
Identyfikator polecenia wiadomości, która ma zostać opublikowana.

### <a name="remarks"></a>Uwagi

Ta metoda asynchronicznie księguje wiadomość mapowane do identyfikatora określonego przez polecenie. Wywołuje CWnd::PostMessage umieścić wiadomość w kolejce komunikatów okna, a następnie zwraca bez oczekiwania na odpowiednie okno do przetwarzania wiadomości.

## <a name="icommandsourceremovecommandhandler"></a><a name="removecommandhandler"></a>ICommandSource::RemoveCommandHandler

Usuwa program obsługi poleceń z obiektu źródłowego polecenia.

```cpp
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*identyfikator cmdID*<br/>
Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa program obsługi polecenia mapowany na cmdID z obiektu źródłowego polecenia.

## <a name="icommandsourceremovecommandrangehandler"></a><a name="removecommandrangehandler"></a>ICommandSource::RemoveCommandRangeHandler

Usuwa grupę programów obsługi poleceń z obiektu źródłowego polecenia.

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Indeks początkowy zakresu identyfikatora polecenia.
*cmdIDMax*<br/>
Końcowy indeks zakresu identyfikatora polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa grupę programów obsługi wiadomości, mapowane do identyfikatorów poleceń określonych przez cmdIDMin i cmdIDMax, z obiektu źródła polecenia.

## <a name="icommandsourceremovecommandrangeuihandler"></a><a name="removecommandrangeuihandler"></a>ICommandSource::RemoveCommandRangeUIHandler

Usuwa grupę programów obsługi komunikatów polecenia interfejsu użytkownika z obiektu źródłowego polecenia.

```cpp
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Parametry

*cmdIDMin*<br/>
Indeks początkowy zakresu identyfikatora polecenia.
*cmdIDMax*<br/>
Końcowy indeks zakresu identyfikatora polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa z obiektu źródłowego polecenia polecenia grupy programów obsługi poleceń interfejsu użytkownika, mapowanych na identyfikatory poleceń określone przez cmdIDMin i cmdIDMax.

## <a name="icommandsourceremovecommanduihandler"></a><a name="removecommanduihandler"></a>ICommandSource::RemoveCommandUIHandler

Usuwa program obsługi komunikatów polecenia interfejsu użytkownika z obiektu źródłowego polecenia.

```cpp
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*identyfikator cmdID*<br/>
Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa program obsługi komunikatów polecenia interfejsu użytkownika mapowany na cmdID z obiektu źródłowego polecenia.

## <a name="icommandsourcesendcommand"></a><a name="sendcommand"></a>ICommandSource::SendCommand

Wysyła wiadomość i czeka na jej przetworzenie przed zwróceniem.

```cpp
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*Polecenia*<br/>
Identyfikator polecenia wiadomości, która ma zostać wysłana.

### <a name="remarks"></a>Uwagi

Ta metoda synchronicznie wysyła wiadomość mapowane do identyfikatora określonego przez polecenie. Wywołuje CWnd::SendMessage umieścić wiadomość w kolejce komunikatów okna i czeka, aż procedura tego okna przetworzy wiadomość przed zwróceniem.

## <a name="see-also"></a>Zobacz też

[Instrukcje: dodawanie routingu poleceń do formantu interfejsu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Klasa ICommandTarget](../../mfc/reference/icommandtarget-interface.md)

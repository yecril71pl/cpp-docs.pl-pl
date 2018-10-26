---
title: Klasa Icommandsource | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4908566a80fcad2350023f2306a952b2d97b2e62
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060679"
---
# <a name="icommandsource-interface"></a>Klasa Icommandsource

Zarządza polecenia wysyłane z obiektu źródła polecenia do kontrolki użytkownika.

## <a name="syntax"></a>Składnia

```
interface class ICommandSource
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[ICommandSource::AddCommandHandler](#addcommandhandler)|Dodaje procedurę obsługi poleceń do obiektu źródła polecenia.|
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|Dodaje grupę programy obsługi poleceń do obiektu źródła polecenia.|
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|Dodaje grupę obsługi komunikatów poleceń interfejsu użytkownika do obiektu źródła polecenia.|
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|Dodaje program obsługi komunikatów poleceń interfejsu użytkownika do obiektu źródła polecenia.|
|[ICommandSource::PostCommand](#postcommand)|Publikuje komunikat bez oczekiwania na przetworzenie.|
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|Usuwa procedurę obsługi poleceń z obiektu źródła polecenia.|
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Usuwa grupę programy obsługi poleceń z obiektu źródła polecenia.|
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Usuwa grupę obsługi komunikatów poleceń interfejsu użytkownika z obiektu źródła polecenia.|
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|Usuwa obsługi komunikatów poleceń interfejsu użytkownika z obiektu źródła polecenia.|
|[ICommandSource::SendCommand](#sendcommand)|Wysyła komunikat i czeka na jego przetworzenie przed zwróceniem.|

### <a name="remarks"></a>Uwagi

Hostowanie kontrolki użytkownika w widoku MFC [klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md) polecenia tras i aktualizacja poleceń interfejsu użytkownika wiadomości do formantu użytkownika, aby zezwalała na obsługę jego poleceń MFC (na przykład ramek elementów menu i przycisków paska narzędzi). Implementując [klasa Icommandtarget](../../mfc/reference/icommandtarget-interface.md), podać odwołanie do formantu użytkownika `ICommandSource` obiektu.

Zobacz [porady: Dodawanie routingu poleceń do formantu programu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `ICommandTarget`.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

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

Ta metoda dodaje cmdHandler obsługi polecenia do obiektu źródła polecenia i mapuje cmdID program obsługi.
Zobacz [porady: Dodawanie routingu poleceń do formantu programu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia AddCommandHandler.

## <a name="addcommandrangehandler"></a> ICommandSource::AddCommandRangeHandler

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

## <a name="addcommandrangeuihandler"></a> ICommandSource::AddCommandRangeUIHandler

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

## <a name="addcommanduihandler"></a> ICommandSource::AddCommandUIHandler

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

Ta metoda dodaje użytkownika interfejsu polecenia komunikatu obsługi cmdHandler do obiektu źródła polecenia i mapuje cmdID program obsługi.

## <a name="postcommand"></a> ICommandSource::PostCommand

Publikuje komunikat bez oczekiwania na przetworzenie.
```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*Polecenie*<br/>
Identyfikator polecenia wiadomość do opublikowania.
### <a name="remarks"></a>Uwagi

Ta metoda asynchronicznie publikuje komunikat zamapowane na identyfikator określony przez polecenie. Jego wywołuje CWnd::PostMessage można umieścić komunikatu w kolejce komunikatów okna i zwraca bez oczekiwania na odpowiednie okno przetworzyć komunikatu.

## <a name="removecommandhandler"></a> ICommandSource::RemoveCommandHandler

Usuwa procedurę obsługi poleceń z obiektu źródła polecenia.
```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.
### <a name="remarks"></a>Uwagi

Ta metoda usuwa mapowane na cmdID z obiektu źródła polecenia program obsługi poleceń.

## <a name="removecommandrangecommandhandler"></a> ICommandSource::RemoveCommandRangeHandler

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

Ta metoda usuwa grupę programy obsługi komunikatów, mapowane do określonych identyfikatorów poleceń cmdIDMin i cmdIDMax, z obiektu źródła polecenia.

## <a name="removecommandrangeuihandler"></a> ICommandSource::RemoveCommandRangeUIHandler

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

Ta metoda usuwa grupę użytkownika interfejsu polecenia programy obsługi komunikatów, mapowane do określonych identyfikatorów poleceń cmdIDMin i cmdIDMax, z obiektu źródła polecenia.

## <a name="removecommanduihandler"></a> ICommandSource::RemoveCommandUIHandler

Usuwa obsługi komunikatów poleceń interfejsu użytkownika z obiektu źródła polecenia.
```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.
### <a name="remarks"></a>Uwagi

Ta metoda usuwa obsługi komunikatów poleceń interfejsu użytkownika mapowane na cmdID z obiektu źródła polecenia.

## <a name="sendcommand"></a> ICommandSource::SendCommand

Wysyła komunikat i czeka na jego przetworzenie przed zwróceniem.
```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Parametry

*Polecenie*<br/>
Identyfikator polecenia komunikatu do wysłania.
### <a name="remarks"></a>Uwagi

Ta metoda synchronicznie wysyła komunikat zamapowane na identyfikator określony przez polecenie. On wywołuje CWnd::SendMessage można umieścić komunikatu w kolejce komunikatów okna i czeka, aż tej procedury okna przetworzeniu komunikatu przed zwróceniem.
## <a name="see-also"></a>Zobacz też

[Instrukcje: dodawanie routingu poleceń do formantu interfejsu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Klasa ICommandTarget](../../mfc/reference/icommandtarget-interface.md)

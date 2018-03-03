---
title: Interfejs ICommandSource | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc8ad34ccce059caca8e86a014622e29c14022ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="icommandsource-interface"></a>Interfejs ICommandSource
Zarządza polecenia przesyłane z obiektem źródłowym polecenia do kontrolki użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
interface class ICommandSource  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ICommandSource::AddCommandHandler](#addcommandhandler)|Dodaje programem obsługi do obiektu źródłowego polecenia.|  
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|Dodaje grupę programy obsługi poleceń do obiektu źródłowego polecenia.|  
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|Dodaje grupę programów obsługi wiadomości polecenia interfejsu użytkownika do obiektu źródłowego polecenia.|  
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|Dodaje program obsługi komunikatów polecenia interfejsu użytkownika do obiektu źródłowego polecenia.|  
|[ICommandSource::PostCommand](#postcommand)|Zapisuje komunikat bez oczekiwania na przetworzenie.|  
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|Usuwa programem obsługi z obiektem źródłowym polecenia.|  
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Usuwa grupę programy obsługi poleceń z obiektem źródłowym polecenia.|  
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Usuwa grupę programów obsługi wiadomości polecenia interfejsu użytkownika z obiektem źródłowym polecenia.|  
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|Usuwa program obsługi komunikatów polecenia interfejsu użytkownika z obiektem źródłowym polecenia.|  
|[ICommandSource::SendCommand](#sendcommand)|Wysyła komunikat i czeka na jego przetworzenie przed zwróceniem.|  
  
### <a name="remarks"></a>Uwagi  
 Kiedy host kontrolkę użytkownika w widoku MFC [klasy CWinFormsView](../../mfc/reference/cwinformsview-class.md) polecenia tras i aktualizacji polecenia interfejsu użytkownika wiadomości do kontrolki użytkownika, aby umożliwić jego poleceń MFC (na przykład elementów menu ramki i przycisków paska narzędzi). Zaimplementowanie [interfejsu obiektu ICommandTarget](../../mfc/reference/icommandtarget-interface.md), nadaj odwołanie do kontrolki użytkownika `ICommandSource` obiektu.  
  
 Zobacz [porady: dodawanie do formantu formularzy systemu Windows Routing poleceń](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia `ICommandTarget`.  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)  
  
## <a name="addcommandhandler"></a>ICommandSource::AddCommandHandler
Dodaje programem obsługi do obiektu źródłowego polecenia.
```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parametry  
`cmdID`  
Identyfikator polecenia.  
`cmdHandler`  
Dojście do metody obsługi poleceń.

### <a name="remarks"></a>Uwagi
Ta metoda dodaje cmdHandler obsługi polecenia do obiektu źródłowego polecenia i mapowania programu obsługi do z cmdID.
Zobacz [porady: dodawanie do formantu formularzy systemu Windows Routing poleceń](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) przykład sposobu użycia AddCommandHandler.

## <a name="addcommandrangehandler"></a>ICommandSource::AddCommandRangeHandler

Dodaje grupę programy obsługi poleceń do obiektu źródłowego polecenia.
```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```
### <a name="parameters"></a>Parametry  
`cmdIDMin`  
Indeks początkowy zakres Identyfikatora polecenia.
`cmdIDMax`  
Indeks końcowy zakres Identyfikatora polecenia.
`cmdHandler`  
Dojście do metody obsługi wiadomości zamapowany poleceń.
### <a name="remarks"></a>Uwagi
Ta metoda mapuje ciągły zakres identyfikatorów poleceń do obsługi wiadomości i dodaje go do obiektu źródłowego polecenia. Służy to do obsługi grupy przycisków powiązane z jedną z metod.

## <a name="addcommandrangeuihandler"></a>ICommandSource::AddCommandRangeUIHandler
Dodaje grupę programów obsługi wiadomości polecenia interfejsu użytkownika do obiektu źródłowego polecenia.
```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin, 
    unsigned int cmdIDMax, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>Parametry  
`cmdIDMin`  
Indeks początkowy zakres Identyfikatora polecenia.
`cmdIDMax`  
Indeks końcowy zakres Identyfikatora polecenia.
`cmdHandler`  
Dojście do metody obsługi wiadomości zamapowany poleceń.

### <a name="remarks"></a>Uwagi
Ta metoda mapuje ciągły zakres identyfikatorów poleceń do obsługi komunikatów polecenia interfejsu pojedynczego użytkownika i dodaje go do obiektu źródłowego polecenia. Służy to do obsługi grupy przycisków powiązane z jedną z metod.

## <a name="addcommanduihandler"></a>ICommandSource::AddCommandUIHandler
Dodaje program obsługi komunikatów polecenia interfejsu użytkownika do obiektu źródłowego polecenia.
```
void AddCommandUIHandler(
    unsigned int cmdID, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>Parametry
`cmdID`  
Identyfikator polecenia.  
`cmdUIHandler`  
Dojście do metody obsługi wiadomości polecenia interfejsu użytkownika.

### <a name="remarks"></a>Uwagi
Ta metoda dodaje użytkownika interfejsu polecenia komunikat obsługi cmdHandler do obiektu źródłowego polecenia i mapowania programu obsługi do z cmdID.

## <a name="postcommand"></a>ICommandSource::PostCommand
Zapisuje komunikat bez oczekiwania na przetworzenie.
```
void PostCommand(unsigned int command);
```
### <a name="parameters"></a>Parametry
`command`  
Identyfikator polecenia komunikatu zaksięgowania.
### <a name="remarks"></a>Uwagi
Ta metoda asynchronicznie zapisuje komunikat zamapowane na identyfikator określony przez polecenie. Go wywołuje CWnd::PostMessage do umieszczenia wiadomości w kolejce wiadomości okna, a następnie zwraca bez oczekiwania na odpowiednie okno, aby przetworzyć komunikatu.


## <a name="removecommandhandler"></a>ICommandSource::RemoveCommandHandler
Usuwa programem obsługi z obiektem źródłowym polecenia.
```
void RemoveCommandHandler(unsigned int cmdID);
```
### <a name="parameters"></a>Parametry
`cmdID`  
Identyfikator polecenia.
### <a name="remarks"></a>Uwagi
Ta metoda usuwa mapowane na cmdID z obiektu źródłowego polecenia program obsługi poleceń.


## <a name="removecommandrangecommandhandler"></a>ICommandSource::RemoveCommandRangeHandler 
Usuwa grupę programy obsługi poleceń z obiektem źródłowym polecenia.
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```
### <a name="parameters"></a>Parametry
`cmdIDMin`  
Indeks początkowy zakres Identyfikatora polecenia.
`cmdIDMax`  
Indeks końcowy zakres Identyfikatora polecenia.
### <a name="remarks"></a>Uwagi
Ta metoda usuwa grupę programów obsługi wiadomości, zamapowany na określono identyfikatorów poleceń cmdIDMin i cmdIDMax, z polecenia obiektu źródłowego.

## <a name="removecommandrangeuihandler"></a>ICommandSource::RemoveCommandRangeUIHandler 
Usuwa grupę programów obsługi wiadomości polecenia interfejsu użytkownika z obiektem źródłowym polecenia.
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```
### <a name="parameters"></a>Parametry
`cmdIDMin`  
Indeks początkowy zakres Identyfikatora polecenia.
`cmdIDMax`  
Indeks końcowy zakres Identyfikatora polecenia.
### <a name="remarks"></a>Uwagi
Ta metoda usuwa grupę użytkownika interfejsu polecenie Programy obsługi wiadomości, zamapowany na określono identyfikatorów poleceń cmdIDMin i cmdIDMax, z obiektu źródłowego polecenia.

## <a name="removecommanduihandler"></a>ICommandSource::RemoveCommandUIHandler 
Usuwa program obsługi komunikatów polecenia interfejsu użytkownika z obiektem źródłowym polecenia.
```
void RemoveCommandUIHandler(unsigned int cmdID);
```
### <a name="parameters"></a>Parametry
`cmdID`  
Identyfikator polecenia.
### <a name="remarks"></a>Uwagi
Ta metoda usuwa obsługi wiadomości polecenia interfejsu użytkownika zamapowany na cmdID z polecenia obiektu źródłowego.

## <a name="sendcommand"></a>ICommandSource::SendCommand 
Wysyła komunikat i czeka na jego przetworzenie przed zwróceniem.
```
void SendCommand(unsigned int command);
```
### <a name="parameters"></a>Parametry
`command`  
Identyfikator polecenia komunikatu do wysłania.
### <a name="remarks"></a>Uwagi
Ta metoda synchronicznie wysyła wiadomość zamapowane na identyfikator określony przez polecenie. Wywołuje CWnd::SendMessage do umieszczenia wiadomości w kolejce wiadomości okna, a czeka, aż tej procedury okna przed zwróceniem przetworzył wiadomość.
## <a name="see-also"></a>Zobacz też  
 [Porady: Dodawanie polecenia routingu do systemu Windows formantu formularzy](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [Klasa ICommandTarget](../../mfc/reference/icommandtarget-interface.md)

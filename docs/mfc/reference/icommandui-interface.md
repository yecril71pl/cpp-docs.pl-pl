---
title: Interfejs ICommandUI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
dev_langs:
- C++
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 70e6f1eb8848c5ee93063877ae036f66584b69c4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icommandui-interface"></a>Interfejs ICommandUI
Zarządza polecenia interfejsu użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
interface class ICommandUI  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[icommandui__Check](#check)|Ustawia element interfejsu użytkownika dla tego polecenia w stanie odpowiedniego wyboru.|  
|[ICommandUI::ContinueRouting](#continuerouting)|Określa, że nadal routingu do bieżącej wiadomości w łańcuchu obsługi mechanizmu routing poleceń.|  
|[ICommandUI::Enabled](#enabled)|Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia.|  
|[ICommandUI::ID](#id)|Pobiera identyfikator obiektu interfejsu użytkownika reprezentowanego przez `ICommandUI` obiektu.|  
|[ICommandUI::Index](#index)|Pobiera indeks obiektu interfejsu użytkownika reprezentowanego przez `ICommandUI` obiektu.|  
|[ICommandUI::Radio](#radio)|Ustawia element interfejsu użytkownika dla tego polecenia w stanie odpowiedniego wyboru.|  
|[ICommandUI::Text](#text)|Ustawia tekst elementu interfejsu użytkownika dla tego polecenia.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs udostępnia metody i właściwości, które zarządzają polecenia interfejsu użytkownika. `ICommandUI` przypomina [ccmdui — klasa](../../mfc/reference/ccmdui-class.md), ale `ICommandUI` jest używana dla aplikacji MFC, które współdziałają z składniki platformy .NET.  
  
 `ICommandUI` jest używany w ramach `ON_UPDATE_COMMAND_UI` obsługi w [obiektu ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-klasy. Gdy użytkownik aplikacji aktywuje (wybiera lub kliknięć) menu, każdy element menu jest wyświetlany jako włączona lub wyłączona. Elementem docelowym każdego polecenia menu udostępnia te informacje zaimplementowanie `ON_UPDATE_COMMAND_UI` obsługi. Dla każdego z obiektów interfejsu użytkownika poleceń w aplikacji umożliwiają utworzenie wpisu mapy wiadomości i prototypu funkcji obsługi każdego okna właściwości.  
  
 Aby uzyskać więcej informacji na temat sposobu `ICommandUI` interfejs jest używany w routing poleceń, zobacz [porady: Dodawanie polecenia routingu do formantu formularzy systemu Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 Aby uzyskać więcej informacji dotyczących sposobu zarządzania polecenia interfejsu użytkownika w MFC, zobacz [ccmdui — klasa](../../mfc/reference/ccmdui-class.md).  
  
## <a name="check"></a> ICommandUI::Check  
Ustawia element interfejsu użytkownika dla tego polecenia w stanie odpowiedniego wyboru.
```
property UICheckState Check;
```
## <a name="remarks"></a>Uwagi  
Dana właściwość ustawia element interfejsu użytkownika dla tego polecenia do stanu odpowiedniego wyboru. Sprawdź, ustaw następujące wartości:  
- Usuń zaznaczenie 0  
- Sprawdź 1  
- Ustaw nieokreślony 2  

## <a name="continuerouting"></a> ICommandUI::ContinueRouting   
Określa, że mechanizm routingu polecenia kontynuować routingu do bieżącej wiadomości w łańcuchu programów obsługi.
```
void ContinueRouting();
```
## <a name="remarks"></a>Uwagi
To jest funkcja Zaawansowane elementu członkowskiego, które mają być używane w połączeniu z programem obsługi on_command_ex —, która zwraca wartość FALSE. Aby uzyskać więcej informacji, zobacz techniczne Uwaga TN006: mapy komunikatów.

## <a name="enabled"></a> ICommandUI::Enabled 
Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia.
```
property bool Enabled;
```
## <a name="remarks"></a>Uwagi
Tej właściwości Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia. Włączone, aby należy ustawić wartość TRUE powoduje włączenie elementu wartość FALSE, aby ją wyłączyć.

## <a name="id"></a> ICommandUI::ID  
Pobiera identyfikator reprezentowanych przez obiekt ICommandUI obiekt interfejsu użytkownika.
```
property unsigned int ID;
```
## <a name="remarks"></a>Uwagi
Ta właściwość pobiera identyfikator (dojścia) element menu, przycisk paska narzędzi lub innych reprezentowanych przez obiekt ICommandUI obiekt interfejsu użytkownika.

## <a name="index"></a> ICommandUI::Index   
Pobiera indeks reprezentowanych przez obiekt ICommandUI obiekt interfejsu użytkownika.
```
property unsigned int Index;
```
## <a name="remarks"></a>Uwagi
Ta właściwość pobiera indeks (dojścia) element menu, przycisk paska narzędzi lub innych reprezentowanych przez obiekt ICommandUI obiekt interfejsu użytkownika.

## <a name="radio"></a> ICommandUI::Radio 
Ustawia element interfejsu użytkownika dla tego polecenia w stanie odpowiedniego wyboru.
```
property bool Radio;
```
## <a name="remarks"></a>Uwagi
Dana właściwość ustawia element interfejsu użytkownika dla tego polecenia do stanu odpowiedniego wyboru. Zestaw opcji na wartość TRUE powoduje włączenie elementu; w przeciwnym razie wartość FALSE.

## <a name="text"></a> ICommandUI::Text 
Ustawia tekst elementu interfejsu użytkownika dla tego polecenia.
```
property String^ Text;
```
## <a name="remarks"></a>Uwagi
Ta właściwość określa tekst elementu interfejsu użytkownika dla tego polecenia. Ustawianie tekstu do uchwytu ciągu tekstowego.

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CCmdUI](../../mfc/reference/ccmdui-class.md)

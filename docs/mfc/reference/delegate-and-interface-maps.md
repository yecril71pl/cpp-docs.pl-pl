---
title: Delegat i interfejs mapy makra (MFC) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 03/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9767c8b92316ffb9e458ba650e28db9ddf1a095b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
|||  
|-|-|  
|[BEGIN_DELEGATE_MAP —](#begin_delegate_map)|Rozpoczyna się mapy delegata.|
|[BEGIN_INTERFACE_MAP —](#begin_interface_map)|Rozpoczyna się definicję planu podłączony.|
|[Commandhandler — obiekt delegowany](#commandhandler)|Rejestruje wywołanie zwrotne metody źródło polecenia.  |
|[END_DELEGATE_MAP —](#end_delegate_map)|Kończy się mapy delegata.|
|[END_INTERFACE_MAP —](#end_interface_map)|Kończy się na mapie interfejsu w pliku implementacji. |
|[EVENT_DELEGATE_ENTRY —](#event_delegate_entry)|Tworzy wpis w mapie delegata.|
|[INTERFACE_PART —](#interface_part)|Używany podczas komunikacji między `BEGIN_INTERFACE_MAP` makro i `END_INTERFACE_MAP` makro dla każdego interfejsu obiektu będzie obsługiwać.|
|[MAKE_DELEGATE —](#make_delegate)|Dołącza program obsługi zdarzeń do zarządzanego formantu.|


## <a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP —
Rozpoczyna się mapy delegata.  
   
### <a name="syntax"></a>Składnia    
```  
BEGIN_DELEGATE_MAP(  CLASS );  
```
### <a name="parameters"></a>Parametry  
 `CLASS`  
 Klasa, w którym jest hostowany zarządzanego formantu.  
   
### <a name="remarks"></a>Uwagi  
 To makro oznacza początek listy wpisów delegata, które tworzą mapy delegata. Na przykład sposobu używania tego makra, zobacz [event_delegate_entry —](#event_delegate_entry).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** msclr\event.h  
   
### <a name="see-also"></a>Zobacz też  
 [Instrukcje: wychwytywanie zdarzeń interfejsu Windows Forms z klas natywnych języka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)
 
##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP —
Rozpoczyna się definicji podłączony mapy, gdy są używane w pliku implementacji.  
   
### <a name="syntax"></a>Składnia    
```
BEGIN_INTERFACE_MAP( theClass, baseClass )  
```
### <a name="parameters"></a>Parametry  
 `theClass`  
 Klasy, w którym ma być zdefiniowana mapy interfejsu  
  
 `baseClass`  
 Klasy, z którego `theClass` pochodną.  
   
### <a name="remarks"></a>Uwagi  
 Dla każdego interfejsu, która jest zaimplementowana, istnieje co najmniej jeden `INTERFACE_PART` makro wywołań. Dla każdego wartość zagregowaną, która korzysta z klasy, istnieje **INTERFACE_AGGREGATE** wywołanie makra.  
  
 Aby uzyskać więcej informacji na map interfejsów, zobacz [38 Uwaga techniczna](../tn038-mfc-ole-iunknown-implementation.md).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
 
##  <a name="commandhandler"></a>Commandhandler — obiekt delegowany
Rejestruje wywołanie zwrotne metody źródło polecenia.  
   
### <a name="syntax"></a>Składnia    
```  
delegate void CommandHandler(  UINT^ cmdID  );  
```
### <a name="parameters"></a>Parametry  
 `cmdID`  
 Identyfikator polecenia.  
   
### <a name="remarks"></a>Uwagi  
 Ten delegat rejestruje metody wywołania zwrotnego z źródło polecenia. Po dodaniu delegata do obiektu źródłowego polecenia metody wywołania zwrotnego staje się obsługi dla poleceń pochodzących z określonego źródła.  
  
 Aby uzyskać więcej informacji, zobacz [porady: dodawanie do formantu formularzy systemu Windows Routing poleceń](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)  
   
### <a name="see-also"></a>Zobacz też  
 [Instrukcje: dodawanie routingu poleceń do formantu interfejsu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)
 
##  <a name="commanduihandler"></a>Commanduihandler — obiekt
Rejestruje metody wywołania zwrotnego komunikat polecenia aktualizacji interfejsu użytkownika.  
   
### <a name="syntax"></a>Składnia    
```  
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);  
```
### <a name="parameters"></a>Parametry  
 `cmdID`  
 Identyfikator polecenia.  
  
 `cmdUI`  
 Identyfikator polecenia komunikatu.  
   
### <a name="remarks"></a>Uwagi  
 Ten delegat rejestruje metody wywołania zwrotnego komunikat polecenia aktualizacji interfejsu użytkownika. `CommandUIHandler`przypomina [commandhandler — obiekt](#commandhandler) z tą różnicą, że ten delegat jest używany z polecenia aktualizacji obiektu interfejsu użytkownika. Polecenia aktualizacji interfejsu użytkownika należy mapować w jeden do jednego z metody obsługi wiadomości.  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)  
   
### <a name="see-also"></a>Zobacz też  
 [Porady: Dodawanie polecenia routingu do systemu Windows formantu formularzy](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [CommandHandler](#commandhandler)

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP —
Kończy się mapy delegata.  
   
### <a name="syntax"></a>Składnia    
```  
END_DELEGATE_MAP();  
```  
   
### <a name="remarks"></a>Uwagi  
 To makro oznacza koniec listy wpisów delegata, które tworzą mapy delegata. Na przykład sposobu używania tego makra, zobacz [event_delegate_entry —](#event_delegate_entry).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** msclr\event.h  
   
### <a name="see-also"></a>Zobacz też  

 [Instrukcje: wychwytywanie zdarzeń interfejsu Windows Forms z klas natywnych języka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

 
##  <a name="end_interface_map"></a>END_INTERFACE_MAP —
Kończy się na mapie interfejsu w pliku implementacji.  
   
### <a name="syntax"></a>Składnia    
```
END_INTERFACE_MAP( )    
```  
   
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat map interfejsów, temacie [38 Uwaga techniczna](../tn038-mfc-ole-iunknown-implementation.md).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [BEGIN_INTERFACE_MAP —](#begin_interface_map)
 

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY —
Tworzy wpis w mapie delegata.  
   
### <a name="syntax"></a>Składnia    
```  
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);  
```
### <a name="parameters"></a>Parametry  
 `MEMBER`  
 Metoda obsługi zdarzeń jest dołączony do formantu.  
  
 `ARG0`  
 Pierwszy argument metoda obsługi zdarzeń zarządzanych, takich jak **Object ^**.  
  
 `ARG1`  
 Drugi argument funkcji metoda obsługi zdarzeń zarządzanych, takich jak **EventArgs ^**.  
   
### <a name="remarks"></a>Uwagi  
 Każdy wpis w mapie delegata odpowiada delegata obsługi zarządzanych zdarzeń utworzonych przez [make_delegate —](#make_delegate).  
   
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób użycia `EVENT_DELEGATE_ENTRY` utworzyć wpis w mapie delegowanego dla `OnClick` obsługi zdarzeń; Zobacz też przykładowy kod w `MAKE_DELEGATE`. Aby uzyskać więcej informacji, zobacz [porady: obiekt Sink zdarzenia formularzy systemu Windows z natywnego klas C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).  
  
 ```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()

```  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** msclr\event.h  
   
### <a name="see-also"></a>Zobacz też  
 [MAKE_DELEGATE —](#make_delegate)   
 [BEGIN_DELEGATE_MAP —](#begin_delegate_map)   
 [END_DELEGATE_MAP —](#end_delegate_map)
 

##  <a name="interface_part"></a>INTERFACE_PART —
Używany podczas komunikacji między `BEGIN_INTERFACE_MAP` makro i `END_INTERFACE_MAP` makro dla każdego interfejsu obiektu będzie obsługiwać.  
   
### <a name="syntax"></a>Składnia    
```
INTERFACE_PART( theClass, iid, localClass)  
```
### <a name="parameters"></a>Parametry  
 `theClass`  
 Nazwa klasy zawierającej mapy interfejsu.    
 `iid`  
 Identyfikator IID, który ma być zmapowana do osadzonego klasy.    
 *localClass*  
 Nazwa klasy lokalnej.  
   
### <a name="remarks"></a>Uwagi  
 Umożliwia mapowanie identyfikatora IID do elementu członkowskiego klasy oznaczona `theClass` i *localClass*.  
  
 Aby uzyskać więcej informacji na map interfejsów, zobacz [38 Uwaga techniczna](../tn038-mfc-ole-iunknown-implementation.md).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
   
 
##  <a name="make_delegate"></a>MAKE_DELEGATE —
Dołącza program obsługi zdarzeń do zarządzanego formantu.  
   
### <a name="syntax"></a>Składnia    
```  
MAKE_DELEGATE( DELEGATE,  MEMBER) ;  
```
### <a name="parameters"></a>Parametry  
 `DELEGATE`  
 Typem obsługi zdarzeń zarządzanych delegować, takich jak [EventHandler](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True).  
  
 `MEMBER`  
 Nazwa metody obsługi zdarzeń jest dołączony do formantu.  
   
### <a name="remarks"></a>Uwagi  
 To makro tworzy delegata obsługi zdarzeń zarządzanego typu `DELEGATE` i nazwy `MEMBER`. Obiektu delegowanego obsługi zdarzeń zarządzanych umożliwia klasy natywnej do obsługi zdarzeń zarządzanych.  
   
### <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób wywoływania `MAKE_DELEGATE` dołączyć `OnClick` program obsługi zdarzeń do formantu MFC `MyControl`. Dla szerszego opis działania tego makra w aplikacji MFC, zobacz [porady: obiekt Sink zdarzenia formularzy systemu Windows z natywnego klas C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).  
  
```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** msclr\event.h  
   
### <a name="see-also"></a>Zobacz też  
 [BEGIN_DELEGATE_MAP —](#begin_delegate_map)   
 [END_DELEGATE_MAP —](#end_delegate_map)   
 [EVENT_DELEGATE_ENTRY —](#event_delegate_entry)
 




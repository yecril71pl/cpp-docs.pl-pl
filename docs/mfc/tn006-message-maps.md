---
title: 'TN006: Mapy wiadomości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.messages.maps
dev_langs:
- C++
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- ON_NOTIFY_RANGE macro [MFC]
- ON_COMMAND macro [MFC]
- ON_CONTROL_RANGE macro [MFC]
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_NOTIFY message [MFC]
- ON_COMMAND_RANGE_EX macro [MFC]
- ON_MESSAGE macro [MFC]
- Windows messages [MFC], message maps
- ON_COMMAND_RANGE macro [MFC]
- TN006
- ON_CONTROL macro [MFC]
- ON_COMMAND_EX macro [MFC]
- message maps [MFC], Windows messaging
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ec424729a7bd0eb4da9ec62282ff2aafd4da133
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955561"
---
# <a name="tn006-message-maps"></a>TN006: mapy komunikatów
Ta uwaga opisuje funkcja mapy komunikatów MFC.  
  
## <a name="the-problem"></a>Problem  
 Microsoft Windows implementuje funkcje wirtualne w klasach okna, które skorzystać z jego funkcji obsługi komunikatów. Z powodu dużej liczby komunikatów związane zapewnienie osobnych funkcji wirtualnej dla każdej wiadomości Windows spowodowałoby vtable zbyt duża.  
  
 Ponieważ liczbę komunikatów zdefiniowanych w systemie Windows zmienia się wraz z upływem czasu, ponieważ aplikacje można zdefiniować własne komunikaty systemu Windows, mapy wiadomości zapewnienia poziomu pośredni uniemożliwiający istniejący kod fundamentalne zmiany interfejsu.  
  
## <a name="overview"></a>Omówienie  
 MFC stanowi alternatywę dla instrukcji switch, który był używany w tradycyjnych programów systemu Windows do obsługi wiadomości wysyłane do okna. Mapowanie komunikatów do metod można zdefiniować tak, aby po odebraniu komunikatu przez okno odpowiednie metoda jest wywoływana automatycznie. Tej funkcji mapy komunikatów zaprojektowano tak, aby przypominały funkcje wirtualne, ale ma dodatkowe korzyści z funkcji wirtualnych C++ nie jest możliwe.  
  
## <a name="defining-a-message-map"></a>Definiowanie mapy komunikatów  
 [Declare_message_map —](reference/message-map-macros-mfc.md#declare_message_map) Makro deklaruje trzy elementy członkowskie klasy.  
  
-   Wywołuje tablicy prywatnej wpisów AFX_MSGMAP_ENTRY *_messageEntries*.  
  
-   Wywołuje chronionych struktury AFX_MSGMAP *messageMap* wskazującego *_messageEntries* tablicy.  
  
-   A chronione funkcji wirtualnej o nazwie `GetMessageMap` zwracającą adres *messageMap*.  
  
 To makro należy umieścić w deklaracji klasy przy użyciu mapy komunikatów. Według Konwencji jest na końcu deklaracji klasy. Na przykład:  
  
```  
class CMyWnd : public CMyParentWndClass  
{ *// my stuff...  
 
protected: *//{{AFX_MSG(CMyWnd)  
    afx_msg void OnPaint();
*//}}AFX_MSG  
 
    DECLARE_MESSAGE_MAP() 
};  
```  
  
 Jest to format wygenerowanych przez kreatorami AppWizard i ClassWizard podczas tworzenia nowych klas. / / {{I / /}} nawiasy kwadratowe są potrzebne dla ClassWizard.  
  
 Mapy wiadomości tabela będzie zdefiniowana przy użyciu zestawu makr, które rozszerzają na wpisy mapy wiadomości. Tabela rozpoczyna się od [begin_message_map —](reference/message-map-macros-mfc.md#begin_message_map) wywołanie makra, który definiuje klasę, która jest obsługiwany przez ten mapy komunikatów i klasy nadrzędnej, do którego są przekazywane nieobsługiwany wiadomości. Kończy tabeli [end_message_map —](reference/message-map-macros-mfc.md#end_message_map) wywołanie makra.  
  
 Między wywołaniami tych dwóch makro jest wpis dla każdego komunikatu mają być obsługiwane przez ten mapy komunikatów. Każdy standardowych komunikatów systemu Windows ma makra w postaci ON_WM_*MESSAGE_NAME* generujący wpis dla tej wiadomości.  
  
 Podpis standardowa funkcja został zdefiniowany dla rozpakowanie parametrach każdy komunikat systemu Windows i zapewnienia bezpieczeństwa typu. Te podpisy można znaleźć w pliku Afxwin.h w deklaracji z [CWnd](../mfc/reference/cwnd-class.md). Każdy z nich jest oznaczona jako ze słowem kluczowym **afx_msg** ułatwiający identyfikację.  
  
> [!NOTE]
>  ClassWizard wymaga użycia **afx_msg** — słowo kluczowe w Twojej deklaracje obsługi mapy wiadomości.  
  
 Te podpisy funkcja uzyskano przy użyciu prostego Konwencji. Nazwa funkcji zawsze rozpoczyna się od `"On`". To jest następuje nazwa komunikatów systemu Windows z "WM_" usunięte i pierwszą literę każdego wyrazu kapitalizacji. Kolejność parametrów jest *wParam* następuje `LOWORD`(*lParam*) następnie `HIWORD`(*lParam*). Nieużywane parametry nie są przekazywane. Wszystkie dojścia, które są kodowane przez klasy MFC są konwertowane na wskaźniki do odpowiednich obiektów MFC. Poniższy przykład przedstawia sposób obsłużyć komunikat WM_PAINT i spowodować `CMyWnd::OnPaint` funkcja wywoływana:  
  
```  
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass) *//{{AFX_MSG_MAP(CMyWnd)  
    ON_WM_PAINT() *//}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 Tabela mapy komunikatów musi być zdefiniowana poza zakresem żadnych definicji funkcji lub klasy. Nie należy go umieścić w bloku "C" extern.  
  
> [!NOTE]
>  ClassWizard zmodyfikuje wpisy mapy wiadomości, które mają miejsce między / / {{i / /}} komentarz nawiasu.  
  
## <a name="user-defined-windows-messages"></a>Komunikaty systemu Windows zdefiniowane przez użytkownika  
 Wiadomości zdefiniowane przez użytkownika może być zawarta w mapie komunikatów przy użyciu [on_message —](reference/message-map-macros-mfc.md#on_message) makra. To makro akceptuje liczba wiadomości, a także metodę formularza:  
  
"" * / / wewnątrz deklaracji klasy  
    afx_msg OnMyMessage(WPARAM wParam, LPARAM lParam) elementu LRESULT;

 
 #<a name="define-wmmymessage-wmuser--100"></a>Zdefiniuj WM_MYMESSAGE (WM_USER + 100)  
 
Begin_message_map — (CMyWnd, CMyParentWndClass)  
    On_message — (WM_MYMESSAGE, OnMyMessage)  
END_MESSAGE_MAP()  
```  
  
 In this example, we establish a handler for a custom message that has a Windows message ID derived from the standard WM_USER base for user-defined messages. The following example shows how to call this handler:  
  
```  
CWnd * pWnd =...;  
pWnd -> SendMessage(WM_MYMESSAGE);
```  
  
 The range of user-defined messages that use this approach must be in the range WM_USER to 0x7fff.  
  
> [!NOTE]
>  ClassWizard does not support entering ON_MESSAGE handler routines from the ClassWizard user interface. You must manually enter them from the Visual C++ editor. ClassWizard will parse these entries and let you browse them just like any other message-map entries.  
  
## Registered Windows Messages  
 The [RegisterWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms644947) function is used to define a new window message that is guaranteed to be unique throughout the system. The macro ON_REGISTERED_MESSAGE is used to handle these messages. This macro accepts a name of a *UINT NEAR* variable that contains the registered windows message ID. For example  
  
```  
Klasa CMyWnd: CMyParentWndClass publiczny  
{  
publiczny:  
    CMyWnd();

 *//{{AFX_MSG(CMyWnd)  
    afx_msg OnFind(WPARAM wParam, LPARAM lParam) elementu LRESULT; * //}}AFX_MSG  
 
    DECLARE_MESSAGE_MAP() 
};  
 
statyczne UINT NIEMAL WM_FIND = RegisterWindowMessage("COMMDLG_FIND");

 
*//{{AFX_MSG_MAP(CMyWnd) begin_message_map — (CMyWnd, CMyParentWndClass)  
    On_registered_message — (WM_FIND, OnFind) * //}}AFX_MSG_MAP  
END_MESSAGE_MAP()  
```  
  
 The registered Windows message ID variable (WM_FIND in this example) must be a *NEAR* variable because of the way ON_REGISTERED_MESSAGE is implemented.  
  
 The range of user-defined messages that use this approach will be in the range 0xC000 to 0xFFFF.  
  
> [!NOTE]
>  ClassWizard does not support entering ON_REGISTERED_MESSAGE handler routines from the ClassWizard user interface. You must manually enter them from the text editor. ClassWizard will parse these entries and let you browse them just like any other message-map entries.  
  
## Command Messages  
 Command messages from menus and accelerators are handled in message maps with the ON_COMMAND macro. This macro accepts a command ID and a method. Only the specific WM_COMMAND message that has a *wParam* equal to the specified command ID is handled by the method specified in the message-map entry. Command handler member functions take no parameters and return **void**. The macro has the following form:  
  
```  
On_command — (identyfikator, memberFxn)  
```  
  
 Command update messages are routed through the same mechanism, but use the ON_UPDATE_COMMAND_UI macro instead. Command update handler member functions take a single parameter, a pointer to a [CCmdUI](../mfc/reference/ccmdui-class.md) object, and return **void**. The macro has the form  
  
```  
On_update_command_ui — (identyfikator, memberFxn)  
```  
  
 Advanced users can use the ON_COMMAND_EX macro, which is an extended form of command message handlers. The macro provides a superset of the ON_COMMAND functionality. Extended command-handler member functions take a single parameter, a **UINT** that contains the command ID, and return a **BOOL**. The return value should be **TRUE** to indicate that the command has been handled. Otherwise routing will continue to other command target objects.  
  
 Examples of these forms:  
  
-   Inside Resource.h (usually generated by Visual C++)  
  
 ```  
 #<a name="define----idmycmd------100"></a>Zdefiniuj ID_MYCMD 100  
 #<a name="define----idcomplex----101"></a>Zdefiniuj ID_COMPLEX 101  
 ```  
  
-   Inside the class declaration  
  
 ```  
    afx_msg void OnMyCommand();
afx_msg void OnUpdateMyCommand (CCmdUI * pCmdUI);

    afx_msg BOOL OnComplexCommand(UINT nID);

 ```  
  
-   Inside the message map definition  
  
 ```  
    ON_COMMAND(ID_MYCMD,
    OnMyCommand)  
    ON_UPDATE_COMMAND_UI(ID_MYCMD,
    OnUpdateMyCommand)  
    ON_COMMAND_EX(ID_MYCMD,
    OnComplexCommand)  
 ```  
  
-   In the implementation file  
  
 ```  
    void CMyClass::OnMyCommand()  
 {* / / obsługuje polecenie  
 }  
 
    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)  
 {* / / Ustaw stan interfejsu użytkownika z pCmdUI  
 }  
 
    BOOL CMyClass::OnComplexCommand(UINT nID)  
 {* / / obsługuje polecenie  
    Zwraca wartość TRUE;  
 }  
 ```  
  
 Advanced users can handle a range of commands by using a single command handler: [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range) or ON_COMMAND_RANGE_EX. See the product documentation for more information about these macros.  
  
> [!NOTE]
>  ClassWizard supports creating ON_COMMAND and ON_UPDATE_COMMAND_UI handlers, but it does not support creating ON_COMMAND_EX or ON_COMMAND_RANGE handlers. However, Class Wizard will parse and let you browse all four command handler variants.  
  
## Control Notification Messages  
 Messages that are sent from child controls to a window have an extra bit of information in their message map entry: the control's ID. The message handler specified in a message map entry is called only if the following conditions are true:  
  
-   The control notification code (high word of *lParam*), such as BN_CLICKED, matches the notification code specified in the message-map entry.  
  
-   The control ID (*wParam*) matches the control ID specified in the message-map entry.  
  
 Custom control notification messages may use the [ON_CONTROL](reference/message-map-macros-mfc.md#on_control) macro to define a message map entry with a custom notification code. This macro has the form  
  
```  
On_control — (wNotificationCode, identyfikator, memberFxn)  
```  
  
 For advanced usage [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range) can be used to handle a specific control notification from a range of controls with the same handler.  
  
> [!NOTE]
>  ClassWizard does not support creating an ON_CONTROL or ON_CONTROL_RANGE handler in the user interface. You must manually enter them with the text editor. ClassWizard will parse these entries and let you browse them just like any other message map entries.  
  
 The Windows Common Controls use the more powerful [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) for complex control notifications. This version of MFC has direct support for this new message by using the ON_NOTIFY and ON_NOTIFY_RANGE macros. See the product documentation for more information about these macros.  
  
## See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)


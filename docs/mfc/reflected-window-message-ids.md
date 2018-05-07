---
title: Identyfikatory komunikatów okien odzwierciedlone | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OCM_CTLCOLORBTN
- OCM_PARENTNOTIFY
- OCM_VKEYTOITEM
- OCM_CTLCOLORSTATIC
- OCM_HSCROLL
- OCM_CHARTOITEM
- OCM_DRAWITEM
- OCM_MEASUREITEM
- OCM_COMPAREITEM
- OCM_COMMAND
- OCM_NOTIFY
- OCM_CTLCOLORMSGBOX
- OCM_DELETEITEM
- OCM_CTLCOLORLISTBOX
- OCM_CTLCOLORDLG
- OCM_CTLCOLOREDIT
- OCM_CTLCOLORSCROLLBAR
- OCM_VSCROLL
- OCM_CTLCOLOR
dev_langs:
- C++
helpviewer_keywords:
- OCM_HSCROLL message [MFC]
- OCM_PARENTNOTIFY message [MFC]
- messages, reflected
- reflected messages, window message Ids
- OCM_CTLCOLORDLG message [MFC]
- OCM_COMMAND message [MFC]
- OCM_CTLCOLORMSGBOX message [MFC]
- OCM_COMPAREITEM message [MFC]
- OCM_DRAWITEM message [MFC]
- OCM_VSCROLL message [MFC]
- OCM_CTLCOLOREDIT message [MFC]
- OCM_VKEYTOITEM message [MFC]
- OCM_CHARTOITEM message [MFC]
- OCM_CTLCOLORBTN message [MFC]
- OCM_CTLCOLORSTATIC message [MFC]
- OCM_MEASUREITEM message [MFC]
- OCM_CTLCOLOR message [MFC]
- OCM_CTLCOLORSCROLLBAR message [MFC]
- OCM_ messages
- OCM_DELETEITEM message [MFC]
- OCM_CTLCOLORLISTBOX message [MFC]
- OCM_NOTIFY message [MFC]
- reflected messages
ms.assetid: 3417ff51-ff9f-458c-bff4-17c200f00d96
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa6935c0fb9838c63c73e725da9f7b4e0fde4df4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="reflected-window-message-ids"></a>Identyfikatory odbitych komunikatów okien
Szybko utworzyć formantu ActiveX lub inny formant specjalne, jest do podklasy okna. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX MFC: Tworzenie podklasy kontrolki okna](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
 Aby uniemożliwić odbieranie komunikatów okien wysyłany przez kontrolkę podklasą Windows formantu kontenera [colecontrol —](../mfc/reference/colecontrol-class.md) tworzy okno "reflektora", aby przechwycić niektórych komunikatów okien i wyślij je do formantu. Kontrolki, w jego procedurę okna następnie może przetwarzać te komunikaty odbite przez podejmowanie działań odpowiednich dla formantu ActiveX.  
  
 W poniższej tabeli przedstawiono komunikaty, które są przechwytywane oraz odpowiednie komunikaty, które wysyła okna reflektora.  
  
|Komunikat wysyłany przez kontrolkę|Komunikat odzwierciedlana formantu|  
|---------------------------------|--------------------------------------|  
|[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)|**OCM_COMMAND —**|  
|[WM_CTLCOLORBTN](http://msdn.microsoft.com/library/windows/desktop/bb761849)|**OCM_CTLCOLORBTN —**|  
|[WM_CTLCOLOREDIT](http://msdn.microsoft.com/library/windows/desktop/bb761691)|**OCM_CTLCOLOREDIT —**|  
|[WM_CTLCOLORDLG](http://msdn.microsoft.com/library/windows/desktop/ms645417)|**OCM_CTLCOLORDLG —**|  
|[WM_CTLCOLORLISTBOX](http://msdn.microsoft.com/library/windows/desktop/bb761360)|**OCM_CTLCOLORLISTBOX —**|  
|[WM_CTLCOLORSCROLLBAR](http://msdn.microsoft.com/library/windows/desktop/bb787573)|**OCM_CTLCOLORSCROLLBAR —**|  
|[WM_CTLCOLORSTATIC](http://msdn.microsoft.com/library/windows/desktop/bb787524)|**OCM_CTLCOLORSTATIC —**|  
|[WM_DRAWITEM](http://msdn.microsoft.com/library/windows/desktop/bb775923)|**OCM_DRAWITEM —**|  
|[WM_MEASUREITEM](http://msdn.microsoft.com/library/windows/desktop/bb775925)|**OCM_MEASUREITEM —**|  
|[WM_DELETEITEM](http://msdn.microsoft.com/library/windows/desktop/bb761362)|**OCM_DELETEITEM —**|  
|[WM_VKEYTOITEM](http://msdn.microsoft.com/library/windows/desktop/bb761364)|**OCM_VKEYTOITEM —**|  
|[WM_CHARTOITEM](http://msdn.microsoft.com/library/windows/desktop/bb761358)|**OCM_CHARTOITEM —**|  
|[WM_COMPAREITEM](http://msdn.microsoft.com/library/windows/desktop/bb775921)|**OCM_COMPAREITEM —**|  
|[WM_HSCROLL](http://msdn.microsoft.com/library/windows/desktop/bb787575)|**OCM_HSCROLL —**|  
|[WM_VSCROLL](http://msdn.microsoft.com/library/windows/desktop/bb787577)|**OCM_VSCROLL —**|  
|[WM_PARENTNOTIFY](https://msdn.microsoft.com/library/ms632638.aspx)|**OCM_PARENTNOTIFY —**|  
|[WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)|**OCM_NOTIFY —**|  
  
> [!NOTE]
>  Jeśli formant jest uruchomiony w systemie Win32, istnieje kilka typów **wm_ctlcolor —\***  wiadomości może zostać wyświetlony. Aby uzyskać więcej informacji, zobacz **WM_CTLCOLORBTN**, **WM_CTLCOLORDLG**, **WM_CTLCOLOREDIT**, **WM_CTLCOLORLISTBOX**,  **WM_CTLCOLORMSGBOX**, **WM_CTLCOLORSCROLLBAR**, **WM_CTLCOLORSTATIC**.  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty MFC ActiveX: Tworzenie podklasy kontrolki okna](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)   
 [TN062: odbicie komunikatu dla kontrolek systemu Windows](../mfc/tn062-message-reflection-for-windows-controls.md)


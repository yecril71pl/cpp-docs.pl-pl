---
title: "Domyślne zdarzenia formantów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Dialog editor, default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls, events
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a8f85e534892cf45987cf563f968ca5e1ec28262
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="default-control-events"></a>Domyślne zdarzenia kontroli
Następujące nazwy formantu ma towarzyszący domyślne zdarzenia:  
  
|Nazwa formantu|Zdarzenie domyślne|  
|------------------|-------------------|  
|Animowanie|**ACN_START**|  
|Pole wyboru|**BN_CLICKED**|  
|Pola kombi|**CBN_SELCHANGE**|  
|Niestandardowe|**TTN_GETDISPINFO**|  
|Wybór daty i godziny|**DTN_DATETIMECHANGE —**|  
|pole edycji|**EN_CHANGE**|  
|Pole grupy|(Nie dotyczy)|  
|Klawisz dostępu|**NM_OUTOFMEMORY —**|  
|Adres IP|**IPN_FIELDCHANGED**|  
|Lista|**LVN_ITEMCHANGE**|  
|pola listy|**LBN_SELCHANGE**|  
|Kalendarza miesięcznego|**MCN_SELCHANGE**|  
|Formant obrazu|(Nie dotyczy)|  
|Postęp|**NM_CUSTOMDRAW**|  
|Przycisk polecenia|**BN_CLICKED**|  
|Przycisk radiowy|**BN_CLICKED**|  
|Edycji wzbogaconej|**EN_CHANGE**|  
|Pasek przewijania|**NM_THEMECHANGED**|  
|Suwak|**NM_CUSTOMDRAW**|  
|Pokrętła|**UDN_DELTAPOS**|  
|Tekst statyczny|(Nie dotyczy)|  
|Tab|**TCN_SELCHANGE**|  
|Drzewo|**TVN_SELCHANGE**|  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](https://msdn.microsoft.com/library/f45fce5x.aspx) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](https://msdn.microsoft.com/library/xbx3z216.aspx). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie zmiennych Członkowskich dla formantów okna dialogowego](../windows/defining-member-variables-for-dialog-controls.md)   
 [Typy komunikatów związane z obiektami interfejsu użytkownika](../mfc/reference/message-types-associated-with-user-interface-objects.md)   
 [Edytowanie programu obsługi wiadomości](../mfc/reference/editing-a-message-handler.md)   
 [Definiowanie obsługi komunikatów dla komunikatów odbitych](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)   
 [Deklarowanie zmiennej opartej na nowej klasie formantów](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)   
 [Zastępowanie funkcji wirtualnych](../ide/overriding-a-virtual-function-visual-cpp.md)


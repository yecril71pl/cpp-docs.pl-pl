---
title: Programy obsługi zdefiniowane przez użytkownika | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.handlers
dev_langs:
- C++
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fdc8c70f7ef9bdd04bf40f408c4e014b3e3faa3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="user-defined-handlers"></a>Programy obsługi zdefiniowane przez użytkownika
Następujące wpisy mapy odpowiadają prototypy funkcji.  
  
|Wpis w mapie|Prototyp funkcji|  
|---------------|------------------------|  
|On_message — ( \<wiadomości >, \<memberFxn >)|afx_msg elementu LRESULT memberFxn (WPARAM, LPARAM);|  
|On_registered_message — ( \<nMessageVariable >, \<memberFxn >)|afx_msg elementu LRESULT memberFxn (WPARAM, LPARAM);|  
|On_thread_message — ( \<wiadomości >, \<memberFxn >)|afx_msg memberFxn void (WPARAM, LPARAM);|  
|On_registered_thread_message — ( \<nMessageVariable >, \<memberFxn >)|afx_msg memberFxn void (WPARAM, LPARAM);|  
  
## <a name="see-also"></a>Zobacz też  
 [Mapy komunikatów](../../mfc/reference/message-maps-mfc.md)   
 [Programy obsługi komunikatów WM_](../../mfc/reference/handlers-for-wm-messages.md)


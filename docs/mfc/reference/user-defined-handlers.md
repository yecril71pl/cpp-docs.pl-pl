---
title: "Programy obsługi zdefiniowane przez użytkownika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.handlers
dev_langs: C++
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dcfc7849aae5b9377365b4dc088fc0ecdd227a83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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


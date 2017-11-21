---
title: "Canceltransitionpolicy — wyliczenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
dev_langs: C++
helpviewer_keywords: CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7f21959daf740155a70787f7c35f8467d1fb2149
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy — Wyliczenie
Wskazuje, jak operację asynchroniczną na próbę przejście do stanu terminali zakończone lub błąd zachowania w przypadku względem klient zażądał stan anulowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum CancelTransitionPolicy;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`RemainCanceled`|Jeśli operacja asynchroniczna jest obecnie w stanie Anulowane klient zażądał, oznacza to, że pozostanie w stanie anulowane w przeciwieństwie do przechodzenia do terminal zakończone lub stanu błędu.|  
|`TransitionFromCanceled`|Jeśli operacja asynchroniczna jest obecnie w stanie Anulowane klient zażądał, wskazuje to, że stan powinien przejść od tego stanu Anulowano terminali stanu ukończone lub błędu, zgodnie z ustaleniami połączenia, który korzysta z tej flagi.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)
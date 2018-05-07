---
title: Wyliczenie platform::CallbackContext | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
dev_langs:
- C++
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 757de5f686bb809a5d2fb159a3ee547a20edc982
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext — wyliczenie
Określa kontekst wątku, w której wykonuje funkcję wywołania zwrotnego (procedura obsługi zdarzeń).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum class CallbackContext {};  
```  
  
### <a name="members"></a>Elementy członkowskie  
  
|Kod typu|Opis|  
|---------------|-----------------|  
|wszystkie|Funkcja wywołania zwrotnego można wykonywać w dowolnym kontekście wątku.|  
|tym samym|Funkcja wywołania zwrotnego można wykonać w kontekście wątku, który uruchomił operację asynchroniczną.|  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd
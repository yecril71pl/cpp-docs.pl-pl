---
title: Wyliczenie platform::CallbackContext | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::CallbackContext
dev_langs: C++
helpviewer_keywords: Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
caps.latest.revision: "3"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ede3cfecadbe87caf5182e0d3df9c25a481f3079
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
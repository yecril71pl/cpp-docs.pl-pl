---
title: Klasa platform::Delegate | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::Delegate
dev_langs: C++
helpviewer_keywords: Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a95dad9833bcf1bebe9d9f74eceb05efcfa8ce0f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="platformdelegate-class"></a>Klasa platform::Delegate
Reprezentuje obiekt funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public delegate void delegate_name();  
```  
  
### <a name="members"></a>Elementy członkowskie  
 Klasa delegata ma metodę Equals, metoda GetHashCode(), ani metody ToString() pochodzi z [Platform::Object klasy](../cppcx/platform-object-class.md).  
  
### <a name="remarks"></a>Uwagi  
 Użyj [delegować](../windows/delegate-cpp-component-extensions.md) — słowo kluczowe do tworzenia delegatów; nie używaj Platform::Delegate jawnie. Aby uzyskać więcej informacji, zobacz [delegatów](../cppcx/delegates-c-cx.md). Na przykład sposobu tworzenia i zużywać delegata zobacz [tworzenia składników środowiska wykonawczego systemu Windows w języku C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md).  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
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
ms.openlocfilehash: 661e96cd2455610e6a7f669928d49c915b7d7575
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
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
 Użyj [delegować](../windows/delegate-cpp-component-extensions.md) — słowo kluczowe do tworzenia delegatów; nie używaj Platform::Delegate jawnie. Aby uzyskać więcej informacji, zobacz [delegatów](../cppcx/delegates-c-cx.md). Na przykład sposobu tworzenia i zużywać delegata zobacz [tworzenia składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
---
title: Klasa platform::Delegate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
dev_langs:
- C++
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 679a868cac536aad541d770433fe1407fc5d08d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33087236"
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
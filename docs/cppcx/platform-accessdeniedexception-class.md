---
title: Klasa platform::AccessDeniedException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::AccessDeniedException
- VCCORLIB/Platform::AccessDeniedException::AccessDeniedException
dev_langs: C++
helpviewer_keywords: Platform::AccessDeniedException
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 87e94e5f0aafabe8d3c8f4cb549a80717cf82742
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="platformaccessdeniedexception-class"></a>Klasa platform::AccessDeniedException
Wyjątek podczas dostępu do zasobów lub funkcji jest zabroniony.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli naciśniesz tego wyjątku, upewnij się, że żądana odpowiednia możliwość i wprowadzone wymagane deklaracji w manifeście pakietu aplikacji. Aby uzyskać więcej informacji, zobacz [COMException](../cppcx/platform-comexception-class.md) klasy.  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa platform::COMException](../cppcx/platform-comexception-class.md)
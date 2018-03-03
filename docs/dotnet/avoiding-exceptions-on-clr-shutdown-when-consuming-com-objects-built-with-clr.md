---
title: "Unikanie wyjątków zgłaszanych przez obiektów COM skompilowanych z - clr | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 287c9831f8c604272b37ac85528d66fe640de557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Unikanie wyjątków przy zamykaniu środowiska CLR w przypadku konsumowania obiektów COM skompilowanych przy użyciu opcji /clr
Gdy środowisko uruchomieniowe języka wspólnego (CLR) wprowadza Tryb zamykania, funkcje natywne mają ograniczony dostęp do usług CLR. Podczas próby wywołać wersji dla obiekt COM skompilowane z **/CLR**, CLR przejścia do kodu natywnego, a następnie przejść z powrotem do kodu zarządzanego do obsługi wywołania IUnknown::Release (który jest zdefiniowany w zarządzanym kodzie). Środowisko CLR zapobiega wywołania do kodu zarządzanego, ponieważ jest w trybie zamykania.  
  
 Aby rozwiązać ten problem, upewnij się, że wywoływana z metod wersji destruktorów zawierać tylko kodu natywnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)
---
title: Domeny aplikacji i programu Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8ddb60b3fad6c230677e2098dd89a723198bea8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="application-domains-and-visual-c"></a>Domeny aplikacji i program Visual C++
Jeśli masz `__clrcall` funkcji wirtualnej vtable będzie dla domeny aplikacji (appdomain). Jeśli obiekt jest tworzony w jednej domenie aplikacji, można wywołać tylko funkcji wirtualnej z wewnątrz tego elementu appdomain. W trybie mieszanym (**/CLR**) ma na proces tablic metod wirtualnych, jeśli nie ma typu `__clrcall` funkcji wirtualnych. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
 Aby uzyskać więcej informacji, zobacz artykuł  
  
-   [appdomain](../cpp/appdomain.md)  
  
-   [__clrcall](../cpp/clrcall.md)  
  
-   [proces](../cpp/process.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)
---
title: Domeny aplikacji i programu Visual C++ | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 57a45bd6f73040623fe90626b1c3896df3258dd8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="application-domains-and-visual-c"></a>Domeny aplikacji i program Visual C++
Jeśli masz `__clrcall` funkcji wirtualnej vtable będzie dla domeny aplikacji (appdomain). Jeśli obiekt jest tworzony w jednej domenie aplikacji, można wywołać tylko funkcji wirtualnej z wewnątrz tego elementu appdomain. Wszystkie funkcje zdefiniowane w **/CLR: pure** Użyj jednostki kompilacji `__clrcall` konwencji wywoływania. W związku z tym wszystkie tablice metod wirtualnych zdefiniowanych w **/CLR: pure** jednostki kompilacji są dla domeny appdomain. W trybie mieszanym (**/CLR**) ma na proces tablic metod wirtualnych, jeśli nie ma typu `__clrcall` funkcji wirtualnych. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
 Aby uzyskać więcej informacji, zobacz  
  
-   [domeny aplikacji](../cpp/appdomain.md)  
  
-   [__clrcall](../cpp/clrcall.md)  
  
-   [Porady: Migracja do/CLR: pure (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [proces](../cpp/process.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)
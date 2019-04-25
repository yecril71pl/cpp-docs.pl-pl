---
title: Domeny aplikacji i program Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
ms.openlocfilehash: 2296654e6935bc40f301226b184cf34f77cb126d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223036"
---
# <a name="application-domains-and-visual-c"></a>Domeny aplikacji i programu Visual C++

Jeśli masz `__clrcall` funkcję wirtualną dla domeny aplikacji (appdomain) będzie vtable. Jeśli obiekt jest tworzony w jednej domenie aplikacji, może wywołać tylko funkcję wirtualną z w ramach tego elementu appdomain. W trybie mieszanym (**/CLR**) będą mieć na proces tablic metod wirtualnych, jeśli nie ma typu `__clrcall` funkcji wirtualnych. **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Aby uzyskać więcej informacji, zobacz:

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [proces](../cpp/process.md)

## <a name="see-also"></a>Zobacz także

- [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)
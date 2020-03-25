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
ms.openlocfilehash: 16c02bb58681ecb241d3552f57e0b05f2d6711b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208808"
---
# <a name="application-domains-and-visual-c"></a>Domeny aplikacji i program Visual C++

Jeśli masz `__clrcall` funkcję wirtualną, będzie ona dla domeny aplikacji (AppDomain). W przypadku utworzenia obiektu w jednej domenie aplikacji można wywołać tylko funkcję wirtualną z poziomu tej domeny aplikacji. W trybie mieszanym ( **/CLR**) będziesz mieć dla poszczególnych procesów tablice metod, jeśli typ nie ma `__clrcall` funkcji wirtualnych. **/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

Aby uzyskać więcej informacji, zobacz:

- [appdomain](../cpp/appdomain.md)

- [__clrcall](../cpp/clrcall.md)

- [proces](../cpp/process.md)

## <a name="see-also"></a>Zobacz też

- [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)

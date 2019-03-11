---
title: Unikanie wyjątków zgłaszanych przez obiektów COM skompilowanych z / clr
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], CLR shutdown exceptions
- /clr compiler option [C++], CLR shutdown exceptions
- mixed assemblies [C++], CLR shutdown exceptions
- /clr compiler option [C++], COM objects
- interoperability [C++], CLR shutdown exceptions
- CLR shutdown exceptions [C++]
ms.assetid: 41249d83-4b51-4e46-866f-27f475f2498c
ms.openlocfilehash: bafcfb4e8a8abfecc8491220202b63971bef1ac8
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749246"
---
# <a name="avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr"></a>Unikanie wyjątków przy zamykaniu środowiska CLR w przypadku konsumowania obiektów COM skompilowanych przy użyciu opcji /clr

Gdy środowisko uruchomieniowe języka wspólnego (CLR) wprowadza Tryb zamykania, funkcje natywne mają ograniczony dostęp do usług CLR. Podczas próby wywołania wersji na obiekt COM skompilowany przy użyciu **/CLR**, CLR przechodzi do kodu natywnego, a następnie przejść z powrotem do kodu zarządzanego do obsługi rozmów IUnknown::Release, (która jest zdefiniowana w kodzie zarządzanym). Środowisko CLR uniemożliwia wywołanie do kodu zarządzanego, ponieważ jest w trybie zamykania.

Aby rozwiązać ten problem, upewnij się, że destruktory wywoływana z metody wydania będzie zawierać tylko kodu natywnego.

## <a name="see-also"></a>Zobacz także

[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)

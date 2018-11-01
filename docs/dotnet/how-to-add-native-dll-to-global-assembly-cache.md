---
title: 'Porady: dodawanie natywnej biblioteki DLL do globalnej pamięci podręcznej zestawów'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
ms.openlocfilehash: 1b11ebfae704ca1529113a00b463df728c85fe60
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641366"
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>Porady: dodawanie natywnej biblioteki DLL do globalnej pamięci podręcznej zestawów

Natywna Biblioteka DLL (nie COM) można umieścić w globalnej pamięci podręcznej zestawów.

## <a name="example"></a>Przykład

**/ ASSEMBLYLINKRESOURCE** umożliwia osadzanie natywnej biblioteki DLL w zestawie.

Aby uzyskać więcej informacji, zobacz [assemblylinkresource (Link do zasobów .NET Framework)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md).

```
/ASSEMBLYLINKRESOURCE:MyComponent.dll
```

## <a name="see-also"></a>Zobacz też

[Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
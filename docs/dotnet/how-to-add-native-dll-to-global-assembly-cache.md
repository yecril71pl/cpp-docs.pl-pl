---
title: 'Porady: Dodawanie natywnej biblioteki DLL do globalnej pamięci podręcznej | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 74b24b96b28d8c5805a075a5ac1eee41173fc427
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431999"
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
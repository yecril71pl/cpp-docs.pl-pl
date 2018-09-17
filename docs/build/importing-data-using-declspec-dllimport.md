---
title: Importowanie danych przy użyciu atrybutu __declspec(dllimport) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a024d7488eb1683f40548839ab843da1e56f65e8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710219"
---
# <a name="importing-data-using-declspecdllimport"></a>Importowanie danych przy użyciu atrybutu __declspec(dllimport)

W przypadku danych za pomocą **__declspec(dllimport)** element wygody, który usuwa warstwę pośredniego. Podczas importowania danych z biblioteki DLL, nadal musiał przejść za pomocą tabeli adresów importowania. Przed **__declspec(dllimport)**, oznacza to pamiętać o postępowaniu dodatkowy poziom pośredni, uzyskiwanie dostępu do danych wyeksportowane z biblioteki DLL:

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

Następnie będzie wyeksportować dane w sieci. Plik DEF:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

i uzyskać do niego dostęp poza bibliotekę DLL:

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

Po oznaczeniu danych jako **__declspec(dllimport)**, kompilator automatycznie generuje kod pośredni dla Ciebie. Nie musisz już martwić się o powyższych kroków. Jak wspomniano wcześniej, nie używaj **__declspec(dllimport)** deklaracji danych podczas tworzenia biblioteki DLL. Funkcje w ramach biblioteki DLL nie należy używać tabeli adresów importowania do dostępu do obiektu danych; w związku z tym nie masz dodatkowy poziom pośredni obecne.

Aby wyeksportować dane automatycznie z biblioteki DLL, należy użyć tej deklaracji:

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>Zobacz też

[Importowanie do aplikacji](../build/importing-into-an-application.md)
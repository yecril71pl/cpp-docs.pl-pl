---
title: Importowanie danych przy użyciu atrybutu __declspec(dllimport)
description: Jak używać __declspec (dllimport) do importowania danych biblioteki DLL.
ms.date: 09/03/2020
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: cb9850306d6e73b88e2926a6f068ae21f8d32530
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609118"
---
# <a name="importing-data-using-__declspecdllimport"></a>Importowanie danych przy użyciu `__declspec(dllimport)`

W przypadku danych korzystanie z programu **`__declspec(dllimport)`** to wygodne elementy, które usuwają warstwę operatora pośredniego. W przypadku importowania danych z biblioteki DLL nadal trzeba przejść przez tabelę adresów importu. Wcześniej **`__declspec(dllimport)`** należało pamiętać o przepełnieniu dodatkowego poziomu pośredniego podczas uzyskiwania dostępu do danych wyeksportowanych z biblioteki dll:

```C
// project.h
// Define PROJECT_EXPORTS when building your DLL
#ifdef PROJECT_EXPORTS   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

Następnie można wyeksportować dane z programu. Plik DEF:

```DEF
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

i uzyskać do niego dostęp poza biblioteką DLL:

```C
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

Po oznaczeniu danych jako **`__declspec(dllimport)`** , kompilator automatycznie generuje kod pośredni. Nie musisz już martwić się o powyższe kroki. Jak wspomniano wcześniej, nie należy używać **`__declspec(dllimport)`** deklaracji danych podczas kompilowania biblioteki DLL. Funkcje w bibliotece DLL nie używają tabeli adresów importu do uzyskiwania dostępu do obiektu danych. w związku z tym nie będziesz mieć dodatkowego poziomu pośredniego.

Aby wyeksportować dane automatycznie z biblioteki DLL, Użyj tej deklaracji:

```C
// project.h
// Define PROJECT_EXPORTS when building your DLL
#ifdef PROJECT_EXPORTS   // If accessing the data from inside the DLL
   __declspec(dllexport) ULONG ulDataInDLL;

#else         // If accessing the data from outside the DLL
   __declspec(dllimport) ULONG ulDataInDLL;
#endif
```

## <a name="see-also"></a>Zobacz też

[Importowanie do aplikacji](importing-into-an-application.md)

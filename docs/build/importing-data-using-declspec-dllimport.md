---
title: Importowanie danych przy użyciu atrybutu __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: 341912b53301c3a11df4285167d66c8c1493d2fd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223996"
---
# <a name="importing-data-using-__declspecdllimport"></a>Importowanie danych przy użyciu atrybutu __declspec(dllimport)

W przypadku danych korzystanie z programu **`__declspec(dllimport)`** to wygodne elementy, które usuwają warstwę operatora pośredniego. W przypadku importowania danych z biblioteki DLL nadal trzeba przejść przez tabelę adresów importu. Wcześniej **`__declspec(dllimport)`** należało pamiętać o przepełnieniu dodatkowego poziomu pośredniego podczas uzyskiwania dostępu do danych wyeksportowanych z biblioteki dll:

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

Następnie można wyeksportować dane z programu. Plik DEF:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

i uzyskać do niego dostęp poza biblioteką DLL:

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

Po oznaczeniu danych jako **`__declspec(dllimport)`** , kompilator automatycznie generuje kod pośredni. Nie musisz już martwić się o powyższe kroki. Jak wspomniano wcześniej, nie należy używać **`__declspec(dllimport)`** deklaracji danych podczas kompilowania biblioteki DLL. Funkcje w bibliotece DLL nie używają tabeli adresów importu do uzyskiwania dostępu do obiektu danych. w związku z tym nie będziesz mieć dodatkowego poziomu pośredniego.

Aby wyeksportować dane automatycznie z biblioteki DLL, Użyj tej deklaracji:

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>Zobacz także

[Importowanie do aplikacji](importing-into-an-application.md)

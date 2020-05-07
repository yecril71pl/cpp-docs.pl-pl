---
title: Importowanie danych przy użyciu atrybutu __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: c9dce798572a91bcb9721f022393abb669970131
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440447"
---
# <a name="importing-data-using-__declspecdllimport"></a>Importowanie danych przy użyciu atrybutu __declspec(dllimport)

W przypadku danych korzystanie z **__declspec (dllimport)** to wygodne elementy, które usuwają warstwę operatora pośredniego. W przypadku importowania danych z biblioteki DLL nadal trzeba przejść przez tabelę adresów importu. Przed **__declspec (dllimport)**, należy pamiętać o przepełnieniu dodatkowego poziomu pośredniego podczas uzyskiwania dostępu do danych wyeksportowanych z biblioteki dll:

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

Gdy oznaczesz dane jako **__declspec (dllimport)**, kompilator automatycznie generuje kod pośredni. Nie musisz już martwić się o powyższe kroki. Jak wspomniano wcześniej, nie należy używać deklaracji **__declspec (dllimport)** dla danych podczas KOMPILOWANIA biblioteki DLL. Funkcje w bibliotece DLL nie używają tabeli adresów importu do uzyskiwania dostępu do obiektu danych. w związku z tym nie będziesz mieć dodatkowego poziomu pośredniego.

Aby wyeksportować dane automatycznie z biblioteki DLL, Użyj tej deklaracji:

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>Zobacz też

[Importowanie do aplikacji](importing-into-an-application.md)

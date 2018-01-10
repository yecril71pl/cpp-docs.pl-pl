---
title: "Błąd narzędzi konsolidatora LNK1561 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1561
dev_langs: C++
helpviewer_keywords: LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cbd0ca9e932bdb2845ada2f47b569391e943cb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1561"></a>Błąd narzędzi konsolidatora LNK1561
punkt wejścia musi być zdefiniowana  
  
Nie znaleziono konsolidator *punktu wejścia*, początkowej funkcji do wywołania w pliku wykonywalnego. Domyślnie wyszukuje konsolidator `main` lub `wmain` funkcji aplikacji konsoli, `WinMain` lub `wWinMain` funkcji aplikacji systemu Windows lub `DllMain` dla biblioteki DLL, która wymaga inicjowania. Można określić inną funkcję za pomocą [/Entry](../../build/reference/entry-entry-point-symbol.md) — opcja konsolidatora.  
  
Ten błąd może mieć kilka przyczyn:  
-   Może nie dołączono pliku, który definiuje na liście plików do łączenia punktu wejścia. Upewnij się, że plik zawierający funkcję punktu wejścia jest połączony w swojej aplikacji.  
-   Definicja punktu wejścia przy użyciu sygnatury funkcji niewłaściwy; na przykład możesz mieć zawiera błąd pisowni lub używany nieprawidłowy przypadek dla nazwy funkcji lub niepoprawnie określony zwracany typ lub typy parametrów.  
-   Nie określono [/dll](../../build/reference/dll-build-a-dll.md) podczas tworzenia biblioteki DLL.  
-   Określono nazwę funkcję punktu wejścia niepoprawnie przypadku użycia [/Entry](../../build/reference/entry-entry-point-symbol.md) — opcja konsolidatora.  
-   Jeśli używasz [LIB](../../build/reference/lib-reference.md) narzędzie do tworzenia biblioteki DLL, określony plik .def. Jeśli tak, usuń plik .def z kompilacji.    
  
Podczas tworzenia aplikacji, konsolidator szuka funkcję punktu wejścia do wywołania, aby uruchomić kod. Jest to funkcja, która jest wywoływana po załadowaniu aplikacji i środowiska wykonawczego został zainicjowany. Należy podać funkcję punktu wejścia dla aplikacji lub nie można uruchomić aplikacji. Punkt wejścia jest opcjonalne dla biblioteki DLL. Wyszukuje domyślnie przez funkcję punktu wejścia o jednym z kilku konkretne nazwy i podpisy, takich jak konsolidator `int main(int, char**)`. Można określić inną nazwę funkcji jako wpis punktu, przy użyciu opcji konsolidatora/Entry.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje LNK1561:  
  
```cpp  
// LNK1561.cpp  
// LNK1561 expected  
int i;  
// add a main function to resolve this error  
```
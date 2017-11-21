---
title: "Definicji modułu (. Pliki DEF) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 15dbdfcd1074b32e2a707616571484db3ced9d2a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="module-definition-def-files"></a>Pliki definicji modułu (.Def)
Pliki definicji modułu (.def) podaj konsolidatora z informacjami o eksportu, atrybutów i innych informacji o programie być połączony. Plik .def jest najbardziej przydatna podczas tworzenia biblioteki DLL. Ponieważ istnieją [opcje konsolidatora](../../build/reference/linker-options.md) którego można użyć zamiast instrukcji definicji modułu .def — pliki nie są zazwyczaj konieczne. Można również użyć [__declspec(dllexport)](../../build/exporting-from-a-dll-using-declspec-dllexport.md) jako sposobu na określenie wyeksportowanych funkcji.  
  
 Plik .def może wywołać w fazie konsolidatora z [/DEF (Określ plik definicji modułu)](../../build/reference/def-specify-module-definition-file.md) — opcja konsolidatora.  
  
 Jeśli tworzysz plik .exe, który zawiera żadnego eksportu przy użyciu pliku .def spowoduje, że ładowanie z danych wyjściowych w pliku większych i wolniej.  
  
 Na przykład zobacz [eksportowanie z biblioteki DLL przy użyciu DEF, pliki](../../build/exporting-from-a-dll-using-def-files.md).  
  
 Znajduje się w następujących sekcjach, aby uzyskać więcej informacji:  
  
-   [Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)  
  
-   [EKSPORTY](../../build/reference/exports.md)  
  
-   [HEAPSIZE](../../build/reference/heapsize.md)  
  
-   [BIBLIOTEKA](../../build/reference/library.md)  
  
-   [NAZWA](../../build/reference/name-c-cpp.md)  
  
-   [SEKCJE](../../build/reference/sections-c-cpp.md)  
  
-   [STACKSIZE](../../build/reference/stacksize.md)  
  
-   [STUB](../../build/reference/stub.md)  
  
-   [WERSJA](../../build/reference/version-c-cpp.md)  
  
-   [Słowa zastrzeżone](../../build/reference/reserved-words.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie kompilacji C/C++](../../build/reference/c-cpp-building-reference.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)  
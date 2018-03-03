---
title: "Błąd narzędzi konsolidatora LNK2022 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2022
dev_langs:
- C++
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ca45ed3cd83a3fc81a6dad8fdcec5aee3232c6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2022"></a>Błąd narzędzi konsolidatora LNK2022  
  
> Operacja metadanych nie powiodła się (*HRESULT*): *error_message*  
  
Konsolidator wykrył błąd podczas scalania metadanych. Aby połączyć się pomyślnie, należy usunąć błędy metadanych.  
  
Jednym ze sposobów zdiagnozować problem jest uruchomienie **narzędzia ildasm-tokenów** w plikach obiektu można znaleźć typy, które mają tokenów na liście `error_message`i poszukaj różnice.  W metadanych dwa różne typy o takiej samej nazwie jest nieprawidłowy, nawet jeśli różni się tylko atrybut LayoutType.  
  
Jeden przyczyny dotyczące LNK2022 jest typu (na przykład struktury) istnieje w wielu jednostki kompilacji o takiej samej nazwie, ale z definicje powodujące konflikt, a podczas kompilowania z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  W takim przypadku upewnij się, że typ ma identyczne definicję w wszystkie jednostki kompilacji.  Nazwa typu jest na liście `error_message`.  
  
Inną możliwą przyczyną LNK2022 jest Jeśli konsolidator znajdzie plik metadanych w innej lokalizacji niż określono w kompilatorze (z [#using](../../preprocessor/hash-using-directive-cpp.md) ). Upewnij się, że jego pliku metadanych (.dll lub moduł .netmodule) jest w tej samej lokalizacji, gdy dane są przekazywane do konsolidatora, jak w momencie został przekazany do kompilatora.  
  
Podczas tworzenia aplikacji ATL, użyj makra `_ATL_MIXED` jest wymagany w wszystkie jednostki kompilacji, jeśli jest on używany w co najmniej jednym.  
  
## <a name="example"></a>Przykład  
  
Poniższy przykład definiuje typ puste.  
  
```cpp  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## <a name="example"></a>Przykład  
  
W tym przykładzie pokazano, że nie można połączyć dwóch plików kodu źródłowego, które zawierają typy o tej samej nazwie, ale różne definicje.  
  
Poniższy przykład generuje LNK2022.  
  
```cpp  
// LNK2022_b.cpp  
// compile with: LNK2022_a.cpp /clr /LD   
// LNK2022 expected  
public ref class Test {  
   void func() {}  
   int var;  
};  
```
---
title: Błąd kompilatora C2857 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49e94e12b4cdf07d9f7fe74dd481bbc032a937eb
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601382"
---
# <a name="compiler-error-c2857"></a>Błąd kompilatora C2857

> "#include" instrukcja określona z parametrem/yc*filename* opcji wiersza polecenia nie został znaleziony w pliku źródłowym

[/Yc](../../build/reference/yc-create-precompiled-header-file.md) opcja określa nazwę pliku dołączonego, który nie znajduje się w pliku źródłowym jest kompilowane.

## <a name="remarks"></a>Uwagi

Kiedy używać **/Yc**<em>filename</em> opcję w pliku źródłowym, aby utworzyć plik prekompilowanego nagłówka (PCH), który plik źródłowy musi zawierać *filename* pliku nagłówka. Każdy plik dołączony przez plik źródłowy, w tym określonym *filename*, znajdują się w pliku PCH. W innych plikach źródłowych skompilowane przy użyciu **/Yu**<em>filename</em> opcję, aby użyć PCH pliku dołączania z *filename* musi być pierwszy wiersz komentarza-w pliku. Kompilator ignoruje niczego w pliku źródłowym przed to między innymi.

Ten błąd może być spowodowany przez `#include "filename"` instrukcji w bloku kompilacji warunkowej, która nie jest kompilowana w pliku źródłowym PCH.

## <a name="example"></a>Przykład

W typowych użycia jednego pliku źródłowego w projekcie jest wyznaczony jako plik źródłowy PCH i jeden plik nagłówkowy jest używany jako plik nagłówkowy PCH. Typowy plik nagłówkowy PCH ma wszystkie nagłówki biblioteki używane w projekcie, ale nie lokalnego nagłówki, które są nadal w fazie projektowania. W tym przykładzie plik nagłówkowy PCH o nazwie *my_pch.h*.

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

Plik źródłowy PCH jest kompilowany przy użyciu **/Yc**<em>my_pch.h</em> opcji. Jeśli kompilator nie może znaleźć pliku dołączania ten plik nagłówkowy PCH, generuje C2857:

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

Aby użyć tego pliku PCH, pliki źródłowe muszą być skompilowane przy użyciu **/Yu**<em>my_pch.h</em> opcji. Plik nagłówkowy PCH musi być uwzględniony w najpierw w plikach źródłowych, które używają PCH:

```cpp
// C2857.cpp
// Compile my_pch.cpp first, then
// compile by using: cl /EHsc /W4 /Yumy_pch.h my_project.cpp my_pch.obj
// Include the pch header before any other non-comment line
#include "my_pch.h"

int main()
{
    puts("Using a precompiled header file.\n");
}
```
---
title: Błąd kompilatora C2857
ms.date: 09/13/2018
f1_keywords:
- C2857
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
ms.openlocfilehash: 11b620f9748ac85e731d79b0652c0392375b2ea4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201854"
---
# <a name="compiler-error-c2857"></a>Błąd kompilatora C2857

> w pliku źródłowym nie znaleziono instrukcji "#include" określonej przy użyciu opcji wiersza polecenia/YC*filename*

Opcja [/YC](../../build/reference/yc-create-precompiled-header-file.md) określa nazwę pliku dołączanego, który nie jest uwzględniony w kompilowanym pliku źródłowym.

## <a name="remarks"></a>Uwagi

W przypadku użycia opcji **/YC**<em>filename</em> w pliku źródłowym do utworzenia prekompilowanego pliku nagłówkowego (pch) ten plik źródłowy musi zawierać plik nagłówkowy *filename* . Każdy plik zawarty w pliku źródłowym, włącznie z określoną *nazwą pliku*, znajduje się w pliku PCH. W innych plikach źródłowych skompilowanych przy użyciu opcji **/Yu**<em>filename</em> do użycia pliku PCH, dołączenie *nazwy* pliku musi być pierwszym wierszem niebędącym komentarzem w pliku. Kompilator ignoruje wszystkie elementy w pliku źródłowym przed dołączeniem.

Ten błąd może być spowodowany przez instrukcję `#include "filename"` w bloku kompilacji warunkowej, który nie jest kompilowany w pliku źródłowym PCH.

## <a name="example"></a>Przykład

W typowym użyciu jeden plik źródłowy w projekcie jest wyznaczeni jako plik źródłowy PCH i jeden plik nagłówka jest używany jako plik nagłówka PCH. Typowy plik nagłówka PCH ma wszystkie nagłówki biblioteki używane w projekcie, ale nie nagłówki lokalne, które są nadal w fazie projektowania. W tym przykładzie plik nagłówka PCH ma nazwę *my_pch. h*.

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

Plik źródłowy PCH jest kompilowany przy użyciu opcji **/Yc**<em>my_pch. h</em> . Jeśli kompilator nie znajdzie dołączonego pliku nagłówkowego PCH, generuje C2857:

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

Aby można było użyć tego pliku PCH, pliki źródłowe muszą być kompilowane przy użyciu opcji **/Yu**<em>my_pch. h</em> . Plik nagłówkowy PCH musi być umieszczony najpierw w plikach źródłowych, które używają PCH:

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

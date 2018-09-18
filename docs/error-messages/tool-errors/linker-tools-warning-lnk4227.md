---
title: Ostrzeżenie LNK4227 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4227
dev_langs:
- C++
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28bcf242e48046278030ec4259b7ae3edd1c4a61
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088868"
---
# <a name="linker-tools-warning-lnk4227"></a>Ostrzeżenie LNK4227 narzędzi konsolidatora

> Ostrzeżenie dla operacji na metadanych (*HRESULT*): *warning_message*

Konsolidator Wykryto różnice metadanych podczas scalania:

- Co najmniej jeden zestawach z zestawem aktualnie kompilowana.

- Jeden lub więcej plików kodu źródłowego w kompilacji.

Na przykład może być spowodowany LNK4227 Jeśli masz dwie funkcje globalne o takiej samej nazwie, ale informacje o parametrach, zadeklarowany w inny sposób (czyli deklaracje nie są spójne z wszystkich compilands). Użyj ildasm.exe/Text /METADATA *object_file* w każdym pliku .obj, aby zobaczyć, jak typy różnią się.

LNK4227 służy także do raportów dotyczących problemów, które pochodzą z innego narzędzia. Wyszukiwanie z komunikatem ostrzegawczym, aby uzyskać więcej informacji.

Rozwiąż ostrzeżenia musi mieć stałą problemów metadanych.

## <a name="example"></a>Przykład

LNK4227 jest generowany, gdy przywoływany zestaw został podpisany inaczej niż zestaw, który odwołuje się do niej.

Poniższy przykład spowoduje wygenerowanie LNK4227:

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

Następnie wyszukaj maszynę

```cpp
// LNK4227b.cpp
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe
using namespace System::Reflection;
using namespace System::Runtime::CompilerServices;

[assembly:AssemblyDelaySignAttribute(true)];
// Try the following line instead
// [assembly:AssemblyDelaySignAttribute(false)];

ref class MyClass
{
};
```

## <a name="example"></a>Przykład

LNK4227 również mogą być generowane, gdy numery wersji w nieprawidłowym formacie są przekazywane do zestawu atrybutów.  "*" Dotyczy notacji `AssemblyVersionAttribute`.  Aby rozwiązać to ostrzeżenie, użyj tylko liczby w atrybutach w wersji innej niż `AssemblyVersionAttribute`.

Poniższy przykład spowoduje wygenerowanie LNK4227:

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```
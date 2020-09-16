---
title: Ostrzeżenie LNK4227 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4227
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
ms.openlocfilehash: 7ac3ef2b6ad8f05a454dafe5e6a7ea0abc07a066
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685492"
---
# <a name="linker-tools-warning-lnk4227"></a>Ostrzeżenie LNK4227 narzędzi konsolidatora

> Ostrzeżenie o operacji metadanych (*HRESULT*): *warning_message*

Konsolidator wykrył różnice w metadanych podczas scalania:

- Co najmniej jeden zestaw, do którego się odwołuje, jest obecnie kompilowany.

- Jeden lub więcej plików kodu źródłowego w kompilacji.

Na przykład LNK4227 narzędzi KONSOLIDATORA może być spowodowany tym, że istnieją dwie funkcje globalne o tej samej nazwie, ale informacje o parametrach zadeklarowane inaczej (to oznacza, że deklaracje nie są spójne we wszystkich compilands). Użyj ildasm.exe/TEXT/METADATA *object_file* w każdym pliku. obj, aby zobaczyć, jak różnią się typy.

LNK4227 narzędzi KONSOLIDATORA jest również używany do zgłaszania problemów, które pochodzą z innego narzędzia. Wyszukaj komunikat ostrzegawczy, aby uzyskać więcej informacji.

Aby rozwiązać ten problem, należy naprawić problemy dotyczące metadanych.

## <a name="examples"></a>Przykłady

LNK4227 narzędzi KONSOLIDATORA jest generowany, gdy przywoływany zestaw został podpisany inaczej niż zestaw, który odwołuje się do niego.

Poniższy przykład generuje LNK4227 narzędzi KONSOLIDATORA:

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

a następnie

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

LNK4227 narzędzi KONSOLIDATORA można również generować, gdy numery wersji w niewłaściwym formacie są przesyłane do atrybutów zestawu.  Notacja "*" jest specyficzna dla `AssemblyVersionAttribute` .  Aby rozwiązać ten problem, użyj tylko cyfr w atrybutach wersji innych niż `AssemblyVersionAttribute` .

Poniższy przykład generuje LNK4227 narzędzi KONSOLIDATORA:

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```

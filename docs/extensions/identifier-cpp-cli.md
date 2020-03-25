---
title: __identifier (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
ms.openlocfilehash: 0da32aae9a8c2c7f21ee9576e1e1147822314a36
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172181"
---
# <a name="__identifier-ccli"></a>__identifier (C++/CLI)

Umożliwia używanie C++ słów kluczowych jako identyfikatorów.

## <a name="all-platforms"></a>Wszystkie platformy

### <a name="syntax"></a>Składnia

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>Uwagi

Użycie słowa kluczowego **__identifier** dla identyfikatorów, które nie są słowami kluczowymi jest dozwolone, ale zdecydowanie odradza się jako kwestia stylu.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

### <a name="examples"></a>Przykłady

**Przykład**

W poniższym przykładzie Klasa o nazwie **Template** jest tworzona w C# i dystrybuowana jako biblioteka DLL. W programie C++/CLI, który używa klasy **szablonu** , słowo kluczowe **__identifier** ukrywa fakt, że **szablon** jest standardowym C++ słowem kluczowym.

```csharp
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /ZW
#using <identifier_template.dll>
int main() {
   __identifier(template)^ pTemplate = ref new __identifier(template)();
   pTemplate->Run();
}
```

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="remarks"></a>Uwagi

Słowo kluczowe **__identifier** jest prawidłowe z opcją kompilatora `/clr`.

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

W poniższym przykładzie Klasa o nazwie **Template** jest tworzona w C# i dystrybuowana jako biblioteka DLL. W programie C++/CLI, który używa klasy **szablonu** , słowo kluczowe **__identifier** ukrywa fakt, że **szablon** jest standardowym C++ słowem kluczowym.

```csharp
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /clr
#using <identifier_template.dll>

int main() {
   __identifier(template) ^pTemplate = gcnew __identifier(template)();
   pTemplate->Run();
}
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)<br/>
[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)

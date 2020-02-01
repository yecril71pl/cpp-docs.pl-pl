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
ms.openlocfilehash: 395f1443f4eef16d9eea44c23a6e3288daf03d14
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912838"
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

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)<br/>
[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)
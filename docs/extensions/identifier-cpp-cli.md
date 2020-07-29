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
ms.openlocfilehash: 5f95e9fc55acd33705b855c7c4f0ef268d4776a0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219693"
---
# <a name="__identifier-ccli"></a>__identifier (C++/CLI)

Umożliwia korzystanie z słów kluczowych języka C++ jako identyfikatorów.

## <a name="all-platforms"></a>Wszystkie platformy

### <a name="syntax"></a>Składnia

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>Uwagi

Użycie słowa kluczowego **__identifier** dla identyfikatorów, które nie są słowami kluczowymi jest dozwolone, ale zdecydowanie odradza się jako kwestia stylu.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

### <a name="examples"></a>Przykłady

**Przykład**

W poniższym przykładzie Klasa o nazwie `template` jest tworzona w języku C# i dystrybuowana jako biblioteka DLL. W programie C++/CLI, który używa `template` klasy, **`__identifier`** słowo kluczowe ukrywa fakt, że `template` jest standardowym słowem kluczowym języka C++.

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

Słowo kluczowe **__identifier** jest prawidłowe z `/clr` opcją kompilatora.

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

### <a name="examples"></a>Przykłady

W poniższym przykładzie Klasa o nazwie `template` jest tworzona w języku C# i dystrybuowana jako biblioteka DLL. W programie C++/CLI, który używa `template` klasy, **`__identifier`** słowo kluczowe ukrywa fakt, że `template` jest standardowym słowem kluczowym języka C++.

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

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)<br/>
[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)

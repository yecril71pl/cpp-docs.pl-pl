---
title: __identifier (c + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
dev_langs:
- C++
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 572767c2f85b07f201bef93578b14b731aa467e0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415021"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)

Umożliwia korzystanie z Visual C++ słów kluczowych jako identyfikatorów.

## <a name="all-platforms"></a>Wszystkie platformy

### <a name="syntax"></a>Składnia

```cpp
__identifier(
Visual_C++_keyword
)  
```

### <a name="remarks"></a>Uwagi

Korzystanie z **__identifier** — słowo kluczowe dla identyfikatorów, które nie są słowami kluczowymi jest dozwolone, ale zdecydowanie niezalecane jako stylu.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

### <a name="examples"></a>Przykłady

**Przykład**

W poniższym przykładzie klasę o nazwie **szablonu** jest tworzone w języku C# i dystrybuowanych jako biblioteki DLL. W programie Visual C++, który używa **szablonu** klasy **__identifier** — słowo kluczowe zawiera fakt, **szablonu** jest standardowa słowa kluczowego języka C++.

```cs
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

**__Identifier** — słowo kluczowe jest prawidłowa w przypadku `/clr` — opcja kompilatora.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

W poniższym przykładzie klasę o nazwie **szablonu** jest tworzone w języku C# i dystrybuowanych jako biblioteki DLL. W programie Visual C++, który używa **szablonu** klasy **__identifier** — słowo kluczowe zawiera fakt, **szablonu** jest standardowa słowa kluczowego języka C++.

```cs
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

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)<br/>
[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)
---
title: override (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6071cef3d5669fda86975bb0f27a2b9b87eeb011
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407273"
---
# <a name="override--c-component-extensions"></a>override (C++ Component Extensions)

**Zastąpienia** kontekstowe słowo kluczowe wskazuje, że składowej typu zastępuje klasy bazowej lub składowej interfejsu podstawowego.

## <a name="remarks"></a>Uwagi

**Zastąpienia** — słowo kluczowe jest prawidłowy, podczas kompilowania dla natywnych obiektów docelowych (opcja kompilatora domyślna), elementy docelowe środowisko uruchomieniowe Windows (`/ZW` — opcja kompilatora), lub obiektów docelowych środowiska uruchomieniowego języka wspólnego (`/clr` — opcja kompilatora).

Aby uzyskać więcej informacji na temat nadpisania specyfikatorów, zobacz [specyfikator override](../cpp/override-specifier.md) i [zastąpienie specyfikatorów i kompilacji macierzystych](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Aby uzyskać więcej informacji na temat kontekstowych słów kluczowych, zobacz [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md).

## <a name="examples"></a>Przykłady

Poniższy przykład kodu pokazuje, że **zastąpienia** może również służyć w kompilacjach kodu natywnego.

```cpp
// override_keyword_1.cpp
// compile with: /c
struct I1 {
   virtual void f();
};

struct X : public I1 {
   virtual void f() override {}
};
```

### <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, że **zastąpienia** mogą być używane w kompilacjach środowiska wykonawczego Windows.

```cpp 
// override_keyword_2.cpp
// compile with: /ZW /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

### <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, że **zastąpienia** mogą być używane w typowych kompilacje środowiska uruchomieniowego języka.

```cpp
// override_keyword_3.cpp
// compile with: /clr /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

## <a name="see-also"></a>Zobacz też

[override, specyfikator](../cpp/override-specifier.md)<br/>
[Specyfikatory przesłonięć](../windows/override-specifiers-cpp-component-extensions.md)
---
title: override (C++/CLI i C++/CX)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
ms.openlocfilehash: 32c825539efe670528eab7416afefe07d4cb1b6c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172103"
---
# <a name="override--ccli-and-ccx"></a>override (C++/CLI i C++/CX)

**Przesłonięcie** kontekstowego słowa kluczowego wskazuje, że element członkowski typu zastępuje klasę bazową lub składową interfejsu podstawowego.

## <a name="remarks"></a>Uwagi

Słowo kluczowe **override** jest prawidłowe w przypadku kompilowania natywnych obiektów docelowych (opcja domyślnego kompilatora), środowisko wykonawcze systemu Windows targets (opcja kompilatora`/ZW`) lub obiektów docelowych środowiska uruchomieniowego języka wspólnego (opcja kompilatora`/clr`).

Aby uzyskać więcej informacji na temat specyfikatorów przesłonięcia, zobacz specyfikator [override](../cpp/override-specifier.md) i specyfikatory przesłonięcia [oraz kompilacje natywne](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Aby uzyskać więcej informacji na temat kontekstowych słów kluczowych, zobacz [kontekstowe słowa kluczowe](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="examples"></a>Przykłady

Poniższy przykład kodu pokazuje, że **przesłonięcie** może być również używane w kompilacjach natywnych.

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

Poniższy przykład kodu pokazuje, że **przesłonięcie** może być używane w kompilacjach środowisko wykonawcze systemu Windows.

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

Opcja kompilatora: `/ZW`

### <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, że **zastąpienie** może być używane w kompilacjach środowiska uruchomieniowego języka wspólnego.

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

Opcja kompilatora: `/clr`

## <a name="see-also"></a>Zobacz też

[override, specyfikator](../cpp/override-specifier.md)<br/>
[Specyfikatory zastąpienia](override-specifiers-cpp-component-extensions.md)

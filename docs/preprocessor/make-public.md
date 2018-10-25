---
title: make_public | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eeabbfac65e67e0a293f4c31ff6f8911cc0b676e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066724"
---
# <a name="makepublic"></a>make_public
Wskazuje, że typ macierzysty powinien mieć publicznego zestawu dostępności.

## <a name="syntax"></a>Składnia

```
#pragma make_public(type)
```

### <a name="parameters"></a>Parametry

*Typ* jest nazwa typu, o których chcesz mieć publicznego zestawu dostępności.

## <a name="remarks"></a>Uwagi

**make_public** jest przydatne w przypadku, gdy typ macierzysty, którego chcesz się odwołać pochodzą z pliku .h, którego nie można zmienić. Za pomocą typu natywnego w sygnaturze funkcji publicznych w typie widoczność publiczny zestaw, typ natywny musi również mieć publicznego zestawu dostępności lub kompilator zgłosi ostrzeżenie.

**make_public** musi być określona w zakresie globalnym i działa tylko wtedy, od punktu, w których jest zadeklarowany za pomocą na końcu pliku kodu źródłowego.

Typ natywny może być jawnie lub niejawnie prywatny; zobacz [widoczność typów](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) Aby uzyskać więcej informacji.

## <a name="examples"></a>Przykłady

Poniższy przykład jest zawartość pliku .h, która zawiera definicje dla dwóch struktur natywnych.

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

Poniższy przykład kodu wykorzystuje plik nagłówkowy i pokazuje, że o ile użytkownik wyraźnie oznaczyć natywnej struktury jako publiczne, za pomocą **make_public**, kompilator wygeneruje ostrzeżenie, gdy próba użycia natywnej struktury w Podpis funkcji publicznych w publicznego typu zarządzanego.

```cpp
// make_public_pragma.cpp
// compile with: /c /clr /W1
#pragma warning (default : 4692)
#include "make_public_pragma.h"
#pragma make_public(Native_Struct_1)

public ref struct A {
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692
};
```

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
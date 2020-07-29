---
title: Operator __uuidof
ms.date: 10/10/2018
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
- __uuidof
- _uuidof
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
ms.openlocfilehash: f7564270408d14f58d1528c1f41c0afd2dbe219c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226974"
---
# <a name="__uuidof-operator"></a>`__uuidof`, operator

**Specyficzne dla firmy Microsoft**

Pobiera identyfikator GUID dołączony do wyrażenia.

## <a name="syntax"></a>Składnia

> **`__uuidof (`***wyrażenie***`)`**

## <a name="remarks"></a>Uwagi

*Wyrażenie* może być nazwą typu, wskaźnikiem, odwołaniem lub tablicą tego typu, szablonem wyspecjalizowanym dla tych typów lub zmienną tych typów. Argument jest prawidłowy, o ile kompilator może go użyć, aby znaleźć dołączony identyfikator GUID.

Szczególnym przypadkiem tego wewnętrznego jest podano wartość **0** lub null jako argument. W tym przypadku zwróci **`__uuidof`** Identyfikator GUID składający się z zer.

Użyj tego słowa kluczowego, aby wyodrębnić identyfikator GUID dołączony do:

- Obiekt przez [`uuid`](../cpp/uuid-cpp.md) rozszerzony atrybut.

- Blok biblioteki utworzony przy użyciu [`module`](../windows/attributes/module-cpp.md) atrybutu.

> [!NOTE]
> W kompilacji debugowania **`__uuidof`** zawsze inicjuje obiekt dynamicznie (w czasie wykonywania). W kompilacji wydania **`__uuidof`** można statycznie (w czasie kompilacji) zainicjować obiekt.

W celu zapewnienia zgodności z poprzednimi wersjami, **`_uuidof`** jest synonimem, **`__uuidof`** Jeśli opcja kompilatora [ `/Za` \( disable rozszerzenia języka](../build/reference/za-ze-disable-language-extensions.md) nie jest określona.

## <a name="example"></a>Przykład

Poniższy kod (skompilowany za pomocą ole32. lib) będzie wyświetlał identyfikator UUID bloku biblioteki utworzonego za pomocą atrybutu modułu:

```cpp
// expre_uuidof.cpp
// compile with: ole32.lib
#include "stdio.h"
#include "windows.h"

[emitidl];
[module(name="MyLib")];
[export]
struct stuff {
   int i;
};

int main() {
   LPOLESTR lpolestr;
   StringFromCLSID(__uuidof(MyLib), &lpolestr);
   wprintf_s(L"%s", lpolestr);
   CoTaskMemFree(lpolestr);
}
```

## <a name="comments"></a>Komentarze

W przypadkach, gdy nazwa biblioteki nie jest już w zakresie, można użyć `__LIBID_` zamiast **`__uuidof`** . Na przykład:

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)

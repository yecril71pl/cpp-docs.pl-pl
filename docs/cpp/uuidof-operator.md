---
title: __uuidof operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
dev_langs:
- C++
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84fd779d50fb481cffc97b61a65f255c6c8f52a1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056742"
---
# <a name="uuidof-operator"></a>Operator __uuidof

**Microsoft Specific**

Pobiera identyfikator GUID podłączony do wyrażenia.

## <a name="syntax"></a>Składnia

```
__uuidof (expression)
```

## <a name="remarks"></a>Uwagi

*Wyrażenie* może być nazwą typu, wskaźnik, odwołanie lub tablicy tego typu, szablon przeznaczone specjalnie dla tych typów lub zmienną typu. Argument jest nieprawidłowy, tak długo, jak kompilator służy można znaleźć dołączonego identyfikatora GUID.

Przypadek specjalny tym wewnętrznych jest, gdy albo **0** lub wartość NULL jest dostarczany jako argument. W tym przypadku **__uuidof** zwróci identyfikator GUID składają się z zer.

Użyj słowa kluczowego, aby wyodrębnić identyfikator GUID podłączony do:

- Obiekt o [uuid](../cpp/uuid-cpp.md) atrybutów rozszerzonych.

- Blok biblioteki utworzonych za pomocą [modułu](../windows/module-cpp.md) atrybutu.

> [!NOTE]
>  Do kompilacji debugowanej **__uuidof** zawsze inicjuje obiekt dynamicznie (w czasie wykonywania). W kompilacji wydania **__uuidof** statycznie (w czasie kompilacji) można zainicjować obiektu.

## <a name="example"></a>Przykład

Poniższy kod (skompilowany przy użyciu ole32.lib) spowoduje wyświetlenie uuid bloku biblioteki utworzonych za pomocą atrybutu modułu:

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

W przypadkach, w którym nazwa biblioteki nie jest już w zakresie, można użyć `__LIBID_` zamiast **__uuidof**. Na przykład:

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
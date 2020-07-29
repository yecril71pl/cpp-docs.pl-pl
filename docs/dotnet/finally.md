---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: b3331c17fc2313cbd6146db3beb015cd8d8c1eeb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221461"
---
# <a name="finally"></a>finally

Oprócz **`try`** **`catch`** klauzul i, obsługa wyjątków CLR obsługuje **`finally`** klauzulę. Semantyka jest identyczna z **`__finally`** blokiem w obsłudze wyjątków strukturalnych (SEH). **`__finally`** Blok może następować po **`try`** **`catch`** bloku lub.

## <a name="remarks"></a>Uwagi

Celem **`finally`** bloku jest wyczyszczenie wszystkich zasobów pozostawionych po wystąpieniu wyjątku. Należy zauważyć, że **`finally`** blok jest zawsze wykonywany, nawet jeśli nie zgłoszono żadnego wyjątku. **`catch`** Blok jest wykonywany tylko wtedy, gdy w skojarzonym bloku zostanie zgłoszony wyjątek zarządzany **`try`** .

`finally`jest kontekstowego słowa kluczowego; Aby uzyskać więcej informacji, zobacz [kontekstowe słowa kluczowe](../extensions/context-sensitive-keywords-cpp-component-extensions.md) .

## <a name="example"></a>Przykład

Poniższy przykład ilustruje prosty **`finally`** blok:

```cpp
// keyword__finally.cpp
// compile with: /clr
using namespace System;

ref class MyException: public System::Exception{};

void ThrowMyException() {
   throw gcnew MyException;
}

int main() {
   try {
      ThrowMyException();
   }
   catch ( MyException^ e ) {
      Console::WriteLine(  "in catch" );
      Console::WriteLine( e->GetType() );
   }
   finally {
      Console::WriteLine(  "in finally" );
   }
}
```

```Output
in catch
MyException
in finally
```

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../extensions/exception-handling-cpp-component-extensions.md)

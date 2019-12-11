---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: 2574ba5a10bbf5eddc68d6e0265d5dfc99c6d8fc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988337"
---
# <a name="finally"></a>finally

Oprócz klauzul `try` i `catch`, obsługa wyjątków CLR obsługuje klauzulę `finally`. Semantyka jest identyczna z blokiem `__finally` w obsłudze wyjątków strukturalnych (SEH). Blok `__finally` może następować po bloku `try` lub `catch`.

## <a name="remarks"></a>Uwagi

Celem bloku `finally` jest wyczyszczenie wszystkich zasobów pozostawionych po wystąpieniu wyjątku. Należy zauważyć, że blok `finally` jest zawsze wykonywany, nawet jeśli nie zgłoszono żadnego wyjątku. Blok `catch` jest wykonywany tylko wtedy, gdy w skojarzonym bloku `try` zostanie zgłoszony wyjątek zarządzany.

`finally` to kontekstowe słowo kluczowe; Aby uzyskać więcej informacji, zobacz [kontekstowe słowa kluczowe](../extensions/context-sensitive-keywords-cpp-component-extensions.md) .

## <a name="example"></a>Przykład

Poniższy przykład ilustruje prosty blok `finally`:

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

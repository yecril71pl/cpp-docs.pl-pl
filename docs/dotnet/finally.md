---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: f7db4320cf901412e3a9e3de682d0cfbcc9f23bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223017"
---
# <a name="finally"></a>finally

Oprócz `try` i `catch` klauzul, obsługa obsługuje wyjątków CLR `finally` klauzuli. Semantyka są takie same jak `__finally` bloku wyjątków strukturalnych (SEH) obsługi. A `__finally` skorzystać z bloku `try` lub `catch` bloku.

## <a name="remarks"></a>Uwagi

Celem `finally` bloku jest Oczyść wszystkie zasoby w lewo po wystąpieniu wyjątku. Należy pamiętać, że `finally` bloku jest wykonywane zawsze, nawet wtedy, gdy żaden wyjątek został zgłoszony. `catch` Bloku jest wykonywana tylko w przypadku zarządzanych wyjątku w obrębie skojarzonej `try` bloku.

`finally` jest kontekstowej słowem kluczowym; zobacz [Context-Sensitive Keywords](../extensions/context-sensitive-keywords-cpp-component-extensions.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano prosty `finally` bloku:

```
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

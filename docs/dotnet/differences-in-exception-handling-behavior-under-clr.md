---
title: Różnice w zachowaniu obsługi wyjątków w przypadku użycia opcji -CLR
ms.date: 11/04/2016
helpviewer_keywords:
- EXCEPTION_CONTINUE_EXECUTION macro
- set_se_translator function
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
ms.openlocfilehash: 940d297ff77248ba9e9980f7032b5d722d95c7eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364379"
---
# <a name="differences-in-exception-handling-behavior-under-clr"></a>Różnice w zachowaniu obsługi wyjątków w przypadku użycia opcji /CLR

[Podstawowe pojęcia w using managed exceptions](../dotnet/basic-concepts-in-using-managed-exceptions.md) omówiono obsługę wyjątków w aplikacjach zarządzanych. W tym temacie różnice w stosunku do standardowego zachowania obsługi wyjątków i niektóre ograniczenia są szczegółowo omówione. Aby uzyskać więcej informacji, zobacz [funkcja _set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="jumping-out-of-a-finally-block"></a><a name="vcconjumpingoutofafinallyblock"></a>Wyskakiwanie z bloku wreszcie

W natywnym kodzie C/C++ wyskakiwanie z bloku __**finally** przy użyciu obsługi wyjątków strukturalnych (SEH) jest dozwolone, mimo że generuje ostrzeżenie.  W [obszarze /clr](../build/reference/clr-common-language-runtime-compilation.md)wyskakiwanie z bloku **finally** powoduje błąd:

```cpp
// clr_exception_handling_4.cpp
// compile with: /clr
int main() {
   try {}
   finally {
      return 0;   // also fails with goto, break, continue
    }
}   // C3276
```

## <a name="raising-exceptions-within-an-exception-filter"></a><a name="vcconraisingexceptionswithinanexceptionfilter"></a>Zgłaszanie wyjątków w ramach filtru wyjątków

Gdy wyjątek jest wywoływany podczas przetwarzania [filtru wyjątków](../cpp/writing-an-exception-filter.md) w kodzie zarządzanym, wyjątek jest przechwytywał i traktowany tak, jakby filtr zwraca 0.

Jest to w przeciwieństwie do zachowania w kodzie macierzystym, gdzie zagnieżdżony wyjątek jest wywoływany, **ExceptionRecord** pole w **strukturze EXCEPTION_RECORD** (zwracany przez [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation)) jest ustawiona, a **exceptionFlags** pole ustawia bit 0x10. Poniższy przykład ilustruje tę różnicę w zachowaniu:

```cpp
// clr_exception_handling_5.cpp
#include <windows.h>
#include <stdio.h>
#include <assert.h>

#ifndef false
#define false 0
#endif

int *p;

int filter(PEXCEPTION_POINTERS ExceptionPointers) {
   PEXCEPTION_RECORD ExceptionRecord =
                     ExceptionPointers->ExceptionRecord;

   if ((ExceptionRecord->ExceptionFlags & 0x10) == 0) {
      // not a nested exception, throw one
      *p = 0; // throw another AV
   }
   else {
      printf("Caught a nested exception\n");
      return 1;
    }

   assert(false);

   return 0;
}

void f(void) {
   __try {
      *p = 0;   // throw an AV
   }
   __except(filter(GetExceptionInformation())) {
      printf_s("We should execute this handler if "
                 "compiled to native\n");
    }
}

int main() {
   __try {
      f();
   }
   __except(1) {
      printf_s("The handler in main caught the "
               "exception\n");
    }
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Caught a nested exception
We should execute this handler if compiled to native
```

## <a name="disassociated-rethrows"></a><a name="vccondisassociatedrethrows"></a>Rozłączone rethrows

**/clr** nie obsługuje ponownego wyrostka wyjątku poza programem obsługi catch (znanym jako odłączony rethrow). Wyjątki tego typu są traktowane jako standardowe c++ rethrow. Jeśli rozłączony rethrow występuje, gdy istnieje aktywny wyjątek zarządzany, wyjątek jest zawijany jako wyjątek C++, a następnie rethrown. Wyjątki tego typu można złapać tylko jako <xref:System.Runtime.InteropServices.SEHException>wyjątek typu.

Poniższy przykład pokazuje rethrown wyjątek zarządzany jako wyjątek C++:

```cpp
// clr_exception_handling_6.cpp
// compile with: /clr
using namespace System;
#include <assert.h>
#include <stdio.h>

void rethrow( void ) {
   // This rethrow is a dissasociated rethrow.
   // The exception would be masked as SEHException.
   throw;
}

int main() {
   try {
      try {
         throw gcnew ApplicationException;
      }
      catch ( ApplicationException^ ) {
         rethrow();
         // If the call to rethrow() is replaced with
         // a throw statement within the catch handler,
         // the rethrow would be a managed rethrow and
         // the exception type would remain
         // System::ApplicationException
      }
   }

    catch ( ApplicationException^ ) {
      assert( false );

      // This will not be executed since the exception
      // will be masked as SEHException.
    }
   catch ( Runtime::InteropServices::SEHException^ ) {
      printf_s("caught an SEH Exception\n" );
    }
}
```

### <a name="output"></a>Dane wyjściowe

```Output
caught an SEH Exception
```

## <a name="exception-filters-and-exception_continue_execution"></a><a name="vcconexceptionfiltersandexception_continue_execution"></a>Filtry wyjątków i EXCEPTION_CONTINUE_EXECUTION

Jeśli filtr `EXCEPTION_CONTINUE_EXECUTION` zwraca w aplikacji zarządzanej, jest traktowany `EXCEPTION_CONTINUE_SEARCH`tak, jakby filtr zwrócił . Aby uzyskać więcej informacji na temat tych stałych, zobacz [try-except Instrukcji](../cpp/try-except-statement.md).

Poniższy przykład pokazuje tę różnicę:

```cpp
// clr_exception_handling_7.cpp
#include <windows.h>
#include <stdio.h>
#include <assert.h>

int main() {
   int Counter = 0;
   __try {
      __try  {
         Counter -= 1;
         RaiseException (0xe0000000|'seh',
                         0, 0, 0);
         Counter -= 2;
      }
      __except (Counter) {
         // Counter is negative,
         // indicating "CONTINUE EXECUTE"
         Counter -= 1;
      }
    }
    __except(1) {
      Counter -= 100;
   }

   printf_s("Counter=%d\n", Counter);
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Counter=-3
```

## <a name="the-_set_se_translator-function"></a><a name="vcconthe_set_se_translatorfunction"></a>Funkcja _set_se_translator

Funkcja translatora, ustawiona `_set_se_translator`przez wywołanie do , wpływa tylko na połowy w kodzie niezarządzanym. Poniższy przykład pokazuje to ograniczenie:

```cpp
// clr_exception_handling_8.cpp
// compile with: /clr /EHa
#include <iostream>
#include <windows.h>
#include <eh.h>
#pragma warning (disable: 4101)
using namespace std;
using namespace System;

#define MYEXCEPTION_CODE 0xe0000101

class CMyException {
public:
   unsigned int m_ErrorCode;
   EXCEPTION_POINTERS * m_pExp;

   CMyException() : m_ErrorCode( 0 ), m_pExp( NULL ) {}

   CMyException( unsigned int i, EXCEPTION_POINTERS * pExp )
         : m_ErrorCode( i ), m_pExp( pExp ) {}

   CMyException( CMyException& c ) : m_ErrorCode( c.m_ErrorCode ),
                                      m_pExp( c.m_pExp ) {}

   friend ostream& operator <<
                 ( ostream& out, const CMyException& inst ) {
      return out <<  "CMyException[\n" <<
             "Error Code: " << inst.m_ErrorCode <<  "]";
    }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS pExp ) {
   cout <<  "In my_trans_func.\n";
   throw CMyException( u, pExp );
}

#pragma managed
void managed_func() {
   try  {
      RaiseException( MYEXCEPTION_CODE, 0, 0, 0 );
   }
   catch ( CMyException x ) {}
   catch ( ... ) {
      printf_s("This is invoked since "
               "_set_se_translator is not "
               "supported when /clr is used\n" );
    }
}

#pragma unmanaged
void unmanaged_func() {
   try  {
      RaiseException( MYEXCEPTION_CODE,
                      0, 0, 0 );
   }
   catch ( CMyException x ) {
      printf("Caught an SEH exception with "
             "exception code: %x\n", x.m_ErrorCode );
    }
    catch ( ... ) {}
}

// #pragma managed
int main( int argc, char ** argv ) {
   _set_se_translator( my_trans_func );

   // It does not matter whether the translator function
   // is registered in managed or unmanaged code
   managed_func();
   unmanaged_func();
}
```

### <a name="output"></a>Dane wyjściowe

```Output
This is invoked since _set_se_translator is not supported when /clr is used
In my_trans_func.
Caught an SEH exception with exception code: e0000101
```

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Obsługa wyjątków w msvc](../cpp/exception-handling-in-visual-cpp.md)

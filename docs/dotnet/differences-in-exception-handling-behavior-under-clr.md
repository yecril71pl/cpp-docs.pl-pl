---
title: Różnice w zachowaniu obsługi wyjątków w / CLR
ms.date: 11/04/2016
helpviewer_keywords:
- EXCEPTION_CONTINUE_EXECUTION macro
- set_se_translator function
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
ms.openlocfilehash: ae745cfb96f4efe1ede7e3fc762842f9e4d63323
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772741"
---
# <a name="differences-in-exception-handling-behavior-under-clr"></a>Różnice w zachowaniu obsługi wyjątków w przypadku użycia opcji /CLR

[Podstawowe pojęcia związane z przy użyciu zarządzane wyjątki](../dotnet/basic-concepts-in-using-managed-exceptions.md) w tym artykule omówiono obsługę wyjątków w aplikacjach zarządzanych. W tym temacie opisano szczegółowo różnice w stosunku do standardowego zachowania obsługi wyjątków i pewne ograniczenia. Aby uzyskać więcej informacji, zobacz [_set_se_translator — funkcja](../c-runtime-library/reference/set-se-translator.md).

##  <a name="vcconjumpingoutofafinallyblock"></a> Skok na zewnątrz bloku Finally

W kodzie natywnym C/C++, skok poza __**na koniec** bloku przy użyciu obsługi wyjątków strukturalnych (SEH) jest dozwolone, mimo że generuje ostrzeżenie.  W obszarze [/CLR](../build/reference/clr-common-language-runtime-compilation.md), skok na zewnątrz **na koniec** bloku powoduje błąd:

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

##  <a name="vcconraisingexceptionswithinanexceptionfilter"></a> Występowanie wyjątków w ramach filtra wyjątku

Gdy tworzony jest wyjątek podczas przetwarzania [filtra wyjątku](../cpp/writing-an-exception-filter.md) w kodzie zarządzanym wyjątek zgłoszony i traktowany tak, jakby filtr zwraca wartość 0.

Jest to w przeciwieństwie do zachowania w kodzie natywnym, w którym jest zgłoszony wyjątek zagnieżdżony, **ExceptionRecord** pole **EXCEPTION_RECORD** struktury (zwrócone przez [ GetExceptionInformation](/windows/desktop/Debug/getexceptioninformation)) jest ustawiona i **ExceptionFlags** pola ustawia 0x10 bit. Poniższy przykład ilustruje ten różnice w zachowaniu:

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

##  <a name="vccondisassociatedrethrows"></a> Ponownie zgłasza których skojarzenie usunięto

**/ CLR** nie obsługuje ponowne generowanie wyjątku poza obsługi catch (nazywanych, których skojarzenie usunięto Zgłoś ponownie). Wyjątki tego typu są traktowane jako standard C++ Zgłoś ponownie. Jeśli których skojarzenie usunięto Zgłoś ponownie po active zarządzanych wyjątek, wyjątek jest opakowane w wyjątek C++ i następnie zgłaszany ponownie. Wyjątki tego typu można stosować wyłącznie jako wyjątek typu <xref:System.Runtime.InteropServices.SEHException>.

Poniższy przykład ilustruje wyjątków zarządzanych zgłaszany ponownie jako wyjątków C++:

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

##  <a name="vcconexceptionfiltersandexception_continue_execution"></a> Filtry wyjątków i EXCEPTION_CONTINUE_EXECUTION

Jeśli filtr zwróci `EXCEPTION_CONTINUE_EXECUTION` w zarządzanej aplikacji, jest ona traktowana jak gdyby filtr zwrócił `EXCEPTION_CONTINUE_SEARCH`. Aby uzyskać więcej informacji na temat tych stałych, zobacz [spróbuj-except, instrukcja](../cpp/try-except-statement.md).

Poniższy przykład ilustruje różnicę:

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

##  <a name="vcconthe_set_se_translatorfunction"></a> The _set_se_translator Function

Ustaw funkcję tłumacza, przez wywołanie `_set_se_translator`, dotyczy tylko pamięci w niezarządzanym kodzie. W poniższym przykładzie pokazano tego ograniczenia:

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

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)

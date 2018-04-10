---
title: Różnice w zachowaniu obsługi wyjątków w - CLR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- EXCEPTION_CONTINUE_EXECUTION macro
- set_se_translator function
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 56bacf88b2c633704b46c6d0de3bb313767b7b2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="differences-in-exception-handling-behavior-under-clr"></a>Różnice w zachowaniu obsługi wyjątków w przypadku użycia opcji /CLR
[Podstawowe pojęcia związane z wyjątków zarządzanych przy użyciu](../dotnet/basic-concepts-in-using-managed-exceptions.md) omówiono obsługi wyjątków w zarządzanych aplikacji. W tym temacie opisano szczegółowo różnic od standardowego zachowania wyjątków i pewne ograniczenia. Aby uzyskać więcej informacji, zobacz [_set_se_translator — funkcja](../c-runtime-library/reference/set-se-translator.md).  
  
##  <a name="vcconjumpingoutofafinallyblock"></a>Przeskakiwanie z bloku Finally  
 W kodzie C/C++ natywnym, przeskakiwanie poza __**koniec** bloku przy użyciu Obsługa wyjątków strukturalnych (SEH) jest dozwolone, mimo że generuje ostrzeżenie.  W obszarze [/CLR](../build/reference/clr-common-language-runtime-compilation.md), przejście z **koniec** bloku spowoduje wystąpienie błędu:  
  
```  
// clr_exception_handling_4.cpp  
// compile with: /clr  
int main() {  
   try {}  
   finally {  
      return 0;   // also fails with goto, break, continue  
    }  
}   // C3276  
```  
  
##  <a name="vcconraisingexceptionswithinanexceptionfilter"></a>Występowanie wyjątków w ramach filtru wyjątków  
 Jeśli podczas przetwarzania jest wyjątek [filtru wyjątków](../cpp/writing-an-exception-filter.md) w kod zarządzany wyjątek przechwycony i traktowany jak filtr zwraca wartość 0.  
  
 Dzięki temu nie trzeba zachowanie w kodzie natywnym, w którym zagnieżdżonych wyjątek jest zgłaszany, **ExceptionRecord** w **EXCEPTION_RECORD** struktury (zwrócony przez [ GetExceptionInformation](http://msdn.microsoft.com/library/windows/desktop/ms679357)) jest ustawiona i **ExceptionFlags** pola ustawia 0x10 bit. Poniższy przykład przedstawia różnica w zachowanie:  
  
```  
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
  
```  
Caught a nested exception  
We should execute this handler if compiled to native  
```  
  
##  <a name="vccondisassociatedrethrows"></a>Ponownie zgłasza usunięte skojarzenia  
 **/ CLR** nie obsługuje ponowne generowanie wyjątek spoza obsługi catch (nazywane już rethrow). Wyjątki tego typu są traktowane jako standardowe rethrow C++. Jeśli już rethrow po active zarządzanym wyjątku, wyjątek jest opakowana wyjątek C++ i następnie zgłoszony. Wyjątki tego typu można stosować wyłącznie jako wyjątek typu [System::SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx).  
  
 W poniższym przykładzie pokazano zarządzany wyjątek zgłoszony wyjątek C++:  
  
```  
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
  
```  
caught an SEH Exception  
```  
  
##  <a name="vcconexceptionfiltersandexception_continue_execution"></a>Filtry wyjątków i exception_continue_execution —  
 Jeśli filtr zwróci `EXCEPTION_CONTINUE_EXECUTION` w aplikacji zarządzanej, jest traktowany jak gdyby filtr zwrócił `EXCEPTION_CONTINUE_SEARCH`. Aby uzyskać więcej informacji na te stałe, zobacz [spróbuj-except — instrukcja](../cpp/try-except-statement.md).  
  
 W poniższym przykładzie pokazano tej różnicy:  
  
```  
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
  
```  
Counter=-3  
```  
  
##  <a name="vcconthe_set_se_translatorfunction"></a>_Set_se_translator — funkcja  
 Funkcja translator ustawiony przez wywołanie do `_set_se_translator`, dotyczy tylko połowy za pomocą kodu niezarządzanego. W poniższym przykładzie pokazano tego ograniczenia:  
  
```  
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
  
```  
This is invoked since _set_se_translator is not supported when /clr is used  
In my_trans_func.  
Caught an SEH exception with exception code: e0000101  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../windows/exception-handling-cpp-component-extensions.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)
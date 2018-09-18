---
title: auto_handle::reset | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- auto_handle.reset
- msclr::auto_handle::reset
- auto_handle::reset
- msclr.auto_handle.reset
dev_langs:
- C++
helpviewer_keywords:
- auto_handle::reset
ms.assetid: 32dc3a83-80fd-45c9-8f79-8c4096c30f57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7596829cc89dcfa335b38d24a57666a430507e27
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111722"
---
# <a name="autohandlereset"></a>auto_handle::reset
Zniszczenie bieżącego obiektu należące do firmy, a następnie opcjonalnie zająć posiadania nowego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
void reset(  
   _element_type ^ _new_ptr  
);  
void reset();  
```  
  
#### <a name="parameters"></a>Parametry  
*_new_ptr*<br/>
(Opcjonalnie) Nowy obiekt.  
  
## <a name="example"></a>Przykład  
  
```  
// msl_auto_handle_reset.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
   String^ m_s;  
public:  
   ClassA( String^ s ) : m_s( s ) {  
      Console::WriteLine( "ClassA constructor: " + m_s );  
   }  
   ~ClassA() {  
      Console::WriteLine( "ClassA destructor: " + m_s );  
   }  
  
   void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );  
   }  
};  
  
int main()  
{  
   auto_handle<ClassA> agc1 = gcnew ClassA( "first" );  
   agc1->PrintHello();  
  
   ClassA^ ha = gcnew ClassA( "second" );  
   agc1.reset( ha ); // release first object, reference second  
   agc1->PrintHello();  
  
   agc1.reset(); // release second object, set to nullptr  
  
   Console::WriteLine( "done" );  
}  
```  
  
```Output  
ClassA constructor: first  
Hello from first A!  
ClassA constructor: second  
ClassA destructor: first  
Hello from second A!  
ClassA destructor: second  
done  
```  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówkowy** \<msclr\auto_handle.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Zobacz też  
 [auto_handle, składowe](../dotnet/auto-handle-members.md)   
 [auto_handle::release](../dotnet/auto-handle-release.md)
---
title: na koniec | Dokumentacja firmy Microsoft
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
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dd357c8eeed9eddc6940ce02de6e5d2b4f8c68d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="finally"></a>finally
Oprócz `try` i `catch` klauzule, obsługa obsługuje wyjątków CLR `finally` klauzuli. Semantyka są takie same jak `__finally` block (SEH) do obsługi wyjątków strukturalnych. A `__finally` bloku można wykonać `try` lub `catch` bloku.  
  
## <a name="remarks"></a>Uwagi  
 Celem `finally` blok jest, aby wyczyścić wszystkie zasoby po Wystąpił wyjątek. Należy pamiętać, że `finally` bloku jest wykonywane zawsze, nawet jeśli nie zgłoszono wyjątek. `catch` Bloku jest wykonywana tylko w przypadku zarządzanych wyjątku w skojarzonych `try` bloku.  
  
 `finally`jest słowem kluczowym kontekstowa; zobacz [słowa kluczowe Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../windows/exception-handling-cpp-component-extensions.md)
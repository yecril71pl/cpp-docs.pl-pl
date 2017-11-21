---
title: marshal_context::marshal_as | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- marshal_context::marshal_as
- marshal_context.marshal_as
- msclr.interop.marshal_context.marshal_as
- msclr::interop::marshal_context::marshal_as
dev_langs: C++
helpviewer_keywords: marshal_context class [C++], operations
ms.assetid: 24a1afee-51c0-497c-948c-f77fe43635c8
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8cf8d8728a71f268db994efdc60f4be0dc5a65a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="marshalcontextmarshalas"></a>marshal_context::marshal_as
Wykonuje organizowanie na obiekt danych określonego można przełączać się między zarządzanego i typu danych w trybie macierzystym.  
  
## <a name="syntax"></a>Składnia  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`input`  
 Wartość, która ma być kierować do `To_Type` zmiennej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zmienna typu `To_Type` czyli przekonwertowanego wartość `input`.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja wykonuje przekazywanie obiektu określonych danych. Za pomocą tej funkcji tylko konwersje wskazanych przez tabelę w [omówienie z Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md).  
  
 Jeśli spróbujesz kierować dwa typy danych, które nie są obsługiwane, `marshal_as` wygeneruje błąd [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) w czasie kompilacji. Przeczytaj wiadomość dostarczona dotyczącą tego błędu, aby uzyskać więcej informacji. `C4996` Błędu mogą być generowane dla więcej niż tylko przestarzałych funkcji. Dwa warunki, które spowoduje wygenerowanie tego błędu są próby skierowania dwa typy danych, które nie są obsługiwane i próbuje użyć `marshal_as` konwersji, która wymaga kontekstu.  
  
 Biblioteka organizowania składa się z kilku plików nagłówka. Wszelkie konwersja wymaga tylko jednego pliku, ale może zawierać dodatkowe pliki, jeśli zachodzi konieczność dla innych konwersji. Tabela w `Marshaling Overview in C++` wskazuje, który zawiera plik powinny zostać uwzględnione w poszczególnych konwersji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest tworzony organizowanie z kontekstem `System::String` do `const char *` typu zmiennej. Przekonwertowana danych nie będą prawidłowe po wierszu, który usuwa kontekstu.  
  
```  
// marshal_context_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   marshal_context^ context = gcnew marshal_context();  
   String^ message = gcnew String("Test String to Marshal");  
   const char* result;  
   result = context->marshal_as<const char*>( message );  
   delete context;  
   return 0;  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, lub \<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as —](../dotnet/marshal-as.md)   
 [marshal_context — klasa](../dotnet/marshal-context-class.md)
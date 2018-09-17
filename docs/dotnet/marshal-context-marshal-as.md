---
title: marshal_context::marshal_as | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::marshal_as
- marshal_context.marshal_as
- msclr.interop.marshal_context.marshal_as
- msclr::interop::marshal_context::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 24a1afee-51c0-497c-948c-f77fe43635c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f88d086c76ea6b56f1bb049b886df70ceadbdbb9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707905"
---
# <a name="marshalcontextmarshalas"></a>marshal_context::marshal_as
Wykonuje marshalingu obiektu określonych danych, aby przekonwertować go między zarządzanego i macierzystego typu danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*Dane wejściowe*<br/>
[in] Wartość, którą chcesz kierować do `To_Type` zmiennej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zmienna typu `To_Type` oznacza to przekonwertowana wartości `input`.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja wykonuje marshalingu obiektu określonych danych. Za pomocą tej funkcji tylko konwersje wskazywanym przez tabelę w [Overview of Marshaling w C++](../dotnet/overview-of-marshaling-in-cpp.md).  
  
 Jeśli zostanie podjęta próba kierować dwa typy danych, które nie są obsługiwane, `marshal_as` spowoduje wygenerowanie błędu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) w czasie kompilacji. Przeczytaj wiadomości podano dotyczącą tego błędu, aby uzyskać więcej informacji. `C4996` Błędu mogą być generowane dla więcej niż tylko przestarzałych funkcji. Dwa warunki, które będą generowały tego błędu są próby skierowania dwa typy danych, które nie są obsługiwane i próby użycia `marshal_as` konwersji, która wymaga kontekstu.  
  
 Biblioteka dotycząca organizowania składa się z kilku plików nagłówkowych. Każda konwersja wymaga tylko jednego pliku, ale może zawierać dodatkowe pliki, jeśli potrzebujesz, w przypadku innych konwersji. W tabeli `Marshaling Overview in C++` wskazuje plik, który zawiera powinny zostać uwzględnione w poszczególnych konwersji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzy kontekst do kierowania z `System::String` do `const char *` typ zmiennej. Przekonwertowane dane nie będą prawidłowe po wierszu, który usuwa kontekst.  
  
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
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context, klasa](../dotnet/marshal-context-class.md)
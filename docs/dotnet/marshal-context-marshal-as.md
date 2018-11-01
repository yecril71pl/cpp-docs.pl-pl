---
title: marshal_context::marshal_as
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- marshal_context::marshal_as
- marshal_context.marshal_as
- msclr.interop.marshal_context.marshal_as
- msclr::interop::marshal_context::marshal_as
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 24a1afee-51c0-497c-948c-f77fe43635c8
ms.openlocfilehash: b097fda0870b2f49d4883e0fafd48f9637d28853
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649780"
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

[Omówienie marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context, klasa](../dotnet/marshal-context-class.md)
---
title: marshal_as
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
ms.openlocfilehash: 2294d8fe94a32f281332c963b21a542366ae3207
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751513"
---
# <a name="marshalas"></a>marshal_as

Ta metoda konwertuje dane między środowiskami macierzystymi i zarządzanymi.

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

Ta metoda jest uproszczony sposób konwertowania danych między typami macierzystym i zarządzanym. Aby określić, jakie typy danych są obsługiwane, zobacz [Overview of Marshaling w C++](../dotnet/overview-of-marshaling-in-cpp.md). Konwersje niektórych danych wymaga kontekstu. Te typy danych można przekonwertować, używając [marshal_context Class](../dotnet/marshal-context-class.md).

Jeśli zostanie podjęta próba kierować dwa typy danych, które nie są obsługiwane, `marshal_as` spowoduje wygenerowanie błędu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) w czasie kompilacji. Przeczytaj wiadomości podano dotyczącą tego błędu, aby uzyskać więcej informacji. `C4996` Błędu mogą być generowane dla więcej niż tylko przestarzałych funkcji. Przykładem takiej próby kierować dwa typy danych, które nie są obsługiwane.

Biblioteka dotycząca organizowania składa się z kilku plików nagłówkowych. Każda konwersja wymaga tylko jednego pliku, ale może zawierać dodatkowe pliki, jeśli potrzebujesz, w przypadku innych konwersji. Aby zobaczyć, jakie konwersje są skojarzone z plików, Szukaj w tabeli w `Marshaling Overview`. Niezależnie od tego konwersji, jakie chcesz zrobić, wymaganie przestrzeni nazw jest zawsze w obiekcie.

## <a name="example"></a>Przykład

W tym przykładzie kieruje z `const char*` do `System::String` typ zmiennej.

```
// marshal_as_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   const char* message = "Test String to Marshal";
   String^ result;
   result = marshal_as<String^>( message );
   return 0;
}
```

## <a name="requirements"></a>Wymagania

**Plik nagłówka:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, lub \<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="see-also"></a>Zobacz także

[Omówienie marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context, klasa](../dotnet/marshal-context-class.md)

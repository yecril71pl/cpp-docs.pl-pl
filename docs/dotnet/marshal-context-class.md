---
title: marshal_context — Klasa
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- msclr::interop::marshal_context::marshal_as
helpviewer_keywords:
- msclr::marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
ms.openlocfilehash: 25fc2be80ba0e5d8c7f76cee1f22eed4d1bb4fc7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384871"
---
# <a name="marshalcontext-class"></a>marshal_context — Klasa

Ta klasa konwertuje dane między środowiskami macierzystymi i zarządzanymi.

## <a name="syntax"></a>Składnia

```cpp
class marshal_context
```

## <a name="remarks"></a>Uwagi

Użyj `marshal_context` klasy podczas konwersji danych, które wymagają kontekst. Aby uzyskać więcej informacji o jakie konwersje wymaga kontekstu i organizowania plik, który ma zostać uwzględniony, zobacz [omówienie marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md). Organizowanie, korzystając z kontekstu wynik jest prawidłowy tylko do `marshal_context` niszczony jest obiekt. Aby zachować wyników, należy skopiować dane.

Taki sam `marshal_context` może służyć do wielu konwersji danych. Ponowne używanie kontekstu w ten sposób nie wpłyną na wyniki z poprzedniego wywołania organizowania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis| 
|---------|-----------| 
|[marshal_context::marshal_context](#marshal-context)|Konstruuje `marshal_context` obiekt ma być używany do konwersji danych między typami danych zarządzanego i natywnego.| 
|[marshal_context::~marshal_context](#tilde-marshal-context)|Niszczy `marshal_context` obiektu.| 

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis| 
|---------|-----------| 
|[marshal_context::marshal_as](#marshal-as)|Wykonuje marshalingu obiektu określonych danych, aby przekonwertować go między zarządzanego i macierzystego typu danych.| 


## <a name="requirements"></a>Wymagania

**Plik nagłówka:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, lub \<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="marshal-context"></a>marshal_context::marshal_context

Konstruuje `marshal_context` obiekt ma być używany do konwersji danych między typami danych zarządzanego i natywnego.

```cpp
marshal_context();
```

### <a name="remarks"></a>Uwagi

Konwersje niektórych danych wymaga kontekstu marshal. Aby uzyskać więcej informacji na temat tłumaczenia wymaga kontekstu i które marshaling plik musi zawierać w swojej aplikacji, zobacz [omówienie marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Przykład

Zobacz przykład [marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md).


## <a name="tilde-marshal-context"></a>marshal_context:: ~ marshal_context

Niszczy `marshal_context` obiektu.

```cpp
~marshal_context();
```

### <a name="remarks"></a>Uwagi

Konwersje niektórych danych wymaga kontekstu marshal. Zobacz [omówienie marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md) Aby uzyskać więcej informacji na temat tłumaczenia, które wymagają kontekstu i organizowania plik, który musi być ujęta w aplikacji.

Usuwanie `marshal_context` obiektu spowoduje unieważnienie danych przekonwertowane przez ten kontekst. Jeśli chcesz zachować dane po `marshal_context` obiekt jest niszczony, należy ręcznie skopiować dane do zmiennej, który będzie aktualny.

## <a name="marshal-as"></a>marshal_context::marshal_as

Wykonuje marshalingu obiektu określonych danych, aby przekonwertować go między zarządzanego i macierzystego typu danych.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Parametry

*Dane wejściowe*<br/>
[in] Wartość, którą chcesz kierować do `To_Type` zmiennej.

### <a name="return-value"></a>Wartość zwracana

Zmienna typu `To_Type` to przekonwertowana wartości `input`.

### <a name="remarks"></a>Uwagi

Ta funkcja wykonuje marshalingu obiektu określonych danych. Za pomocą tej funkcji tylko konwersje wskazywanym przez tabelę w [omówienie marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md).

Jeśli zostanie podjęta próba kierować dwa typy danych, które nie są obsługiwane, `marshal_as` spowoduje wygenerowanie błędu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) w czasie kompilacji. Przeczytaj wiadomości podano dotyczącą tego błędu, aby uzyskać więcej informacji. `C4996` Błędu mogą być generowane dla więcej niż tylko przestarzałych funkcji. Dwa warunki, które generują tego błędu są próby skierowania dwa typy danych, które nie są obsługiwane i próby użycia `marshal_as` konwersji, która wymaga kontekstu.

Biblioteka dotycząca organizowania składa się z kilku plików nagłówkowych. Każda konwersja wymaga tylko jednego pliku, ale może zawierać dodatkowe pliki, jeśli potrzebujesz, w przypadku innych konwersji. W tabeli `Marshaling Overview in C++` wskazuje plik, który zawiera powinny zostać uwzględnione w poszczególnych konwersji.

### <a name="example"></a>Przykład

W tym przykładzie tworzy kontekst do kierowania z `System::String` do `const char *` typ zmiennej. Przekonwertowane dane nie będą prawidłowe po wierszu, który usuwa kontekst.

```cpp
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
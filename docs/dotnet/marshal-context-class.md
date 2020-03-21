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
ms.openlocfilehash: 7fb22754248e66d7a20292af41a8e1b8ba050451
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080032"
---
# <a name="marshal_context-class"></a>marshal_context — Klasa

Ta klasa konwertuje dane między środowiskami macierzystymi i zarządzanymi.

## <a name="syntax"></a>Składnia

```cpp
class marshal_context
```

## <a name="remarks"></a>Uwagi

Użyj klasy `marshal_context` na potrzeby konwersji danych, które wymagają kontekstu. Aby uzyskać więcej informacji o tym, które konwersje wymagają kontekstu, a plik kierujący musi być uwzględniony, zobacz [Omówienie organizowania w C++ ](../dotnet/overview-of-marshaling-in-cpp.md). Wynik organizowania przy użyciu kontekstu jest prawidłowy tylko do momentu zniszczenia obiektu `marshal_context`. Aby zachować wynik, należy skopiować dane.

Ten sam `marshal_context` może służyć do licznych konwersji danych. Użycie kontekstu w ten sposób nie wpłynie na wyniki poprzednich wywołań kierujących.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|Konstruuje obiekt `marshal_context`, który będzie używany do konwersji danych między typami danych zarządzanymi i natywnymi.|
|[marshal_context::~marshal_context](#tilde-marshal-context)|Niszczy obiekt `marshal_context`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|Wykonuje kierowanie dla określonego obiektu danych, aby przekonwertować go między typem danych zarządzanym i natywnym.|

## <a name="requirements"></a>Wymagania

**Plik nagłówkowy:** \<msclr\marshal.h >, \<msclr \ marshal_windows. h >, \<msclr \ marshal_cppstd. h > lub \<msclr \ marshal_atl. h >

**Przestrzeń nazw:** msclr:: Interop

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a>marshal_context:: marshal_context

Konstruuje obiekt `marshal_context`, który będzie używany do konwersji danych między typami danych zarządzanymi i natywnymi.

```cpp
marshal_context();
```

### <a name="remarks"></a>Uwagi

Niektóre konwersje danych wymagają kontekstu Marshal. Aby uzyskać więcej informacji o tym, które tłumaczenia wymagają kontekstu i pliku Marshal, który należy dołączyć do aplikacji, zobacz [Omówienie organizowania w C++ ](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Przykład

Zobacz przykład dla [marshal_context:: marshal_as](../dotnet/marshal-context-marshal-as.md).

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a>marshal_context:: ~ marshal_context

Niszczy obiekt `marshal_context`.

```cpp
~marshal_context();
```

### <a name="remarks"></a>Uwagi

Niektóre konwersje danych wymagają kontekstu Marshal. Zobacz [Omówienie organizowania w programie C++ ](../dotnet/overview-of-marshaling-in-cpp.md) , aby uzyskać więcej informacji o tym, które tłumaczenia wymagają kontekstu, a plik Marshal musi znajdować się w aplikacji.

Usunięcie obiektu `marshal_context` spowoduje unieważnienie danych przekonwertowanych przez ten kontekst. Jeśli chcesz zachować dane po zniszczeniu obiektu `marshal_context`, musisz ręcznie skopiować dane do zmiennej, która będzie trwała.

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a>marshal_context:: marshal_as

Wykonuje kierowanie dla określonego obiektu danych, aby przekonwertować go między typem danych zarządzanym i natywnym.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Parametry

*klawiatur*<br/>
podczas Wartość, którą chcesz zorganizować na zmienną `To_Type`.

### <a name="return-value"></a>Wartość zwracana

Zmienna typu `To_Type`, która jest przekonwertowaną wartością `input`.

### <a name="remarks"></a>Uwagi

Ta funkcja wykonuje kierowanie dla określonego obiektu danych. Tej funkcji należy używać tylko z konwersjemi wskazanymi w tabeli w temacie [Omówienie organizowania w C++ ](../dotnet/overview-of-marshaling-in-cpp.md).

Jeśli spróbujesz zorganizować parę typów danych, które nie są obsługiwane, `marshal_as` wygeneruje błąd [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) w czasie kompilacji. Przeczytaj komunikat dostarczony z tym błędem, aby uzyskać więcej informacji. Błąd `C4996` może być wygenerowany dla więcej niż tylko przestarzałych funkcji. Dwa warunki generujące ten błąd próbują zorganizować parę typów danych, które nie są obsługiwane, i próbować użyć `marshal_as` dla konwersji wymagającej kontekstu.

Biblioteka organizowania składa się z kilku plików nagłówkowych. Każda konwersja wymaga tylko jednego pliku, ale można dołączyć dodatkowe pliki, jeśli zachodzi potrzeba przeprowadzenia innych konwersji. Tabela w `Marshaling Overview in C++` wskazuje, który plik Marshal powinien być dołączony dla każdej konwersji.

### <a name="example"></a>Przykład

Ten przykład tworzy kontekst do organizowania z `System::String` do `const char *` typu zmiennej. Skonwertowane dane nie będą prawidłowe po wierszu, który usuwa kontekst.

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
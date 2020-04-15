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
ms.openlocfilehash: 110fe4abf7eb90b05e7feef563efa4882bed0fc6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332012"
---
# <a name="marshal_context-class"></a>marshal_context — Klasa

Ta klasa konwertuje dane między środowiskami macierzystymi i zarządzanymi.

## <a name="syntax"></a>Składnia

```cpp
class marshal_context
```

## <a name="remarks"></a>Uwagi

Użyj `marshal_context` klasy dla konwersji danych, które wymagają kontekstu. Aby uzyskać więcej informacji o tym, które konwersje wymagają kontekstu i który plik organizowania musi zostać uwzględniony, zobacz [Omówienie organizowania w języku C++](../dotnet/overview-of-marshaling-in-cpp.md). Wynik organizowania podczas korzystania z kontekstu jest `marshal_context` prawidłowy tylko do momentu zniszczenia obiektu. Aby zachować wynik, należy skopiować dane.

To `marshal_context` samo może być używane do wielu konwersji danych. Ponowne przywykanie kontekstu w ten sposób nie wpłynie na wyniki z poprzednich wywołań organizowania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktorzy publiczni

|Nazwa|Opis|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|Konstruuje `marshal_context` obiekt do konwersji danych między typami danych zarządzanych i natywnych.|
|[marshal_context::~marshal_context](#tilde-marshal-context)|Niszczy `marshal_context` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|Wykonuje kierowanie na określonym obiekcie danych, aby przekonwertować go między zarządzanym i macierzystym typem danych.|

## <a name="requirements"></a>Wymagania

**Plik nagłówka:** \<msclr\marshal.h \<>, msclr\marshal_windows.h>, \<msclr\marshal_cppstd.h> lub \<msclr\marshal_atl.h>

**Obszar nazw:** msclr::interop

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a>marshal_context::marshal_context

Konstruuje `marshal_context` obiekt do konwersji danych między typami danych zarządzanych i natywnych.

```cpp
marshal_context();
```

### <a name="remarks"></a>Uwagi

Niektóre konwersje danych wymagają kontekstu marszałka. Aby uzyskać więcej informacji o tym, które tłumaczenia wymagają kontekstu i który plik organizowania należy uwzględnić w aplikacji, zobacz [Omówienie organizowania w języku C++](../dotnet/overview-of-marshaling-in-cpp.md).

### <a name="example"></a>Przykład

Zobacz [przykład: marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md).

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a>marshal_context::~marshal_context

Niszczy `marshal_context` obiekt.

```cpp
~marshal_context();
```

### <a name="remarks"></a>Uwagi

Niektóre konwersje danych wymagają kontekstu marszałka. Zobacz [omówienie organizowania w języku C++,](../dotnet/overview-of-marshaling-in-cpp.md) aby uzyskać więcej informacji o tym, które tłumaczenia wymagają kontekstu i który plik organizowania musi zostać uwzględniony w aplikacji.

Usunięcie `marshal_context` obiektu spowoduje unieważnienie danych przekonwertowanych przez ten kontekst. Jeśli chcesz zachować dane `marshal_context` po zniszczeniu obiektu, należy ręcznie skopiować dane do zmiennej, która będzie się powtarzać.

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a>marshal_context::marshal_as

Wykonuje kierowanie na określonym obiekcie danych, aby przekonwertować go między zarządzanym i macierzystym typem danych.

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>Parametry

*Wejście*<br/>
[w] Wartość, która ma być `To_Type` kierowana do zmiennej.

### <a name="return-value"></a>Wartość zwracana

Zmienna typu, `To_Type` która jest przekonwertowana wartość `input`.

### <a name="remarks"></a>Uwagi

Ta funkcja wykonuje kierowanie na określonym obiekcie danych. Tej funkcji należy używać tylko z konwersjami wskazanymi w tabeli w [przeglądzie organizowania w języku C++](../dotnet/overview-of-marshaling-in-cpp.md).

Jeśli spróbujesz zorganizować parę typów danych, które `marshal_as` nie są obsługiwane, wygeneruje błąd [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) w czasie kompilacji. Przeczytaj komunikat dostarczony z tym błędem, aby uzyskać więcej informacji. Błąd `C4996` może być generowany dla więcej niż tylko przestarzałe funkcje. Dwa warunki, które generują ten błąd, próbują zorganizować parę typów danych, `marshal_as` które nie są obsługiwane i próbuje użyć do konwersji, która wymaga kontekstu.

Biblioteka organizowania składa się z kilku plików nagłówkowych. Każda konwersja wymaga tylko jednego pliku, ale jeśli chcesz uwzględnić inne konwersje, możesz dołączyć dodatkowe pliki. Tabela `Marshaling Overview in C++` w wskazuje, który plik organizowania powinny być zawarte dla każdej konwersji.

### <a name="example"></a>Przykład

W tym przykładzie tworzy kontekst `System::String` do `const char *` organizowania z typu zmiennej do zmiennej. Przekonwertowane dane nie będą prawidłowe po wierszu, który usuwa kontekst.

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

---
title: interior_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
ms.openlocfilehash: affec6dcd88290b24a92cd9035a131baee38bcf1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214272"
---
# <a name="interior_ptr-ccli"></a>interior_ptr (C++/CLI)

*Wewnętrzny wskaźnik* deklaruje wskaźnik do wewnątrz typu referencyjnego, ale nie do samego obiektu. Wewnętrzny wskaźnik może wskazywać na dojście do odwołania, typ wartości, dojście do typu opakowanego, składową typu zarządzanego lub do elementu tablicy zarządzanej.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie do wszystkich środowisk uruchomieniowych).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie tylko do środowisko wykonawcze systemu Windows).

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Poniższy przykład składni ilustruje wewnętrzny wskaźnik.

### <a name="syntax"></a>Składnia

```cpp
cli::interior_ptr<cv_qualifier type> var = &initializer;
```

### <a name="parameters"></a>Parametry

*cv_qualifier*<br/>
**`const`** lub **`volatile`** kwalifikatory.

*Wprowadź*<br/>
Typ *inicjatora*.

*funkcję*<br/>
Nazwa zmiennej **interior_ptr** .

*skład*<br/>
Składową typu referencyjnego, elementu tablicy zarządzanej lub dowolnego innego obiektu, który można przypisać do wskaźnika natywnego.

### <a name="remarks"></a>Uwagi

Natywny wskaźnik nie może śledzić elementu, ponieważ jego lokalizacja zmienia się w zarządzanym stosie, co wynika z przenoszonej instancji obiektu modułu zbierającego elementy bezużyteczne. Aby wskaźnik prawidłowo odwoływał się do wystąpienia, środowisko uruchomieniowe musi zaktualizować wskaźnik do nowo położeniu obiektu.

**Interior_ptr** reprezentuje nadzbiór funkcji wskaźnika natywnego.  W związku z tym wszystkie elementy, które mogą być przypisane do wskaźnika natywnego, można także przypisać do **interior_ptr**.  Wewnętrzny wskaźnik jest dozwolony do wykonywania tego samego zestawu operacji jako wskaźników natywnych, w tym porównania i arytmetycznego wskaźnika.

Wewnętrzny wskaźnik można zadeklarować tylko na stosie.  Wewnętrzny wskaźnik nie może być zadeklarowany jako element członkowski klasy.

Ponieważ wewnętrzne wskaźniki istnieją tylko na stosie, pobranie adresu wskaźnika wewnętrznego daje niezarządzany wskaźnik.

**interior_ptr** ma niejawną konwersję na **`bool`** , która umożliwia korzystanie z instrukcji warunkowych.

Aby uzyskać informacje na temat sposobu deklarowania wewnętrznego wskaźnika, który wskazuje na obiekt, którego nie można przenieść na stertie zebranych elementów bezużytecznych, zobacz [pin_ptr](pin-ptr-cpp-cli.md).

**interior_ptr** znajduje się w przestrzeni nazw interfejsu wiersza polecenia.  Aby uzyskać więcej informacji [, zobacz przestrzenie nazw platform, Default i CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md) .

Aby uzyskać więcej informacji na temat wewnętrznych wskaźników, zobacz.

- [Poradnik: Deklarowanie wewnętrznych wskaźników i zarządzanych tablic oraz posługiwanie się nimi (C++/CLI)](how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)

- [Instrukcje: deklarowanie typów wartości za pomocą słowa kluczowego interior_ptr (C++/CLI)](how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)

- [Poradnik: Funkcje przeładowania z wewnętrznymi i natywnymi wskaźnikami (C++/CLI)](how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)

- [Poradnik: Deklarowanie wewnętrznych wskaźników za pomocą słowa kluczowego const (C++/CLI)](how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład pokazuje sposób deklarowania i używania wewnętrznego wskaźnika w typie referencyjnym.

```cpp
// interior_ptr.cpp
// compile with: /clr
using namespace System;

ref class MyClass {
public:
   int data;
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;
   h_MyClass->data = 1;
   Console::WriteLine(h_MyClass->data);

   interior_ptr<int> p = &(h_MyClass->data);
   *p = 2;
   Console::WriteLine(h_MyClass->data);

   // alternatively
   interior_ptr<MyClass ^> p2 = &h_MyClass;
   (*p2)->data = 3;
   Console::WriteLine((*p2)->data);
}
```

```Output
1
2
3
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)

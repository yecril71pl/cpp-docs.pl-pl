---
title: pin_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
ms.openlocfilehash: 9a9144229b75c09a892ddbf5bd592e67c7c2b6d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230561"
---
# <a name="pin_ptr-ccli"></a>pin_ptr (C++/CLI)

Deklaruje *przypinany wskaźnik*, który jest używany tylko w środowisku uruchomieniowym języka wspólnego.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie do wszystkich środowisk uruchomieniowych).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

(Ta funkcja języka nie jest obsługiwana w środowisko wykonawcze systemu Windows).

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

*Przypinany wskaźnik* jest wskaźnikiem wnętrza, który uniemożliwia przechodzenie obiektu na stosie zebranych elementów bezużytecznych. Oznacza to, że wartość przypinanego wskaźnika nie jest zmieniana przez środowisko uruchomieniowe języka wspólnego. Jest to wymagane, gdy przekazujesz adres zarządzanej klasy do niezarządzanej funkcji, tak aby adres nie był nieoczekiwanie zmieniany podczas rozpoznawania wywołania funkcji niezarządzanej.

### <a name="syntax"></a>Składnia

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>Parametry

*cv_qualifier*<br/>
**`const`** lub **`volatile`** kwalifikatory. Domyślnie przypinany jest wskaźnik **`volatile`** . Jest on nadmiarowy, ale nie jest błędem, aby zadeklarować przypinany wskaźnik **`volatile`** .

*Wprowadź*<br/>
Typ *inicjatora*.

*funkcję*<br/>
Nazwa zmiennej **pin_ptr** .

*skład*<br/>
Składową typu referencyjnego, elementu tablicy zarządzanej lub dowolnego innego obiektu, który można przypisać do wskaźnika natywnego.

### <a name="remarks"></a>Uwagi

**Pin_ptr** reprezentuje nadzbiór funkcji wskaźnika natywnego. W związku z tym wszystkie elementy, które mogą być przypisane do wskaźnika natywnego, można także przypisać do **pin_ptr**. Wewnętrzny wskaźnik jest dozwolony do wykonywania tego samego zestawu operacji jako wskaźników natywnych, w tym porównania i arytmetycznego wskaźnika.

Obiekt lub obiekt podrzędny klasy zarządzanej może być przypięty, w tym przypadku środowisko uruchomieniowe języka wspólnego nie przesunie go podczas odzyskiwania pamięci. Głównym zastosowaniem tego elementu jest przekazanie wskaźnika do danych zarządzanych jako rzeczywisty parametr wywołania funkcji niezarządzanej. Podczas cyklu zbierania środowisko uruchomieniowe sprawdzi metadane utworzone dla przypinanego wskaźnika i nie przeniesie elementu, do którego wskazuje.

Przypinanie obiektu także przypina jego pola wartości; oznacza to, że pola typu pierwotnego lub wartościowego. Jednak pola zadeklarowane przez uchwyt śledzenia ( `%` ) nie są przypięte.

Przypinanie obiektu podrzędnego zdefiniowanego w obiekcie zarządzanym ma wpływ na przypinanie całego obiektu.

Jeśli przypięty wskaźnik zostanie ponownie przypisany do punktu do nowej wartości, wskazane poprzednie wystąpienie nie jest już uważane za przypięty.

Obiekt jest przypięty tylko wtedy, gdy **pin_ptr** do niego. Obiekt nie jest już przypięty, gdy jego przypinany wskaźnik wykracza poza zakres lub jest ustawiony na [nullptr](nullptr-cpp-component-extensions.md). Gdy **pin_ptr** wykracza poza zakres, obiekt, który został przypięty, można przenieść do sterty przez moduł wyrzucania elementów bezużytecznych. Wszelkie macierzyste wskaźniki, które nadal wskazują obiekt, nie będą aktualizowane, a cofnięcie odwołania jednego z nich może spowodować nieodwracalny wyjątek.

Jeśli nie ma żadnego przypiętego wskaźnika do obiektu (wszystkie możliwe do przypięcia wskaźniki wykraczają poza zakres, zostały ponownie przypisane do punktu do innych obiektów lub zostały przypisane [nullptr](nullptr-cpp-component-extensions.md)), obiekt nie jest przypięty.

Przypinający wskaźnik może wskazywać na dojście odwołania, typ wartości lub uchwyt typu opakowanego, element członkowski typu zarządzanego lub element tablicy zarządzanej. Nie może wskazywać typu referencyjnego.

Pobieranie adresu **pin_ptr** , który wskazuje na obiekt macierzysty powoduje niezdefiniowane zachowanie.

Przypinanie wskaźników można zadeklarować tylko jako niestatyczne zmienne lokalne na stosie.

Nie można używać wskaźników przypinania jako:

- parametry funkcji

- zwracany typ funkcji

- element członkowski klasy

- docelowy typ rzutowania.

**pin_ptr** znajduje się w `cli` przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [przestrzenie nazw platform, Default i CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md).

Aby uzyskać więcej informacji o wewnętrznych wskaźnikach, zobacz [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md).

Aby uzyskać więcej informacji na temat przypinania wskaźników, zobacz [How to: Przypinanie wskaźników i tablic](how-to-pin-pointers-and-arrays.md) oraz [instrukcje: deklarowanie przypinania wskaźników i typów wartości](how-to-declare-pinning-pointers-and-value-types.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład używa **pin_ptr** , aby ograniczyć pozycję pierwszego elementu tablicy.

```cpp
// pin_ptr_1.cpp
// compile with: /clr
using namespace System;
#define SIZE 10

#pragma unmanaged
// native function that initializes an array
void native_function(int* p) {
   for(int i = 0 ; i < 10 ; i++)
    p[i] = i;
}
#pragma managed

public ref class A {
private:
   array<int>^ arr;   // CLR integer array

public:
   A() {
      arr = gcnew array<int>(SIZE);
   }

   void load() {
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr
   int* np = p;   // pointer to the first element in arr
   native_function(np);   // pass pointer to native function
   }

   int sum() {
      int total = 0;
      for (int i = 0 ; i < SIZE ; i++)
         total += arr[i];
      return total;
   }
};

int main() {
   A^ a = gcnew A;
   a->load();   // initialize managed array using the native function
   Console::WriteLine(a->sum());
}
```

```Output
45
```

Poniższy przykład pokazuje, że wewnętrzny wskaźnik można przekonwertować na przypięty wskaźnik, a zwracany typ operatora address-of ( `&` ) jest wskaźnikiem wewnętrznym, gdy operand znajduje się na stercie zarządzanym.

```cpp
// pin_ptr_2.cpp
// compile with: /clr
using namespace System;

ref struct G {
   G() : i(1) {}
   int i;
};

ref struct H {
   H() : j(2) {}
   int j;
};

int main() {
   G ^ g = gcnew G;   // g is a whole reference object pointer
   H ^ h = gcnew H;

   interior_ptr<int> l = &(g->i);   // l is interior pointer

   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer

   k = l;   // ok
   Console::WriteLine(*k);
};
```

```Output
1
```

Poniższy przykład pokazuje, że przypinany wskaźnik może być rzutowany na inny typ.

```cpp
// pin_ptr_3.cpp
// compile with: /clr
using namespace System;

ref class ManagedType {
public:
   int i;
};

int main() {
   ManagedType ^mt = gcnew ManagedType;
   pin_ptr<int> pt = &mt->i;
   *pt = 8;
   Console::WriteLine(mt->i);

   char *pc = ( char* ) pt;
   *pc = 255;
   Console::WriteLine(mt->i);
}
```

```Output
8
255
```

---
title: Właściwość (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- property_cpp
- property
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
ms.openlocfilehash: 4a05f9cf8cbec9644254d14873a3259f12b33aed
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509714"
---
# <a name="property--ccli-and-ccx"></a>Właściwość (C++/CLI i C++/CX)

Deklaruje *Właściwość*, która jest funkcją składową, która zachowuje się i jest dostępna, jak element członkowski danych lub element tablicy.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

Można zadeklarować jeden z następujących typów właściwości.

*Właściwość prosta*<br/>
Domyślnie program tworzy *metodę dostępu set* , która przypisuje wartość właściwości, *metodę dostępu get* , która pobiera wartość właściwości, oraz prywatny element członkowski danych wygenerowany przez kompilator zawierający wartość właściwości.

*blok właściwości*<br/>
Służy do tworzenia zdefiniowanych przez użytkownika metod dostępu get i/lub Set. Właściwość jest odczytywana/zapisu, jeśli są zdefiniowane zarówno Akcesory Get, jak i Set, tylko do odczytu, jeśli jest zdefiniowana tylko metoda dostępu get i tylko do zapisu, jeśli jest zdefiniowana tylko metoda dostępu set.

Należy jawnie zadeklarować składową danych, aby zawierała wartość właściwości.

*Właściwość indeksowana*<br/>
Blok właściwości, którego można użyć, aby pobrać i ustawić wartość właściwości, która jest określona przez jeden lub więcej indeksów.

Można utworzyć indeksowaną właściwość, która ma zdefiniowaną przez użytkownika nazwę właściwości lub *domyślną* nazwę właściwości. Nazwa domyślnej właściwości indeksu jest nazwą klasy, w której właściwość jest zdefiniowana. Aby zadeklarować właściwość domyślną, określ słowo kluczowe **default** zamiast nazwy właściwości.

Należy jawnie zadeklarować składową danych, aby zawierała wartość właściwości. Dla właściwości indeksowanej element członkowski danych jest zwykle tablicą lub kolekcją.

### <a name="syntax"></a>Składnia

```cpp
property type property_name;

property type property_name {
   access-modifier type get() inheritance-modifier {property_body};
   access-modifier void set(type value) inheritance-modifier {property_body};
}

property type property_name[index_list] {
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}

property type default[index_list] {
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}
```

### <a name="parameters"></a>Parametry

*type*<br/>
Typ danych wartości właściwości i w związku z tym właściwością.

*property_name*<br/>
Nazwa właściwości.

*Modyfikator dostępu*<br/>
Kwalifikator dostępu. Prawidłowe kwalifikatory są **statyczne** i **wirtualne**.

Metody dostępu get lub set nie muszą zgadzać się z kwalifikatorem wirtualnym, ale muszą wyrazić zgodę na kwalifikator **statyczny** .

*inheritance-modifier*<br/>
Kwalifikator dziedziczenia. Prawidłowe kwalifikatory są **abstrakcyjne** i **zapieczętowane**.

*index_list*<br/>
Rozdzielana przecinkami lista co najmniej jednego indeksu. Każdy indeks składa się z typu indeksu i opcjonalnego identyfikatora, który może być używany w treści metody właściwości.

*value*<br/>
Wartość, która ma zostać przypisana do właściwości w operacji zestawu lub pobierana w operacji pobierania.

*property_body*<br/>
Treść metody właściwości zestawu lub get. *Property_body* może używać *index_list* do uzyskiwania dostępu do elementu członkowskiego danych właściwości bazowej lub jako parametrów w przetwarzaniu zdefiniowanym przez użytkownika.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Aby uzyskać więcej informacji, zobacz [właściwościC++(/CX)](../cppcx/properties-c-cx.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="syntax"></a>Składnia

```cpp
modifier property type property_name;

modifier property type property_name {
   modifier void set(type);
   modifier type get();
}
modifier property type property_name[index-list, value] {
   modifier void set(index-list, value);
   modifier type get(index-list);

modifier property type default[index];
}
```

### <a name="parameters"></a>Parametry

*modyfikator*<br/>
Modyfikator, który może być używany w deklaracji właściwości lub metodzie dostępu get/set. Możliwe wartości są **statyczne** i **wirtualne**.

*type*<br/>
Typ wartości reprezentowanej przez właściwość.

*property_name*<br/>
Parametry dla metody podniesienia; musi być zgodna z podpisem delegata.

*index_list*<br/>
Rozdzielana przecinkami lista co najmniej jednego indeksu, określona w nawiasach kwadratowych (Operator indeksu dolnego ([])). Dla każdego indeksu należy określić typ i opcjonalnie identyfikator, który może być używany w treści metody właściwości.

### <a name="remarks"></a>Uwagi

Pierwszy przykład składni pokazuje prostą *Właściwość*, która niejawnie deklaruje zarówno `set` metodę `get` , jak i. Kompilator automatycznie tworzy pole prywatne do przechowywania wartości właściwości.

Druga Przykładowa składnia przedstawia *blok właściwości*, który jawnie deklaruje zarówno `set` metodę, jak i. `get`

Trzecia Przykładowa składnia przedstawia zdefiniowaną przez klienta *Właściwość indeksu*. Właściwość index przyjmuje parametry oprócz wartości, która ma być ustawiona lub pobrana. Należy określić nazwę właściwości. W `set` przeciwieństwie do prostej właściwości, metody i `get` /lub właściwości indeksu muszą być jawnie zdefiniowane i należy określić nazwę dla właściwości.

Czwarta składnia przykładu przedstawia Właściwość *domyślną* , która zapewnia podobny do tablicy dostęp do wystąpienia typu. Słowo kluczowe, **default**, służy tylko do określenia właściwości domyślnej. Nazwa właściwości domyślnej jest nazwą typu, w którym właściwość jest zdefiniowana.

Słowo kluczowe **Property** może występować w klasie, interfejsie lub typie wartości. Właściwość może mieć funkcję get (tylko do odczytu), funkcję Set (tylko do zapisu) lub obie (odczyt i zapis).

Nazwa właściwości nie może być zgodna z nazwą klasy zarządzanej, która ją zawiera. Zwracany typ funkcji pobierającej musi być zgodny z typem ostatniego parametru odpowiadającej funkcji setter.

Do kodu klienta właściwość ma wygląd zwykłego elementu członkowskiego danych i może być zapisywana lub odczytywana przy użyciu tej samej składni co element członkowski danych.

Metody get i set nie muszą zgadzać się z modyfikatorem wirtualnym.

Dostępność metody get i set może się różnić.

Definicja metody właściwości może występować poza treścią klasy, podobnie jak zwykła Metoda.

Metoda get i Set dla właściwości wyraża zgodę na modyfikator statyczny .

Właściwość jest skalarna, jeśli jej metody get i Set pasują do następującego opisu:

- Metoda get nie ma parametrów i ma zwracany typ `T`.

- Metoda Set ma parametr typu `T`, a zwracany typ **void**.

Zakres o takim samym identyfikatorze powinien zawierać tylko jedną właściwość skalarną. Właściwości skalarne nie mogą być przeciążone.

Gdy element członkowski danych właściwości jest zadeklarowany, kompilator wprowadza element członkowski danych — czasami określany jako "magazyn zapasowy" — w klasie. Jednak nazwa elementu członkowskiego danych jest w postaci, w której nie można odwołać się do elementu członkowskiego w źródle, tak jakby był to rzeczywisty element członkowski danych klasy zawierającej. Użyj Ildasm. exe, aby wyświetlić metadane dla danego typu i zobaczyć nazwę wygenerowaną przez kompilator dla magazynu zapasowego właściwości.

Różne ułatwienia dostępu są dozwolone dla metod dostępu w bloku właściwości.  Oznacza to, że Metoda set może być publiczna, a metoda Get może być prywatna.  Jednak jest to błąd metody dostępu, aby mieć mniej restrykcyjny dostęp niż to, co znajduje się w deklaracji samej właściwości.

**Właściwość** to kontekstowe słowo kluczowe.  Aby uzyskać więcej informacji, zobacz [kontekstowe słowa kluczowe](context-sensitive-keywords-cpp-component-extensions.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

### <a name="examples"></a>Przykłady

W poniższym przykładzie pokazano deklarację i użycie elementu członkowskiego danych właściwości i bloku właściwości.  Pokazuje również, że metoda dostępu do właściwości może być zdefiniowana poza klasą.

```cpp
// mcppv2_property.cpp
// compile with: /clr
using namespace System;
public ref class C {
   int MyInt;
public:

   // property data member
   property String ^ Simple_Property;

   // property block
   property int Property_Block {

      int get();

      void set(int value) {
         MyInt = value;
      }
   }
};

int C::Property_Block::get() {
   return MyInt;
}

int main() {
   C ^ MyC = gcnew C();
   MyC->Simple_Property = "test";
   Console::WriteLine(MyC->Simple_Property);

   MyC->Property_Block = 21;
   Console::WriteLine(MyC->Property_Block);
}
```

```Output
test

21
```

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)
---
title: Kontenery STL/CLR
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
ms.openlocfilehash: dc2e5ce3263c61839a1ba434ab0d2a39e6a9078f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774545"
---
# <a name="stlclr-containers"></a>Kontenery STL/CLR

Biblioteki STL/CLR składa się z kontenerów, które są podobne do tych znajdują się w standardowej biblioteki języka C++, ale działa w środowisku zarządzanym programu .NET Framework. Go nie stale aktualizowane przy użyciu rzeczywistego standardowej biblioteki języka C++ i jest zachowywana na potrzeby obsługi starszej wersji.

Ten dokument zawiera omówienie kontenery w STL/CLR, takie jak wymagania dotyczące elementów kontenera, typów elementów, że można wstawiać do kontenerów i własność problemy z elementami w kontenerach. Ile to możliwe, są wymienione różnice między natywny standardowej biblioteki języka C++ i STL/CLR.

## <a name="requirements-for-container-elements"></a>Wymagania dotyczące elementów kontenera

Wszystkie elementy wstawione do kontenerów STL/CLR musi przestrzegać określonych wytycznych. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące elementów kontenera STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md).

## <a name="valid-container-elements"></a>Prawidłowy kontener elementów

Kontenery STL/CLR mogą zawierać jeden z dwóch typów elementów:

- Obsługuje na typy odwołań.

- Typy odwołań.

- Typy wartości rozpakowany.

Spakowane typy wartości nie można wstawić do dowolnego kontenery STL/CLR.

### <a name="handles-to-reference-types"></a>Uchwyty na typy odwołań

Dojście do typu referencyjnego można wstawić do kontenera STL/CLR. Dojście w języku C++, przeznaczonego dla CLR jest porównywalna ze wskaźnikiem w natywnym kodzie C++. Aby uzyskać więcej informacji, zobacz [Operator uchwytu do obiektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md).

#### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak wstawić dojścia do obiektu pracowników na [cliext::set](../dotnet/set-stl-clr.md).

```
// cliext_container_valid_reference_handle.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee^ empl1419 = gcnew Employee();
    empl1419->Name = L"Darin Lockert";
    empl1419->EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee^>^ emplSet = gcnew set<Employee^>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="reference-types"></a>Typy odwołań

Istnieje również możliwość Wstawianie kontenera STL/CLR typu odwołania (zamiast dojścia do typu odwołania). Główną różnicą jest to, że po usunięciu kontenera typu referencyjnego destruktor jest wywoływany dla wszystkich elementów w tym kontenerze. W kontenerze uchwytów na typy odwołań nie będzie wywoływana destruktory dla tych elementów.

#### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak wstawianie obiektu pracowników do `cliext::set`.

```
// cliext_container_valid_reference.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="unboxed-value-types"></a>Typy wartości rozpakowany

Można także wstawić rozpakowany typ wartościowy do kontenera STL/CLR. Rozpakowany typ wartościowy jest typem wartości, która nie została *opakowany* do typu odwołania.

Element typu wartości może być jednym z typów wartości standardowej, takich jak `int`, lub może być typem wartości zdefiniowanej przez użytkownika, takie jak `value class`. Aby uzyskać więcej informacji, zobacz [klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md)

#### <a name="example"></a>Przykład

Poniższy przykład modyfikuje pierwszego przykładu, wprowadzając pracowników klasy typu wartości. Ten typ wartości zostanie wstawiony na `cliext::set` podobnie jak w pierwszym przykładzie.

```
// cliext_container_valid_valuetype.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

value class Employee
{
public:
    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl.EmployeeNumber, empl.Name);
    }

    return 0;
}
```

Jeśli użytkownik podejmie próbę wstawienia dojścia do typu wartości w kontenerze, [błąd kompilatora C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md) jest generowany.

### <a name="performance-and-memory-implications"></a>Wydajność i skutki pamięci

Podczas ustalania, czy należy odwoływać się do typów lub wartości jako elementy kontenera za pomocą uchwytów, należy wziąć pod uwagę kilka czynników. Jeśli zdecydujesz się używać typów wartości, należy pamiętać, że kopię elementu jest nawiązywane za każdym razem, gdy element jest wstawiany do kontenera. W przypadku małych obiektów to nie powinna być problemem, ale w przypadku dużych obiektów, jest wstawiany może to spowodować obniżenie wydajności. Ponadto jeśli używasz typów wartości, jest niemożliwe do przechowywania jeden element w wielu kontenerach w tym samym czasie, ponieważ każdy kontener będzie mieć własną kopię elementu.

Jeśli zdecydujesz się na typy odwołań w zamian za pomocą uchwytów wydajności może zwiększyć, ponieważ nie jest to niezbędne do zapewnienia kopię elementu, gdy znajduje się w kontenerze. Ponadto w odróżnieniu od z typami wartości tego samego elementu w może istnieć wiele kontenerów. Jednak jeśli użytkownik zdecyduje się za pomocą uchwytów, możesz należy uważać, aby upewnij się, że uchwyt jest prawidłowy oraz że odwołuje się do obiektu nie został usunięty gdzie indziej w taki sposób, w programie.

## <a name="ownership-issues-with-containers"></a>Kwestie własnościowe z kontenerami

Kontenery w STL/CLR działają na semantyce wartość. Za każdym razem, gdy należy wstawić element do kontenera, jest wstawiany kopię tego elementu. Jeśli chcesz pobrać semantyka odwołań podobne, można wstawić dojścia do obiektu, a nie samego obiektu.

Podczas wywołania niezaszyfrowane lub erase — metoda kontenera obiektów dojście do obiektów, które dotyczą uchwyty nie są zwalniane z pamięci. Użytkownik musi jawnie usunąć obiekt albo, ponieważ obiekty te znajdują się na zarządzanym stosie, Zezwalaj na moduł odśmiecania pamięci zwolnić pamięć, gdy ustali, że obiekt jest już używana.

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

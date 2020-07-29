---
title: Kontenery STL/CLR
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
ms.openlocfilehash: 04ba56bf4f134ac5e9b906f7f84563c00ffe1b96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214870"
---
# <a name="stlclr-containers"></a>Kontenery STL/CLR

Biblioteka STL/CLR zawiera kontenery podobne do tych znajdujących się w standardowej bibliotece języka C++, ale działa w środowisku zarządzanym .NET Framework. Nie jest on aktualizowany za pomocą rzeczywistej standardowej biblioteki C++ i jest obsługiwany dla starszej obsługi.

Ten dokument zawiera omówienie kontenerów w STL/CLR, takich jak wymagania dotyczące elementów kontenera, typy elementów, które można wstawić do kontenerów, i problemy własności z elementami w kontenerach. W razie potrzeby różnice między natywną biblioteką standardu C++ i STL/CLR są wymienione.

## <a name="requirements-for-container-elements"></a>Wymagania dotyczące elementów kontenera

Wszystkie elementy wstawione do kontenerów STL/CLR muszą przestrzegać pewnych wytycznych. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące elementów kontenera STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md).

## <a name="valid-container-elements"></a>Prawidłowe elementy kontenera

Kontenery STL/CLR mogą zawierać jeden z dwóch typów elementów:

- Obsługuje typy odwołań.

- Typy odwołań.

- Nieopakowane typy wartości.

Nie można wstawić opakowanych typów wartości do żadnego kontenera STL/CLR.

### <a name="handles-to-reference-types"></a>Uchwyty do typów referencyjnych

Dojście do typu odwołania można wstawić do kontenera STL/CLR. Dojście w języku C++, które jest celem środowiska CLR jest analogiczne do wskaźnika w natywnym języku C++. Aby uzyskać więcej informacji, zobacz [uchwyt do operatora obiektu (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md).

#### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak wstawić uchwyt do obiektu Employee do elementu [cliext:: Set](../dotnet/set-stl-clr.md).

```cpp
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

Można również wstawić typ referencyjny (zamiast dojścia do typu referencyjnego) do kontenera STL/CLR. Główną różnicą jest to, że po usunięciu kontenera typów odwołań destruktor jest wywoływany dla wszystkich elementów wewnątrz tego kontenera. W kontenerze dojść do typów referencyjnych destruktory dla tych elementów nie będą wywoływane.

#### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak wstawić obiekt Employee do `cliext::set` .

```cpp
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

### <a name="unboxed-value-types"></a>Nieopakowane typy wartości

Możesz również wstawić nieopakowany typ wartości do kontenera STL/CLR. Nieopakowany typ wartości jest typem wartości, który nie został *opakowany* na typ referencyjny.

Element typu wartości może być jednym z standardowych typów wartości, takich jak **`int`** , lub może być typem wartości zdefiniowanym przez użytkownika, np **`value class`** .. Aby uzyskać więcej informacji, zobacz [klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md)

#### <a name="example"></a>Przykład

Poniższy przykład modyfikuje pierwszy przykład, tworząc klasę Employee jako typ wartości. Ten typ wartości jest następnie wstawiany do postaci `cliext::set` tak jak w pierwszym przykładzie.

```cpp
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

Jeśli podjęto próbę wstawienia dojścia do typu wartości do kontenera, generowany jest [błąd kompilatora C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md) .

### <a name="performance-and-memory-implications"></a>Wpływ na wydajność i pamięć

Należy wziąć pod uwagę kilka czynników przy określaniu, czy należy używać dojść do typów referencyjnych lub typów wartości jako elementów kontenera. Jeśli zdecydujesz się używać typów wartościowych, pamiętaj, że kopia elementu jest wykonywana za każdym razem, gdy element zostanie wstawiony do kontenera. W przypadku małych obiektów nie powinno to być problemem, ale jeśli wstawiane obiekty są duże, może to mieć wpływ na wydajność. Ponadto, jeśli używasz typów wartościowych, nie jest możliwe przechowywanie jednego elementu w wielu kontenerach w tym samym czasie, ponieważ każdy kontener będzie miał własną kopię elementu.

Jeśli zdecydujesz się użyć dojść do typów referencyjnych, wydajność może wzrosnąć, ponieważ nie jest konieczne tworzenie kopii elementu, gdy zostanie wstawiony do kontenera. Ponadto, w przeciwieństwie do typów wartości, ten sam element może istnieć w wielu kontenerach. Jeśli jednak zdecydujesz się używać uchwytów, musisz mieć pewność, że dojście jest prawidłowe i że obiekt, do którego się odwołuje, nie został usunięty w innym miejscu programu.

## <a name="ownership-issues-with-containers"></a>Problemy z własnością przy użyciu kontenerów

Kontenery w STL/CLR pracują z semantyką wartości. Za każdym razem, gdy wstawisz element do kontenera, zostanie wstawiona kopia tego elementu. Jeśli chcesz uzyskać semantykę przypominającą odwołanie, możesz wstawić uchwyt do obiektu, a nie sam obiekt.

Gdy wywoływana jest metoda Clear lub Erase kontenera obiektów dojścia, obiekty, do których odwołuje się dojścia, nie są zwalniane z pamięci. Należy jawnie usunąć obiekt lub, ponieważ te obiekty znajdują się na stercie zarządzanym, zezwolić modułowi wyrzucania elementów bezużytecznych na zwolnienie pamięci po ustaleniu, że obiekt nie jest już używany.

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)

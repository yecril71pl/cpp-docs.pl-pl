---
title: Kontenery STL/CLR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ce6a2f096e5ee24716fcffd89411ffdf926a59aa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33173141"
---
# <a name="stlclr-containers"></a>Kontenery STL/CLR
Biblioteka STL/CLR ma tego samego kontenerów, które znajdują się w standardowa biblioteka C++, ale działa w środowisku zarządzanym programu .NET Framework. Jeśli już znasz standardowa biblioteka C++, STL/CLR jest najlepszy sposób, aby nadal używać umiejętności, które został już utworzony podczas uaktualniania kodu docelowe środowisko uruchomieniowe języka wspólnego (CLR).  
  
 Ten dokument zawiera omówienie kontenery STL/CLR, takich jak wymagania dotyczące elementów kontenera, typy elementów można wstawiać do kontenerów, czy własność problemy związane z elementów w kontenerach. Ewentualnie różnice między natywnych standardowa biblioteka C++ i STL/CLR są wymienione.  
  
## <a name="requirements-for-container-elements"></a>Wymagania dotyczące elementów kontenera  
 Wszystkie elementy wstawione do kontenerów standardowa biblioteka C++ muszą przestrzegać określonych wytycznych. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące elementów kontenera STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md).  
  
## <a name="valid-container-elements"></a>Elementów prawidłową kontenera  
 Kontenery STL/CLR mogą zawierać jedną z dwóch typów elementów:  
  
-   Uchwytów na typy referencyjne.  
  
-   Typy referencyjne.  
  
-   Typy wartości rozpakowany.  
  
 Spakowane typy wartości nie można wstawić do dowolnego kontenery STL/CLR.  
  
### <a name="handles-to-reference-types"></a>Dojścia do typu odwołania  
 Dojście do typu referencyjnego można wstawić do kontenera STL/CLR. Dojście w języku C++ przeznaczonego dla CLR jest odpowiednikiem wskaźnika w natywnym kodzie C++. Aby uzyskać więcej informacji, zobacz [Operator uchwytu do obiektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md).  
  
#### <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób Wstaw uchwyt do obiektu pracowników do [cliext::set](../dotnet/set-stl-clr.md).  
  
```  
// cliext_container_valid_reference_handle.cpp  
// compile with: /clr  
  
#include <cliext/set>  
  
using namespace cliext;  
using namespace System;  
  
ref class Employee  
{  
public:  
    // C++ Standard Library containers might require a public constructor, so it  
    // is a good idea to define one.  
    Employee() :  
        name(nullptr),  
        employeeNumber(0) { }  
  
    // All C++ Standard Library containers require a public copy constructor.  
    Employee(const Employee% orig) :  
        name(orig.name),  
        employeeNumber(orig.employeeNumber) { }  
  
    // All C++ Standard Library containers require a public assignment operator.  
    Employee% operator=(const Employee% orig)  
    {  
        if (this != %orig)  
        {  
            name = orig.name;  
            employeeNumber = orig.employeeNumber;  
        }  
  
        return *this;  
    }  
  
    // All C++ Standard Library containers require a public destructor.  
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
 Istnieje również możliwość wstawiania typu odwołania (zamiast dojścia do typu odwołania) do kontenera STL/CLR. Główną różnicą jest to, że po usunięciu kontener typy referencyjne destruktor jest wywoływana dla wszystkich elementów w tym kontenerze. W kontenerze dojścia do typu odwołania nie będzie można wywołać destruktory dla tych elementów.  
  
#### <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wstawienia obiektu pracowników do `cliext::set`.  
  
```  
// cliext_container_valid_reference.cpp  
// compile with: /clr  
  
#include <cliext/set>  
  
using namespace cliext;  
using namespace System;  
  
ref class Employee  
{  
public:  
    // C++ Standard Library containers might require a public constructor, so it  
    // is a good idea to define one.  
    Employee() :  
        name(nullptr),  
        employeeNumber(0) { }  
  
    // All C++ Standard Library containers require a public copy constructor.  
    Employee(const Employee% orig) :  
        name(orig.name),  
        employeeNumber(orig.employeeNumber) { }  
  
    // All C++ Standard Library containers require a public assignment operator.  
    Employee% operator=(const Employee% orig)  
    {  
        if (this != %orig)  
        {  
            name = orig.name;  
            employeeNumber = orig.employeeNumber;  
        }  
  
        return *this;  
    }  
  
    // All C++ Standard Library containers require a public destructor.  
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
 Można również wstawić rozpakowany typ wartościowy do kontenera STL/CLR. Rozpakowany typ wartościowy jest typem wartości, która nie została *opakowany* do typu referencyjnego.  
  
 Element typu wartość może być jedną z Typy standardowe wartości, takich jak `int`, lub może być typem wartości zdefiniowanej przez użytkownika, takie jak `value class`. Aby uzyskać więcej informacji, zobacz [klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)  
  
#### <a name="example"></a>Przykład  
 Poniższy przykład modyfikuje pierwszym przykładzie przez pracownika klasy typu wartości. Tego typu wartość zostanie wstawiony na `cliext::set` tak jak w przypadku pierwszym przykładzie.  
  
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
  
 Przy próbie wstawienia dojścia do typu wartości do kontenera, [C3225 błąd kompilatora](../error-messages/compiler-errors-2/compiler-error-c3225.md) jest generowany.  
  
### <a name="performance-and-memory-implications"></a>Wydajność i efekty pamięci  
 Podczas ustalania, czy używać dojść do odwołania typy lub wartości jako elementy kontenera, należy wziąć pod uwagę kilka czynników. Jeśli zdecydujesz się używać typów wartości, należy pamiętać, że kopii elementu jest wykonywane przy każdym elementem zostaną wstawione do kontenera. W przypadku małych obiektów nie powinno to być spowodowane problemem, ale w przypadku dużych obiektów wstawiane może pogorszyć wydajność. Ponadto jeśli korzystasz z typów wartości, jest niemożliwe do przechowywania jeden element w wielu kontenerów w tym samym czasie, ponieważ każdego kontenera ma własną kopię elementu.  
  
 Jeśli zdecydujesz się na potrzeby typy referencyjne zamiast tego dojść, ponieważ nie można utworzyć kopii elementu, gdy znajduje się w kontenerze może zwiększyć wydajność. Ponadto w odróżnieniu od z typami wartości tego samego elementu może istnieć w wielu kontenerów. Jednak jeśli zdecydujesz się używać dojść, użytkownik musi zajmie się aby upewnić się, że dojście jest prawidłowa i czy odwołuje się do obiektu nie została usunięta w innym miejscu w taki sposób, w programie.  
  
## <a name="ownership-issues-with-containers"></a>Własność problemy z kontenerami  
 Kontenery STL/CLR działają w semantyki wartości. Za każdym razem, gdy wstawieniu elementu do kontenera, jest wstawiany kopię tego elementu. Jeśli chcesz pobrać semantykę odwołania przypominającej można wstawić dojścia do obiektu, a nie samego obiektu.  
  
 Podczas wywołania wyczyść lub erase — metoda kontenera obiektów dojścia obiektów, które dotyczą uchwyty nie są zwalniane z pamięci. Należy jawnie usunąć obiekt, lub, ponieważ obiekty te znajdują się na stercie zarządzanej Zezwalaj moduł zbierający elementy bezużyteczne zwolnić pamięć, gdy ustali, że obiekt jest już używana.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
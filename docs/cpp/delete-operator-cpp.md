---
title: delete — Operator (C++)
ms.date: 08/12/2019
f1_keywords:
- delete_cpp
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
ms.openlocfilehash: 3b00bf78d286ba530dee85240236a2a9ea171113
ms.sourcegitcommit: a146b169664c001406a0cccc7fbda1b8d7be5078
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2019
ms.locfileid: "69024644"
---
# <a name="delete-operator-c"></a>delete — Operator (C++)

Zwalnia blok pamięci.

## <a name="syntax"></a>Składnia

> [`::`] `delete` *wyrażenie cast*\
> [`::`] `delete []` *wyrażenie cast*

## <a name="remarks"></a>Uwagi

Argument *cast-expression* musi być wskaźnikiem do bloku pamięci, który został wcześniej przydzielony dla obiektu utworzonego za pomocą [operatora new](../cpp/new-operator-cpp.md). Operator **delete** ma wynik typu **void** i w związku z tym nie zwraca wartości. Na przykład:

```cpp
CDialog* MyDialog = new CDialog;
// use MyDialog
delete MyDialog;
```

Użycie polecenia **delete** na wskaźniku do obiektu, który nie jest przydzielony przy użyciu funkcji **New** , daje nieprzewidywalne wyniki. Można jednak użyć **delete** na wskaźniku o wartości 0. Dzięki temu, gdy **nowe** zwraca wartość 0 w przypadku niepowodzenia, usunięcie wyniku nieudanej **nowej** operacji jest nieszkodliwe. Aby uzyskać więcej informacji, zobacz [Operatory New i DELETE](../cpp/new-and-delete-operators.md).

Operatorów **New** i **delete** można także używać w przypadku typów wbudowanych, w tym tablic. Jeśli `pointer` odwołuje się do tablicy, umieść puste nawiasy ( `pointer``[]`) przed:

```cpp
int* set = new int[100];
//use set[]
delete [] set;
```

Użycie operatora **delete** na obiekcie powoduje cofnięcie przydziału pamięci. Program, który odwołuje się do wskaźnika po usunięciu obiektu, może mieć nieprzewidywalne wyniki lub awarię.

Gdy **delete** jest używany do cofnięcia alokacji pamięci C++ dla obiektu klasy, destruktor obiektu jest wywoływana przed cofnięciem alokacji pamięci obiektu (Jeśli obiekt ma destruktor).

Jeśli argument operacji operatora **delete** jest modyfikowalną wartością l, jej wartość jest niezdefiniowana po usunięciu obiektu.

Jeśli określono opcję kompilatora [/SDL (Włącz dodatkowe kontrole zabezpieczeń)](/cpp/build/reference/sdl-enable-additional-security-checks) , operand do operatora **delete** jest ustawiony na nieprawidłową wartość po usunięciu obiektu.

## <a name="using-delete"></a>Używanie opcji usuwania

Istnieją dwie warianty składni dla [operatora delete](../cpp/delete-operator-cpp.md): jeden dla pojedynczych obiektów i drugi dla tablic obiektów. Poniższy fragment kodu przedstawia różnice między nimi:

```cpp
// expre_Using_delete.cpp
struct UDType
{
};

int main()
{
   // Allocate a user-defined object, UDObject, and an object
   //  of type double on the free store using the
   //  new operator.
   UDType *UDObject = new UDType;
   double *dObject = new double;
   // Delete the two objects.
   delete UDObject;
   delete dObject;
   // Allocate an array of user-defined objects on the
   // free store using the new operator.
   UDType (*UDArr)[7] = new UDType[5][7];
   // Use the array syntax to delete the array of objects.
   delete [] UDArr;
}
```

Dwa następujące przypadki generują niezdefiniowane wyniki: przy użyciu formy tablicowej Delete`delete []`() dla obiektu oraz przy użyciu formy usuwania z tablicy.

## <a name="example"></a>Przykład

Przykłady użycia polecenia **delete**można znaleźć w temacie [New Operator](../cpp/new-operator-cpp.md).

## <a name="how-delete-works"></a>Jak działa usuwanie

Operator delete wywołuje **operator funkcji Delete**.

Dla obiektów, które nie są typu klasy ([Klasa](../cpp/class-cpp.md), [Struktura](../cpp/struct-cpp.md)lub [Unia](../cpp/unions.md)), jest wywoływany operator usuwania globalnego. W przypadku obiektów typu klasy nazwa funkcji cofania alokacji jest rozpoznawana w zakresie globalnym, jeśli wyrażenie delete zaczyna się od jednoargumentowego operatora rozpoznawania zakresu`::`(). W przeciwnym razie operator delete wywołuje destruktor dla obiektu przed cofnięciem alokacji pamięci (jeśli wskaźnik nie ma wartości null). Operator delete można zdefiniować dla poszczególnych klas. Jeśli nie ma takiej definicji dla danej klasy, zostanie wywołany globalny operator delete. Jeśli wyrażenie delete służy do cofnięcia alokacji obiektu klasy, którego typ statyczny ma destruktor wirtualny, funkcja cofania alokacji jest rozwiązywana przez destruktor wirtualny typu dynamicznego obiektu.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)\
[Keywords](../cpp/keywords-cpp.md)\
[new i delete, operatory](../cpp/new-and-delete-operators.md)
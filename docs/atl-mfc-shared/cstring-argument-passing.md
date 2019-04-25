---
title: Cstring — przekazywanie argumentów
ms.date: 11/04/2016
helpviewer_keywords:
- strings [C++], as function input/output
- argument passing [C++]
- arguments [C++], passing
- functions [C++], strings as input/output
- argument passing [C++], C strings
- passing arguments, C strings
- CString objects, passing arguments
- string arguments
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
ms.openlocfilehash: 1729167786d71c107fe6a4369d5a0c7e7c8594f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236388"
---
# <a name="cstring-argument-passing"></a>Cstring — przekazywanie argumentów

W tym artykule wyjaśniono, jak przekazać [CString](../atl-mfc-shared/reference/cstringt-class.md) obiektów funkcji oraz sposób zwracania `CString` obiektów z usługi functions.

##  <a name="_core_cstring_argument.2d.passing_conventions"></a> Konwencji przekazywania argumentów CString

Podczas definiowania interfejsu klasy, należy określić Konwencji przekazywania argumentów dla funkcji elementu członkowskiego. Istnieją pewne standardowe reguły, przekazywanie i zwracanie `CString` obiektów. Jeśli postępuj zgodnie z zasadami opisanymi w [ciągi jako dane wejściowe funkcji](#_core_strings_as_function_inputs) i [ciągi jako dane wyjściowe funkcji](#_core_strings_as_function_outputs), trzeba będzie wydajne, poprawny kod.

##  <a name="_core_strings_as_function_inputs"></a> Ciągi jako dane wejściowe — funkcja

Najbardziej wydajny i bezpieczny sposób używania `CString` jest przekazanie obiektu w funkcji o nazwie `CString` obiektu do funkcji. Niezależnie od nazwy `CString` obiektu nie przechowuje ciąg wewnętrznie jako ciąg stylu C, który ma terminator o wartości null. Zamiast tego `CString` obiektu śledzi dokładnej liczbę znaków, które przedstawiono w nim. Posiadanie `CString` podane LPCTSTR wskaźnik na ciąg zakończony znakiem null niewielką ilość pracy, która może stać się istotne, jeśli kod ma na celu stale. Wynik jest tymczasowy, ponieważ dowolne zmiany `CString` zawartość unieważnia stare kopie LPCTSTR wskaźnika.

Sensowne w niektórych przypadkach można podać ciąg stylu C. Na przykład może być sytuacja, w którym wywołana funkcja został napisany w języku C i nie obsługuje obiektów. W tym przypadku wymuszone `CString` parametr LPCTSTR i funkcja otrzyma ciąg stylu C zakończony znakiem null. Można również przejść innym kierunku i tworzyć `CString` obiektu za pomocą `CString` Konstruktor, który przyjmuje parametr ciąg stylu C.

W przypadku zawartości ciągu ma zostać zmieniony przez funkcję, należy zadeklarować parametru jako nonconstant `CString` odwołania (`CString&`).

##  <a name="_core_strings_as_function_outputs"></a> Ciągi jako dane wyjściowe — funkcja

Zazwyczaj może zwrócić `CString` obiekty z funkcji, ponieważ `CString` obiektów postępuj zgodnie z semantyką wartości, takich jak typy pierwotne. Zwraca ciąg tylko do odczytu, użyj stałej `CString` odwołania (`const CString&`). Poniższy przykład ilustruje użycie `CString` parametry i zwracane typy:

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>Zobacz także

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

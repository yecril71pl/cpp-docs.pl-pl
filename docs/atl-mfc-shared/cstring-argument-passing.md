---
title: CString — przekazywanie argumentów
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
ms.openlocfilehash: 53977eb47520a20571a2d5ba8aa105c567ff40d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317934"
---
# <a name="cstring-argument-passing"></a>CString — przekazywanie argumentów

W tym artykule wyjaśniono, jak przekazać [CString](../atl-mfc-shared/reference/cstringt-class.md) obiektów do funkcji i jak zwracać `CString` obiekty z funkcji.

## <a name="cstring-argument-passing-conventions"></a><a name="_core_cstring_argument.2d.passing_conventions"></a>CString Argument-Passing Konwencje

Podczas definiowania interfejsu klasy, należy określić konwencję przekazywania argumentów dla funkcji członkowskich. Istnieją pewne standardowe reguły przekazywania i zwracania `CString` obiektów. Jeśli zastosujesz się do reguł opisanych w [ciągach jako wejścia funkcyjne](#_core_strings_as_function_inputs) i [ciągi jako wyjścia funkcyjne,](#_core_strings_as_function_outputs)będziesz mieć wydajny, poprawny kod.

## <a name="strings-as-function-inputs"></a><a name="_core_strings_as_function_inputs"></a>Ciągi jako wejścia funkcyjne

Najbardziej efektywnym i bezpiecznym `CString` sposobem użycia obiektu w `CString` wywoływanych funkcjach jest przekazanie obiektu do funkcji. Pomimo nazwy obiekt `CString` nie przechowuje ciąg wewnętrznie jako ciąg w stylu C, który ma zerowy terminator. Zamiast tego `CString` obiekt uważnie śledzi liczbę znaków, które ma. Po `CString` poindylogu LPCTSTR do ciągu zakończonego wartością null jest niewielka ilość pracy, które mogą stać się znaczące, jeśli kod ma to robić stale. Wynik jest tymczasowy, ponieważ `CString` wszelkie zmiany w zawartości unieważniają stare kopie wskaźnika LPCTSTR.

Ma to sens w niektórych przypadkach, aby zapewnić ciąg w stylu C. Na przykład może istnieć sytuacja, w której wywoływana funkcja jest zapisywana w języku C i nie obsługuje obiektów. W takim przypadku wymuszaj `CString` parametr do LPCTSTR, a funkcja otrzyma ciąg zakończony zerem w stylu C. Można również przejść w innym `CString` kierunku i `CString` utworzyć obiekt przy użyciu konstruktora, który akceptuje parametr ciągu w stylu C.

Jeśli zawartość ciągu ma zostać zmieniona przez funkcję, zadeklaruj parametr jako odniesienie niestałe `CString` (`CString&`).

## <a name="strings-as-function-outputs"></a><a name="_core_strings_as_function_outputs"></a>Ciągi jako wyjścia funkcyjne

Zazwyczaj można zwracać `CString` obiekty `CString` z funkcji, ponieważ obiekty podążają za semantyką wartości, taką jak typy pierwotne. Aby zwrócić ciąg tylko do odczytu, należy użyć stałego `CString` odwołania (`const CString&`). Poniższy przykład ilustruje `CString` użycie parametrów i typów zwracanych:

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

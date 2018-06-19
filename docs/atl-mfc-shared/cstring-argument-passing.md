---
title: Przekazywanie argumentów cstring — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 642ff20028a0929bb7bc11815e66b9f845ef9bd7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356833"
---
# <a name="cstring-argument-passing"></a>Przekazywanie argumentów cstring —
W tym artykule opisano sposób przekazywania [cstring —](../atl-mfc-shared/reference/cstringt-class.md) obiekty funkcji i sposób zwracania `CString` obiektów z funkcji.  
  
##  <a name="_core_cstring_argument.2d.passing_conventions"></a> Cstring — konwencje przekazywanie argumentów  
 Podczas definiowania interfejsu klasy, należy określić konwencję przekazywanie argumentu dla funkcji Członkowskich. Istnieją pewne standardowe reguły przekazywanie i zwracanie `CString` obiektów. Jeśli wykonujesz zasady określone w [ciągi jako dane wejściowe funkcji](#_core_strings_as_function_inputs) i [ciągi jako dane wyjściowe funkcji](#_core_strings_as_function_outputs), trzeba będzie wydajne, poprawne kodu.  
  
##  <a name="_core_strings_as_function_inputs"></a> Ciągi jako dane wejściowe — funkcja  
 Najbardziej wydajny i bezpieczny sposób używania `CString` jest przekazanie obiektu w funkcji o nazwie `CString` obiektu funkcji. Pomimo nazwę `CString` obiektu nie przechowuje ciąg wewnętrznie jako ciąg stylu języka C z terminatorem null. Zamiast tego `CString` obiektu śledzi monitorowanie liczby znaków ma. O `CString` podaj `LPCTSTR` niewielką ilość pracy, który może stać się istotne, jeśli kod ma robić stale jest wskaźnikiem do ciągu zakończonego wartością null. Wynik jest tymczasowy, ponieważ wszelkie zmiany `CString` zawartość unieważnia starych kopii `LPCTSTR` wskaźnika.  
  
 Go być uzasadniona w niektórych przypadkach można podać ciąg stylu języka C. Na przykład może być sytuacja, w których wywoływana funkcja jest napisany w języku C i nie obsługuje obiektów. Coerce — w takim przypadku `CString` parametr `LPCTSTR`, a funkcja otrzyma ciąg zerem w stylu języka C. Można również przejść innym kierunku i utworzyć `CString` obiektu przy użyciu `CString` konstruktora, który akceptuje parametr typu string w stylu języka C.  
  
 Jeśli ma zostać zmienione przez funkcję zawartości ciągu, należy zadeklarować jako nonconstant parametr `CString` odwołania (**cstring — &**).  
  
##  <a name="_core_strings_as_function_outputs"></a> Ciągi jako dane wyjściowe — funkcja  
 Zazwyczaj można zwrócić `CString` obiektów z funkcji, ponieważ `CString` obiektów wykonaj semantyki wartości podobnie jak typów pierwotnych. Zwraca ciąg tylko do odczytu, użyj stałej `CString` odwołania (**const cstring — &**). Poniższy przykład przedstawia użycie `CString` parametrów i zwracanych typów:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)


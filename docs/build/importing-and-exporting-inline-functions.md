---
title: Importowanie i eksportowanie funkcji śródwierszowych
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
ms.openlocfilehash: 407ca39aa53cf622b531fa0ca7818682c82c561f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439107"
---
# <a name="importing-and-exporting-inline-functions"></a>Importowanie i eksportowanie funkcji śródwierszowych

Zaimportowane funkcje mogą być definiowane jako wbudowane. Efekt jest mniej więcej taka sama jak definiowanie w tekście standardowej funkcji; wywołań funkcji są rozwijane kod wbudowane, podobnie jak makra. Jest to głównie przydatne, ponieważ sposób obsługi C++ klas w bibliotece DLL tym miejscu może niektóre z ich funkcji w celu zwiększenia wydajności.

Jedna z funkcji importowanych wbudowanej funkcji jest wykonanie adresu w języku C++. Kompilator zwraca adres kopii znajdującej się w bibliotece DLL funkcja w tekście. Kolejną funkcją importowanych wbudowane funkcje jest, czy należy zainicjować lokalnych danych statycznych funkcji importowany, w przeciwieństwie do globalnych, importowanych danych.

> [!CAUTION]
>  Opieka powinny uwzględniać importowane zapewniając wbudowane funkcje, ponieważ tworzą konfliktów wersji. Funkcja śródwierszowa rozwija się w kodzie aplikacji; w związku z tym jeśli przepiszesz później funkcji, go nie zostanie zaktualizowany, chyba że sama aplikacja jest ponownie kompilowana. (Zazwyczaj funkcji DLL można zaktualizować bez ponownie skompilować aplikacje, które z nich korzystają.)

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)

- [Eksportowanie z biblioteki DLL za pomocą. Pliki DEF](../build/exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Eksportuj funkcje C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Określić, której metody eksportowania użyjesz](../build/determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Zobacz też

[Importowanie i eksportowanie](../build/importing-and-exporting.md)
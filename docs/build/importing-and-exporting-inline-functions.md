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
ms.openlocfilehash: abb0443ab8fbd315524350caaff34e0250147ed2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328518"
---
# <a name="importing-and-exporting-inline-functions"></a>Importowanie i eksportowanie funkcji śródwierszowych

Importowane funkcje można definiować jako wbudowane. Efekt jest w przybliżeniu taki sam jak Definiowanie standardowej funkcji wbudowanej; wywołania funkcji są rozszerzane do kodu wbudowanego, podobnie jak makro. Jest to szczególnie przydatne jako sposób obsługi klas języka C++ w bibliotece DLL, która może być wbudowana część funkcji Członkowskich w celu zwiększenia wydajności.

Jedną z funkcji zaimportowanej wbudowanej funkcji jest możliwość poprawnego adresu w języku C++. Kompilator zwraca adres kopii wbudowanej funkcji znajdującej się w pliku DLL. Inną funkcją zaimportowanych funkcji wbudowanych jest możliwość inicjowania statycznych danych lokalnych funkcji zaimportowanej, w przeciwieństwie do globalnych zaimportowanych danych.

> [!CAUTION]
> Należy zachować ostrożność podczas udostępniania zaimportowanych funkcji wbudowanych, ponieważ mogą one stworzyć możliwość konfliktów wersji. Wbudowana funkcja zostanie rozwinięta w kodzie aplikacji; w związku z tym, jeśli później ponownie napiszesz funkcję, nie zostanie ona zaktualizowana, chyba że sama aplikacja zostanie ponowna skompilowana. (Zwykle funkcje DLL można aktualizować bez konieczności ponownego kompilowania aplikacji, które ich używają).

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportuj z biblioteki DLL](exporting-from-a-dll.md)

- [Eksportowanie z biblioteki DLL przy użyciu programu. Pliki DEF](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Określanie, której metody eksportowania użyć](determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Zobacz też

[Importowanie i eksportowanie](importing-and-exporting.md)

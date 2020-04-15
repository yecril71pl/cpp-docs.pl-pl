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

Importowane funkcje można zdefiniować jako wbudowane. Efekt jest mniej więcej taki sam jak definiowanie standardowej funkcji wbudowanej; wywołania funkcji są rozszerzane do kodu wbudowanego, podobnie jak makro. Jest to głównie przydatne jako sposób obsługi klas języka C++ w biblioteki DLL, które mogą wbudowane niektóre z ich funkcji członkowskich dla wydajności.

Jedną z funkcji importowanej funkcji wbudowanej jest to, że można wziąć jej adres w języku C++. Kompilator zwraca adres kopii wbudowanej funkcji zamieszkałej w dll. Inną cechą importowanych funkcji wbudowanych jest zainicjowanie statycznych danych lokalnych importowanej funkcji, w przeciwieństwie do zaimportowanych danych globalnych.

> [!CAUTION]
> Należy zachować ostrożność podczas dostarczania importowanych funkcji wbudowanych, ponieważ mogą one tworzyć możliwość konfliktów wersji. Funkcja wbudowana zostanie rozwinięta do kodu aplikacji; w związku z tym jeśli później przepisać funkcję, nie zostanie zaktualizowany, chyba że sama aplikacja jest ponownie skompilowany. (Zwykle funkcje biblioteki DLL mogą być aktualizowane bez przebudowy aplikacji, które z nich korzystają.)

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)

- [Eksportowanie z biblioteki DLL przy użyciu programu . Pliki DEF](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Eksportowanie funkcji języka C++ do użytku w plikach wykonywalnych w języku C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Określanie, która metoda eksportowania ma być używana](determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Zobacz też

[Importowanie i eksportowanie](importing-and-exporting.md)

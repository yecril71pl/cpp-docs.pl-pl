---
title: Importowanie i eksportowanie
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: c7328f0e5f5d408ec93f31fa4cbea987594264ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492772"
---
# <a name="importing-and-exporting"></a>Importowanie i eksportowanie

Można zaimportować symboli publicznych do aplikacji lub eksportowania funkcji z biblioteki DLL przy użyciu dwóch metod:

- Użyj pliku definicji (.def) moduł podczas kompilowania biblioteki DLL

- Używać słów kluczowych **__declspec(dllimport)** lub **__declspec(dllexport)** w definicji funkcji w głównym aplikacji

## <a name="using-a-def-file"></a>Używając pliku .def

Plik definicji modułu (.def) jest plikiem tekstowym zawierającym jedną lub więcej instrukcji modułu, które opisują różne atrybuty pliku DLL. Jeśli nie używasz **__declspec(dllimport)** lub **__declspec(dllexport)** do eksportowania funkcji DLL, biblioteka DLL wymaga pliku .def.

Możesz użyć .def — pliki do [importowanie do aplikacji](../build/importing-using-def-files.md) lub [eksportowanie z biblioteki DLL](../build/exporting-from-a-dll-using-def-files.md).

## <a name="using-declspec"></a>Za pomocą __declspec

Visual C++ używa **__declspec(dllimport)** i **__declspec(dllexport)** zastąpić **__export** — słowo kluczowe używane wcześniej w 16-bitowych wersjach Visual C++.

Nie trzeba używać **__declspec(dllimport)** swój kod, aby skompilować poprawnie, ale to umożliwia kompilatorowi generowanie lepszego kodu. Kompilator jest w stanie generowanie lepszego kodu, ponieważ można określić, czy funkcja istnieje w bibliotece DLL lub nie, co pozwala kompilator generuje kod, z pominięciem poziom pośrednictwa, które zwykle będą obecne w wywołaniu funkcji, która przekroczyła granicę biblioteki DLL. Jednakże, należy użyć **__declspec(dllimport)** do zaimportowania zmiennych używanych w bibliotece DLL.

Za pomocą sekcji EXPORTS pliku .def odpowiednie **__declspec(dllexport)** nie jest wymagana. **__declspec(dllexport)** została dodana do umożliwiają łatwe do eksportowania funkcji z pliku .exe lub .dll, bez użycia pliku .def.

Format przenośnym plikiem wykonywalnym środowiska Win32 jest przeznaczony do zminimalizować liczbę stron, które muszą dotknięciu naprawić importów. Aby to zrobić, umieszcza wszystkie adresy importu dla dowolnego programu, w jednym miejscu, o nazwie tabeli adresów importowania. Dzięki temu moduł ładujący zmodyfikować jedną lub dwie strony podczas uzyskiwania dostępu do tych importów.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Importowanie do aplikacji](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)

## <a name="see-also"></a>Zobacz też

[Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)
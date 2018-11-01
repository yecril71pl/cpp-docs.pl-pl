---
title: Eksportowanie funkcji z biblioteki DLL według numeru porządkowego a nie nazwy
ms.date: 11/04/2016
f1_keywords:
- NONAME
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 6a5ac13fdc85b3cb1626aefa28b92866a8c856c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503420"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Eksportowanie funkcji z biblioteki DLL według numeru porządkowego a nie nazwy

Najprostszym sposobem, aby wyeksportować funkcje z biblioteki DLL nie jest eksportowane je według nazwy. Jest to, co się stanie, gdy używasz **__declspec(dllexport)**, na przykład. Jednak zamiast tego możesz wyeksportować funkcje według liczby porządkowej. W przypadku tej techniki należy użyć pliku .def, zamiast **__declspec(dllexport)**. Aby określić wartości porządkowe funkcji, Dołącz jego numer nazwa funkcji w pliku .def. Aby uzyskać informacji na temat określania liczby porządkowe, zobacz [eksportowanie z biblioteki DLL za pomocą plików .def](../build/exporting-from-a-dll-using-def-files.md).

> [!TIP]
>  Jeśli chcesz zoptymalizować rozmiar pliku biblioteki DLL, użyj **NONAME** atrybut na każdym eksportowanych funkcji. Za pomocą **NONAME** atrybutu, liczby porządkowe są przechowywane w DLL Eksportowanie tabeli, a nie nazwy funkcji. Jeśli eksportujesz wiele funkcji, może to być znaczne oszczędności.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Użyj pliku .def, dzięki czemu można wyeksportować według liczby porządkowej](../build/exporting-from-a-dll-using-def-files.md)

- [Użyj atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Zobacz też

[Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)
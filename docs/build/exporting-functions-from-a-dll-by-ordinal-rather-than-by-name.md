---
title: Eksportowanie funkcji z biblioteki DLL według numeru porządkowego a nie nazwy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- NONAME
dev_langs:
- C++
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d894df971dd0c50556a420eafa2909474ee6912
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714262"
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
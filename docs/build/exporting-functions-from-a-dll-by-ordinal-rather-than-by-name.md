---
title: Eksportowanie funkcji z biblioteki DLL według numeru porządkowego a nie nazwy
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 66e99b18d181e9067e90398c35a61db2da66c301
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328577"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Eksportowanie funkcji z biblioteki DLL według numeru porządkowego a nie nazwy

Najprostszym sposobem eksportowania funkcji z biblioteki DLL jest eksportowanie ich według nazwy. Dzieje się tak w przypadku używania **__declspec (dllexport)**, na przykład. Ale zamiast tego można eksportować funkcje według liczby porządkowej. W tej metodzie należy użyć pliku. def zamiast **__declspec (dllexport)**. Aby określić wartość porządkową funkcji, Dołącz jej numer porządkowy do nazwy funkcji w pliku. def. Aby uzyskać informacje o określaniu liczby porządkowej, zobacz [Eksportowanie z biblioteki DLL za pomocą plików. def](exporting-from-a-dll-using-def-files.md).

> [!TIP]
> Jeśli chcesz zoptymalizować rozmiar pliku biblioteki DLL, Użyj atrybutu **NoName** w każdej funkcji wyeksportowanej. W przypadku atrybutu **NoName** liczby porządkowe są przechowywane w tabeli eksportu biblioteki DLL, a nie w nazwach funkcji. Może to być znaczne oszczędności w przypadku eksportowania wielu funkcji.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Użyj pliku. def, aby można było eksportować według liczby porządkowej](exporting-from-a-dll-using-def-files.md)

- [Użyj __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Zobacz też

[Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)

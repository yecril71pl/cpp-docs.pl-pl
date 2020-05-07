---
title: Przydzielanie pamięci zerowej
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: 40f21c0fa9a2a4068cb2592c49ccefed82176a35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313496"
---
# <a name="allocating-zero-memory"></a>Przydzielanie pamięci zerowej

**4.10.3 ANSI** Zachowanie funkcji `calloc`,, lub `malloc` `realloc` , jeśli żądany rozmiar wynosi zero

Funkcje `calloc`, `malloc`i `realloc` akceptują zero jako argument. Nie przydzielono rzeczywistej pamięci, ale zwracany jest prawidłowy wskaźnik, a blok pamięci może być później modyfikowany przez ponowne alokację.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)

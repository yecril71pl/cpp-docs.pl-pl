---
title: Typy literałów ciągów
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
ms.openlocfilehash: 7e832ac7aa08ad80ab395baa59eabbabb486b46f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344853"
---
# <a name="type-for-string-literals"></a>Typy literałów ciągów

Literały ciągu mają typ Array of `char` (czyli **Char []**). (Ciągi znaków dwubajtowych mają tablicę `wchar_t` typu (czyli **wchar_t []**).) Oznacza to, że ciąg jest tablicą z elementami typu `char`. Liczba elementów w tablicy jest równa liczbie znaków w ciągu plus jeden dla kończącego znaku null.

## <a name="see-also"></a>Zobacz też

[Literały ciągu języka C](../c-language/c-string-literals.md)

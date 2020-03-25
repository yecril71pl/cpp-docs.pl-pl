---
title: Błąd kompilatora zasobów RC2147
ms.date: 11/04/2016
f1_keywords:
- RC2147
helpviewer_keywords:
- RC2147
ms.assetid: 09974f06-1731-4e70-b373-f9218e0ee8d9
ms.openlocfilehash: f76c61ace4e0e1d8eea9a33669b66021861c36f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191148"
---
# <a name="resource-compiler-error-rc2147"></a>Błąd kompilatora zasobów RC2147

Identyfikator języka nie jest liczbą

Wartość identyfikatora języka podpoziomu musi być liczbą.

Instrukcja **języka** musi mieć następującą składnię:

**LANGUAGE** *Primary_language_ID*języka,*secondary_language_ID*

Prawidłowe identyfikatory języka są zdefiniowane jako stałe **SUBLANG_** w pliku Winnt. h.

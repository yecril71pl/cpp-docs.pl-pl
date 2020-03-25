---
title: Błąd kompilatora zasobów RC2148
ms.date: 11/04/2016
f1_keywords:
- RC2148
helpviewer_keywords:
- RC2148
ms.assetid: 0290065c-35d3-4815-80c5-40bf7132ae1d
ms.openlocfilehash: e2394dbb93dd2d203d65760d805e09f60a692ba4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191330"
---
# <a name="resource-compiler-error-rc2148"></a>Błąd kompilatora zasobów RC2148

Zbyt duży identyfikator języka podjęzyku

Wartość identyfikatora języka jest poza zakresem.

Instrukcja **języka** musi mieć następującą składnię:

**LANGUAGE** *Primary_language_ID*języka,*secondary_language_ID*

Prawidłowe identyfikatory języka są zdefiniowane jako stałe **SUBLANG_** w pliku Winnt. h.

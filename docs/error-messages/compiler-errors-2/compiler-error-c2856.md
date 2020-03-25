---
title: Błąd kompilatora C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: c88610607083ecfaf5f20cd585b479991fa51b44
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201899"
---
# <a name="compiler-error-c2856"></a>Błąd kompilatora C2856

\#pragma hdrstop nie może znajdować się wewnątrz bloku #if

Dyrektywy pragma `hdrstop` nie można umieścić wewnątrz treści bloku kompilacji warunkowej.

Przenieś instrukcję `#pragma hdrstop` do obszaru, który nie znajduje się w bloku `#if/#endif`.

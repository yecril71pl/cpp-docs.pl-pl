---
title: Błąd krytyczny C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: 07bd0f28e35dd2992ca537dbe744d756cc2afe80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203128"
---
# <a name="fatal-error-c1352"></a>Błąd krytyczny C1352

Nieprawidłowe lub uszkodzone MSIL w funkcji "Function" z modułu "File"

Do kompilatora został przekazano element. module, ale kompilator wykrył uszkodzenie w pliku.  Poproszenie osoby, która wyprodukowała moduł.

Kompilator nie sprawdza plików modułu dla wszystkich typów uszkodzeń.  Należy jednak sprawdzić, czy wszystkie ścieżki kontroli w funkcji zawierają instrukcję return.

Aby uzyskać więcej informacji, zobacz [. moduły plików jako dane wejściowe konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).

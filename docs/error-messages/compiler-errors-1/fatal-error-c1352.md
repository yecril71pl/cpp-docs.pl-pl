---
title: Błąd krytyczny C1352 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1352
dev_langs:
- C++
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4f1f062e11651e4d851231e16569412f95b90d4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042939"
---
# <a name="fatal-error-c1352"></a>Błąd krytyczny C1352

Nieprawidłowe lub uszkodzone MSIL w funkcji "function" z modułu 'Plik'

.Netmodule został przekazany do kompilatora, ale kompilator wykrył uszkodzenie w pliku.  Poproś osobę, kto produkowane .netmodule do badania.

Kompilator nie sprawdza pliki .netmodule dla wszystkich typów uszkodzenia.  Jednak Sprawdź, czy wszystkie ścieżki kontroli w funkcji zawiera instrukcję return.

Aby uzyskać więcej informacji, zobacz [pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).
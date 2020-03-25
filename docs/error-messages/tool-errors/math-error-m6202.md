---
title: Błąd matematyczny M6202
ms.date: 11/04/2016
f1_keywords:
- M6202
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
ms.openlocfilehash: b8a3a4ab87a410c4cee8f7e4a1a0517c169d0364
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173663"
---
# <a name="math-error-m6202"></a>Błąd matematyczny M6202

"Function": błąd _SING

Argument danej funkcji był wartością Singularity tej funkcji. Funkcja nie jest zdefiniowana dla tego argumentu.

Ten błąd wywołuje funkcję `_matherr` z nazwą funkcji, jej argumentami i typem błędu. Można ponownie napisać funkcję `_matherr`, aby dostosować obsługę określonych błędów matematycznych zmiennoprzecinkowych w czasie wykonywania.

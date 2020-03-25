---
title: Błąd kompilatora zasobów RC2001
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: 35042687b798b53857becdedba57861bd4f41a05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191729"
---
# <a name="resource-compiler-error-rc2001"></a>Błąd kompilatora zasobów RC2001

stała nowego wiersza

Stała ciągu była kontynuowana w drugim wierszu bez ukośnika odwrotnego ( **\\** ) albo zamykania i otwierania podwójnych cudzysłowów ( **"** ).

Aby przerwać stałą ciągu, która znajduje się w dwóch wierszach w pliku źródłowym, wykonaj jedną z następujących czynności:

- Zakończ pierwszy wiersz za pomocą znaku kontynuacji wiersza, ukośnika odwrotnego.

- Zamknij ciąg w pierwszym wierszu ze znakiem podwójnego cudzysłowu i Otwórz ciąg w następnym wierszu z innym znakiem cudzysłowu.

Nie wystarczy, aby zakończyć pierwszy wiersz za pomocą \n, sekwencji unikowej osadzania znaku nowego wiersza w stałej ciągu.

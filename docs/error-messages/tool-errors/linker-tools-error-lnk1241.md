---
title: Błąd narzędzi konsolidatora LNK1241
ms.date: 11/04/2016
f1_keywords:
- LNK1241
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
ms.openlocfilehash: 6e2b955787166c94be4ca35e1c58df5becd243f2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183816"
---
# <a name="linker-tools-error-lnk1241"></a>Błąd narzędzi konsolidatora LNK1241

plik zasobu "plik zasobów" został już określony

Ten błąd jest generowany, gdy uruchamiasz **CVTRES** ręcznie z wiersza polecenia, a następnie przekażesz otrzymany plik. obj do konsolidatora oprócz innych plików. res.

Aby określić wiele plików. res, przekaż je wszystkie do konsolidatora jako pliki. res, a nie z plików. obj utworzonych przez **CVTRES**.

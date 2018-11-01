---
title: Błąd narzędzi konsolidatora LNK1241
ms.date: 11/04/2016
f1_keywords:
- LNK1241
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
ms.openlocfilehash: 87f73680d7ed40b9b2db9f40f9140976d552ab6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584551"
---
# <a name="linker-tools-error-lnk1241"></a>Błąd narzędzi konsolidatora LNK1241

Plik zasobów 'plik zasobu' już określony

Ten błąd jest generowany, gdy uruchamiasz **cvtres** ręcznie z poziomu wiersza polecenia i jeśli następnie przekazać .obj wynikowy plik konsolidatora dodatkowo do innych plików .res.

Do określenia wielu plików .res, przekazać je wszystkie do konsolidatora jako pliki .res, nie z poziomu plików .obj utworzony przez **cvtres**.
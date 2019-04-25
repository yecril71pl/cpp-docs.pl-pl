---
title: Błąd narzędzi konsolidatora LNK1241
ms.date: 11/04/2016
f1_keywords:
- LNK1241
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
ms.openlocfilehash: 87f73680d7ed40b9b2db9f40f9140976d552ab6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160656"
---
# <a name="linker-tools-error-lnk1241"></a>Błąd narzędzi konsolidatora LNK1241

Plik zasobów 'plik zasobu' już określony

Ten błąd jest generowany, gdy uruchamiasz **cvtres** ręcznie z poziomu wiersza polecenia i jeśli następnie przekazać .obj wynikowy plik konsolidatora dodatkowo do innych plików .res.

Do określenia wielu plików .res, przekazać je wszystkie do konsolidatora jako pliki .res, nie z poziomu plików .obj utworzony przez **cvtres**.
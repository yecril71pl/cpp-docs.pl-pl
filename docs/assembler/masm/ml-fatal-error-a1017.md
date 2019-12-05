---
title: Błąd krytyczny ML A1017
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 6fb0835cca135fc994866dc2453734d7b3012a64
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856829"
---
# <a name="ml-fatal-error-a1017"></a>Błąd krytyczny ML A1017

**Brakująca nazwa pliku źródłowego**

Nie można znaleźć pliku do nałączenia lub przekazania do konsolidatora.

Ten błąd jest generowany, gdy jest przyznawana opcjami wiersza polecenia ML bez określenia nazwy pliku, na którym ma działać. Aby złożyć pliki, które nie mają rozszerzenia ASM, użyj opcji wiersza polecenia **/Ta** .

Ten błąd może być również wygenerowany przez wywołanie ML bez parametrów, jeśli zmienna środowiskowa ML zawiera opcje wiersza polecenia.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>
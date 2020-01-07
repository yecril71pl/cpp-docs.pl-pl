---
title: Błąd krytyczny ML A1017
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 523fed26afae5a88c5f154283487d3453a2e48c7
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318062"
---
# <a name="ml-fatal-error-a1017"></a>Błąd krytyczny ML A1017

**Brakująca nazwa pliku źródłowego**

Nie można znaleźć pliku do nałączenia lub przekazania do konsolidatora.

Ten błąd jest generowany, gdy jest przyznawana opcjami wiersza polecenia ML bez określenia nazwy pliku, na którym ma działać. Aby złożyć pliki, które nie mają rozszerzenia ASM, użyj opcji wiersza polecenia **/Ta** .

Ten błąd może być również wygenerowany przez wywołanie ML bez parametrów, jeśli zmienna środowiskowa ML zawiera opcje wiersza polecenia.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](ml-error-messages.md)

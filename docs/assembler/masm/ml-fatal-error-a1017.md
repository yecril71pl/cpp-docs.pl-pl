---
title: Błąd krytyczny ML A1017 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb98eab68da417526a75beaa57870ce906c85a8d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688562"
---
# <a name="ml-fatal-error-a1017"></a>Błąd krytyczny ML A1017

**Brakująca nazwa pliku źródłowego**

Uczenie Maszynowe, nie można odnaleźć plik, aby utworzyć lub przekazać do konsolidatora.

Ten błąd jest generowany po zapewnieniu ML opcji wiersza polecenia bez określania nazwy pliku wykonywane działania. Gromadzi pliki, które nie mają rozszerzenie .asm, użyj **/Ta** opcji wiersza polecenia.

Ten błąd można wygenerować w taki sposób, wywołując ML bez parametrów, jeśli ML — zmienna środowiskowa zawiera opcje wiersza polecenia.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>
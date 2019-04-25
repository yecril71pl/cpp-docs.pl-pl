---
title: Błąd krytyczny ML A1017
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 22a16569364760d0cb1d01011405f7a11dd21cac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177776"
---
# <a name="ml-fatal-error-a1017"></a>Błąd krytyczny ML A1017

**Brakująca nazwa pliku źródłowego**

Uczenie Maszynowe, nie można odnaleźć plik, aby utworzyć lub przekazać do konsolidatora.

Ten błąd jest generowany po zapewnieniu ML opcji wiersza polecenia bez określania nazwy pliku wykonywane działania. Gromadzi pliki, które nie mają rozszerzenie .asm, użyj **/Ta** opcji wiersza polecenia.

Ten błąd można wygenerować w taki sposób, wywołując ML bez parametrów, jeśli ML — zmienna środowiskowa zawiera opcje wiersza polecenia.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>
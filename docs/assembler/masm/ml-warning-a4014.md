---
title: Ostrzeżenie ML A4014 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A4014
dev_langs:
- C++
helpviewer_keywords:
- A4014
ms.assetid: 11bc8920-3255-4ac8-999a-b9ea9c15bc81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3108d961c213ca5035cdba5ca9e7c5c8c10317b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692154"
---
# <a name="ml-warning-a4014"></a>Ostrzeżenie ML A4014

instrukcje i zainicjowany dane nie są obsługiwane w segmentach BSS

Nastąpiła próba do definiowania danych zainicjowanych w obrębie sekcji BSS.  Sekcja BSS jest zdefiniowany jako klasę, której nazwa to BSS.  Obejmuje to uproszczony segmentu `.data?`.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>
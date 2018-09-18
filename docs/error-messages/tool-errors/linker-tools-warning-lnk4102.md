---
title: Ostrzeżenie LNK4102 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4102
dev_langs:
- C++
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9daaffc4ddfa9a869c2e60e2c05dc2b7e296d94b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031868"
---
# <a name="linker-tools-warning-lnk4102"></a>Ostrzeżenie LNK4102 narzędzi konsolidatora

Eksport destruktora "name"; Usuwanie Obraz może nie działać poprawnie

Program próbował wyeksportować usuwanie destruktora. Wynikowy usuwania może wystąpić granicę biblioteki DLL tak, aby proces może zwolnić pamięć, która nie jest właścicielem. Upewnij się, że dany symbol nie znajduje się w pliku .def i że symbol nie jest wymieniony jako argument **/IMPORT** lub **/EXPORT** opcji wiersza polecenia konsolidatora.

Do odbudowywania biblioteki wykonawczej języka C, możesz zignorować ten komunikat.
---
title: Błąd krytyczny NMAKE U1095 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1095
dev_langs:
- C++
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 964ec1d029e56a5d9d78659ad919c71a4e44506d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039884"
---
# <a name="nmake-fatal-error-u1095"></a>Błąd krytyczny NMAKE U1095

rozwinięty wiersz polecenia "wiersz polecenia" zbyt długo

Po rozwinięciu makra danego wiersza polecenia przekroczyła limit długości wiersze poleceń systemu operacyjnego.

MS-DOS zezwala na maksymalnie 128 znaków, w wierszu polecenia.

W przypadku polecenia dla programu, który może akceptować wejście wiersza polecenia z pliku, zmień polecenie, a następnie podaj dane wejściowe z pliku na dysku lub pliku wbudowanego. Na przykład łącze i LIB akceptuje dane wejściowe z pliku odpowiedzi.
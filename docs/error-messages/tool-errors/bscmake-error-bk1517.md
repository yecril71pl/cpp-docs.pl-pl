---
title: Błąd BSCMAKE BK1517 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1517
dev_langs:
- C++
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 941773fbcf65a3b1c1a6041a1e7a067cfc286823
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097058"
---
# <a name="bscmake-error-bk1517"></a>Błąd BSCMAKE BK1517

plik źródłowy sbrfile skompilowany przy użyciu opcji /Yc i /Yu

Plik .sbr odwołuje się do siebie. Jego została prawdopodobnie ponownie skompilowana przy użyciu /Yu po kompilacji z parametrem/yc. Przywrócić /Yc — opcja kompilatora dla pliku źródłowego, a następnie wybierz **odbudować** wygenerować nowe pliki .sbr. Nie zostanie ponownie skompilowana pliku źródłowego z /Yu.
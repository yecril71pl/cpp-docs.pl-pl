---
title: Błąd BSCMAKE BK1517
ms.date: 11/04/2016
f1_keywords:
- BK1517
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
ms.openlocfilehash: 455e028a72cce132c49e0d0d778628ee21bf3a0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476092"
---
# <a name="bscmake-error-bk1517"></a>Błąd BSCMAKE BK1517

plik źródłowy sbrfile skompilowany przy użyciu opcji /Yc i /Yu

Plik .sbr odwołuje się do siebie. Jego została prawdopodobnie ponownie skompilowana przy użyciu /Yu po kompilacji z parametrem/yc. Przywrócić /Yc — opcja kompilatora dla pliku źródłowego, a następnie wybierz **odbudować** wygenerować nowe pliki .sbr. Nie zostanie ponownie skompilowana pliku źródłowego z /Yu.
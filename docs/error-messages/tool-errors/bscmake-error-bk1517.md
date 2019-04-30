---
title: Błąd BSCMAKE BK1517
ms.date: 11/04/2016
f1_keywords:
- BK1517
helpviewer_keywords:
- BK1517
ms.assetid: 24391f42-0a3e-40a9-9991-c8b9a6a7b1c7
ms.openlocfilehash: 455e028a72cce132c49e0d0d778628ee21bf3a0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380529"
---
# <a name="bscmake-error-bk1517"></a>Błąd BSCMAKE BK1517

plik źródłowy sbrfile skompilowany przy użyciu opcji /Yc i /Yu

Plik .sbr odwołuje się do siebie. Jego została prawdopodobnie ponownie skompilowana przy użyciu /Yu po kompilacji z parametrem/yc. Przywrócić /Yc — opcja kompilatora dla pliku źródłowego, a następnie wybierz **odbudować** wygenerować nowe pliki .sbr. Nie zostanie ponownie skompilowana pliku źródłowego z /Yu.
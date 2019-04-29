---
title: Błąd krytyczny NMAKE U1059
ms.date: 08/27/2018
f1_keywords:
- U1059
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
ms.openlocfilehash: 3c148bf2feb7ba12686e00b29f5bf90cb9f2f2d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367294"
---
# <a name="nmake-fatal-error-u1059"></a>Błąd krytyczny NMAKE U1059

> Błąd składniowy: "}" brakuje w zależnych od ustawień lokalnych

Ścieżki wyszukiwania dla zależnych od ustawień lokalnych został niepoprawnie określony. Albo miejsca istniał w ścieżce lub zamykającego nawiasu klamrowego (**}**) został pominięty.

Składnia dla specyfikację katalogu dla zależnych od ustawień lokalnych

> **{** *katalogi* **} zależne**

gdzie *katalogi* określa jeden lub więcej ścieżek rozdzielonych średnikami (**;**). Żadne spacje są dozwolone.

Jeśli część lub całość ścieżki wyszukiwania zostanie zastąpiony przez makro, upewnij się, że nie może zawierać spacji, istnieje w rozwinięciu makra.
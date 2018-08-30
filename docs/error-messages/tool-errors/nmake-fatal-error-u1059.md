---
title: Błąd krytyczny NMAKE U1059 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1059
dev_langs:
- C++
helpviewer_keywords:
- U1059
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b54919398c757bfe05f747ff57341f31decfc61
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200793"
---
# <a name="nmake-fatal-error-u1059"></a>Błąd krytyczny NMAKE U1059

> Błąd składniowy: "}" brakuje w zależnych od ustawień lokalnych

Ścieżki wyszukiwania dla zależnych od ustawień lokalnych został niepoprawnie określony. Albo miejsca istniał w ścieżce lub zamykającego nawiasu klamrowego (**}**) został pominięty.

Składnia dla specyfikację katalogu dla zależnych od ustawień lokalnych

> **{** *katalogi* **} zależne**

gdzie *katalogi* określa jeden lub więcej ścieżek rozdzielonych średnikami (**;**). Żadne spacje są dozwolone.

Jeśli część lub całość ścieżki wyszukiwania zostanie zastąpiony przez makro, upewnij się, że nie może zawierać spacji, istnieje w rozwinięciu makra.
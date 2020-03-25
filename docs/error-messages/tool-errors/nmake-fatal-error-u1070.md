---
title: Błąd krytyczny NMAKE U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 008d49df3460cb7cf760e4b278db20da444555fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182776"
---
# <a name="nmake-fatal-error-u1070"></a>Błąd krytyczny NMAKE U1070

cykl w definicji makra "Macroname"

Dana definicja makra zawiera makro, którego definicja zawierała podane makro. Definicje makr cyklicznych są nieprawidłowe.

## <a name="example"></a>Przykład

Następujące definicje makr

```
ONE=$(TWO)
TWO=$(ONE)
```

Przyczyna następującego błędu:

```
cycle in macro definition 'TWO'
```

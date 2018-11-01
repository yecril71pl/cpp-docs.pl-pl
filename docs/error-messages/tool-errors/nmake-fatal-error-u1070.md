---
title: Błąd krytyczny NMAKE U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 35bea47f6626dfe283a537d3d96340921c37f3f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484217"
---
# <a name="nmake-fatal-error-u1070"></a>Błąd krytyczny NMAKE U1070

cykl w definicji makra "makra"

Makro, którego definicja zawiera danego — makro znajdujących się w definicji makra danego. Definicje makr cykliczne są nieprawidłowe.

## <a name="example"></a>Przykład

Następujące definicje — makro

```
ONE=$(TWO)
TWO=$(ONE)
```

powodują następujący błąd:

```
cycle in macro definition 'TWO'
```
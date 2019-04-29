---
title: Błąd krytyczny NMAKE U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 35bea47f6626dfe283a537d3d96340921c37f3f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367242"
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
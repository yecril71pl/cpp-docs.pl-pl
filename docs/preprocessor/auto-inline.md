---
title: auto_inline, pragma
ms.date: 08/29/2019
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: 59cda8cb73196215318c9570a5c067786284afaa
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216304"
---
# <a name="auto_inline-pragma"></a>auto_inline, pragma

Wyklucza wszelkie funkcje zdefiniowane w zakresie, w którym wartość **off** jest określana jako kandydatów do automatycznego rozwijania wbudowanego.

## <a name="syntax"></a>Składnia

> **#pragma auto_inline (** [{ **on** | **off** }] **)**

## <a name="remarks"></a>Uwagi

Aby użyć dyrektywy pragma **auto_inline** , umieść ją przed i natychmiast po, a nie wewnątrz, definicję funkcji. Pragma jest skuteczna, gdy tylko pierwsza definicja funkcji zostanie wyświetlona.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
